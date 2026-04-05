# Postman User Guide

## Introduction

[Postman](https://www.postman.com) is a tool used to send, inspect, and test API requests. If you are new to API development, this guide will help you understand Postman step by step — without assuming prior experience with the tool.

Before we begin, here are a few terms you will encounter throughout this guide. You do not need to be an expert, but you should be able to recognize what they refer to:

| Term | Description | |
|------|-------------|---|
| **API** (Application Programming Interface) | A way for software to communicate with another system. | [Learn more](https://www.postman.com/what-is-an-api/) |
| **RESTful API** | A common style of API that uses URLs and HTTP methods to access resources. | [Learn more](https://restfulapi.net/) |
| **HTTP Request** | A message sent from a client to a server, such as `GET` or `POST`. | [Learn more](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) |
| **JSON** (JavaScript Object Notation) | A lightweight data format often used in API requests and responses. | [Learn more](https://www.json.org/json-en.html) |

If these concepts sound familiar — or you can quickly review them using the links above — you are ready to start using Postman.

This guide will walk you through the essential features of Postman and help you build confidence in real API testing workflows.


## Intended Users

This guide is written for:

- Students learning web development or backend fundamentals
- Beginners who want to practice sending [HTTP requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods)
- Developers who need a simple tool to test [RESTful APIs](https://restfulapi.net/)
- Anyone using Postman for the first time and looking for a structured introduction

This document assumes no prior experience with Postman itself.

## Prerequisite Knowledge

Before using this guide, readers should already understand:

- The basic structure of a [RESTful API](https://restfulapi.net/)
- Common HTTP methods: [GET, POST, PUT, DELETE](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
- Basic [JSON](https://www.json.org/json-en.html) formatting

No programming experience is required, but it will be helpful when working with more advanced examples.

## Software Requirements

To follow the tasks in this guide, users must have:

- [Postman Desktop Application](https://www.postman.com/downloads/)  
  (Windows, macOS, or Linux — latest stable version recommended)
- A stable internet connection

## Overview of Tasks

This guide is organized into several hands‑on tasks that introduce Postman's core features:

1. **Task 1 — Sending a Basic GET Request**  
   Learn how to send your first request and read the response.

2. **Task 2 — Using Environment Variables**  
   Understand how to create and use environment variables in your project.

3. **Task 3 — Using Collections to Organize API Requests**  
   Learn how to save, group, and reuse requests efficiently.

4. **Task 4 — Managing Collections**  
    Learn how to export, import, and run collections, and how to troubleshoot variable‑related errors.

Each task builds on the previous one, allowing beginners to gradually develop confidence using Postman.


## Typographical Conventions

To improve clarity, this guide uses the following formatting conventions:

| Convention | Usage | Example |
|------------|-------|---------|
| **"UI Component"** | Buttons, menu items, input fields, and other interactive elements | Select **"Send"**, then open **"Headers"** |
| **Bold text** | Important technical terms or concepts | A **RESTful API** uses standard HTTP methods |
| `Monospace` | Code, JSON, URLs, variable names, and command-line text | `https://api.example.com/users` |

The following admonition blocks are used throughout this guide to draw your attention to important information:

!!! note
    Helpful tips or reminders to support your understanding.

!!! warning
    Important cautions to prevent errors or unintended behavior.

!!! tip
    Practical advice to help you work more efficiently.

!!! important
    Key information you should not overlook.

!!! failure
    Common mistakes or potential failures to watch out for.