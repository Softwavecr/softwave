---
title: "Promise vs Observable"
date: 2020-12-14T10:21:27-05:00
draft: false
---

## 1:1

* a Promise is eager, whereas an Observable is lazy,
* a Promise is always asynchronous, while an Observable can be either synchronous or asynchronous,
* a Promise can provide a single value, whereas an Observable is a stream of values (from 0 to multiple values),
* you can apply RxJS operators to an Observable to get a new tailored stream (categorized as: creation[from, range], transformation[map, scan ], filtering[first, last], joining[mergeall, startwith], multicasting[publish, share], error handling[catchError, retry], utility[delay, timeout])

## Cheat sheet
The following code snippets illustrate how the same kind of operation is defined using observables and promises.

   Operation | Observable | Promise
-------------|------------|--------
Creation | new Observable((observer) => {  observer.next(123);}); | new Promise((resolve, reject) => {  resolve(123);}); |
Transform | obs.pipe(map((value) => value * 2)); |promise.then((value) => value * 2); |
Subscribe | sub = obs.subscribe((value) => { console.log(value)}); | promise.then((value) => { console.log(value); }); |
Unsubscribe | sub.unsubscribe(); | Implied by promise resolution. |
