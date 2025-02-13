+++ 
draft = false
date = 2021-01-04T17:35:55-05:00
title = "Swift Hello World"
description = "Swift Hello World"
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++
## Swift Hello World

1. Testing git 2020.

import UIKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
    }

    @IBAction func showMessage(sender: UIButton) {
        let alertController = UIAlertController(title: "Welcome to My First App", message: "Hello World", preferredStyle: UIAlertController.Style.alert)
        alertController.addAction(UIAlertAction(title: "OK", style: UIAlertAction.Style.default, handler: nil))
        present(alertController, animated: true, completion: nil)
    }
}

Any surprise?
