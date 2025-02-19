+++ 
draft = false
date = 2025-02-18T21:29:20-05:00
title = "Adding tests to C# + React project"
description = ""
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++

Let's add some basic unit tests for both the backend (C#) and frontend (React).

## Backend (C#)
1. __Install Test NuGet Packages__: In your .NET project, install the necessary testing packages:
```bash {linenos=table,linenostart=0}    
dotnet add package xunit
dotnet add package xunit.runner.visualstudio
dotnet add package Microsoft.NET.Test.Sdk
dotnet add package Moq // For mocking dependencies
```

2. __Create Test Project__: Create a new xUnit Test Project in your solution (e.g., `MyBlog.Tests`).  

3. __Create Tests__: (e.g., `PostServiceTests.cs`):
```cs {linenos=table,linenostart=0}    
using Xunit;
using Moq;
using Microsoft.EntityFrameworkCore;
using System.Threading.Tasks;
using System.Collections.Generic;
using MyBlog.Services; // Replace with your namespace
using MyBlog.Models; // Replace with your namespace

public class PostServiceTests
{
    private readonly Mock<BlogDbContext> _mockContext;
    private readonly PostService _postService;

    public PostServiceTests()
    {
        _mockContext = new Mock<BlogDbContext>();
        _postService = new PostService(_mockContext.Object);
    }

    [Fact]
    public async Task GetPostsAsync_ReturnsAllPosts()
    {
        // Arrange
        var posts = new List<Post> {
            new Post { Id = 1, Title = "Post 1", Content = "Content 1" },
            new Post { Id = 2, Title = "Post 2", Content = "Content 2" }
        };

        var mockDbSet = new Mock<DbSet<Post>>();
        mockDbSet.As<IQueryable<Post>>().Setup(m => m.Provider).Returns(posts.AsQueryable().Provider);
        mockDbSet.As<IQueryable<Post>>().Setup(m => m.Expression).Returns(posts.AsQueryable().Expression);
        mockDbSet.As<IQueryable<Post>>().Setup(m => m.GetEnumerator()).Returns(posts.AsQueryable().GetEnumerator());

        _mockContext.Setup(c => c.Posts).Returns(mockDbSet.Object);

        // Act
        var result = await _postService.GetPostsAsync();

        // Assert
        Assert.Equal(2, result.Count);
        Assert.Equal("Post 1", result[0].Title);
        Assert.Equal("Post 2", result[1].Title);
    }

    // Add more tests for GetPostByIdAsync, CreatePostAsync, etc.
}
```

4. __Run Tests__: Use the Visual Studio Test Explorer or the `dotnet test` command.

## Frontend (React)
1. __Install Testing Libraries__: 
```bash {linenos=table,linenostart=0}    
npm install --save-dev jest @testing-library/react @testing-library/jest-dom
```  
2. __Create Tests__(e.g., `PostList.test.js`):
```js {linenos=table,linenostart=0}    
import React from 'react';
import { render, screen, waitFor } from '@testing-library/react';
import PostList from './PostList'; // Your component
import fetch from 'cross-fetch'; // For mocking fetch

global.fetch = jest.fn(); // Mock fetch globally

describe('PostList Component', () => {
    it('fetches and displays posts', async () => {
        // Arrange
        const mockPosts = [
            { id: 1, title: 'Post 1', content: 'Content 1', createdAt: '2024-01-01T12:00:00Z' },
            { id: 2, title: 'Post 2', content: 'Content 2', createdAt: '2024-01-02T12:00:00Z' },
        ];

        fetch.mockResolvedValue({
            json: () => Promise.resolve(mockPosts),
        });

        // Act
        render(<PostList />);

        // Assert (using waitFor to handle asynchronous operations)
        await waitFor(() => {
            expect(screen.getByRole('heading', { name: 'Blog Posts' })).toBeInTheDocument();
            expect(screen.getByRole('heading', { name: 'Post 1' })).toBeInTheDocument();
            expect(screen.getByRole('heading', { name: 'Post 2' })).toBeInTheDocument();
            expect(screen.getByText('Content 1')).toBeInTheDocument();
            expect(screen.getByText('Content 2')).toBeInTheDocument();
        });

        expect(fetch).toHaveBeenCalledTimes(1);
        expect(fetch).toHaveBeenCalledWith('https://localhost:7279/api/post'); //Check if the correct url has been called
    });

    it('displays loading message while fetching', () => {
        // Arrange
        fetch.mockResolvedValue(new Promise(() => {})); // Simulate pending fetch
        render(<PostList />);

        // Assert
        expect(screen.getByText('Loading...')).toBeInTheDocument();
    });

    it('displays error message if fetch fails', async () => {
        // Arrange
        fetch.mockRejectedValue(new Error('Failed to fetch'));
        render(<PostList />);

        // Assert
        await waitFor(() => {
            expect(screen.getByText('Error: Failed to fetch')).toBeInTheDocument();
        });
    });
});
```   
3. __Run Tests__: `npm test`.

## Key Improvements and Explanations:

1. __Mocking__: In the C# tests, we use Moq to mock the `BlogDbContext`. This isolates the `PostService` from the actual database. In the React tests we mock the global `fetch` function to control what data is returned.  
2. __xUnit__: Used xUnit for C# testing.  
3. __Testing Library__: Used `@testing-library/react` for React testing. It encourages testing based on user interactions rather than implementation details.  
4. `waitFor`: The React test uses `waitFor` to handle the asynchronous nature of the `fetch` call.  
5. `describe` and `it`: Used `describe` blocks to group related tests and `it` blocks to define individual test cases.  
6. __Error Handling Test__: Added a test case to check how the component behaves when the API call fails.  
7. __Loading State Test__: Added a test to check if a "Loading..." message is displayed while the data is being fetched.  
8. __Check Fetch URL__: Added a test to check if the correct URL has been called.  

Remember to adapt the namespaces and component names to your project structure.  These examples provide a good starting point for testing your backend and frontend code.  As your application grows, you should add more comprehensive tests to cover various scenarios and edge cases.