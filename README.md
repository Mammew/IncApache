# incApache Report

**Authors:**
* Elena Deidda - 5448731
* Marco Mammoliti - 5564736
* Filippo Pedullà - 5575626

**Date:** 29/12/2023

## Laboratory Objective
The incApache laboratory consists of creating a web server in C.

## Introduction
This report outlines the methodology used both to implement the code and for the debugging phase. The current version of the project includes working 7.0 and 7.1 methods, plus an initial draft for handling the POST method.

## Methodology Used
Starting from the `main` function, we examined the logic of the already implemented functions. Any gaps were addressed and resolved by consulting the manual, watching dedicated videos, and delving into the explanations provided in class. Discussing things within the group allowed us to find suitable solutions for the missing parts, thereby improving the overall robustness of the code and ensuring that each function was implemented accurately and completely.

In version 7.0, the main time-consuming obstacle was understanding and implementing the `send_response` function. Once that was completed and understood, the rest of the flow became much smoother and simpler. Regarding version 7.1, the data structure posed a challenge, particularly figuring out how to use the `to_join` array to include the thread preceding the one just created.

### Using the `to_join` array
The `to_join` array was populated using direct array addressing. The first four cells were reserved for the last created response thread, while the previous thread was inserted into an unused cell (`new_thread_idx`) of the array. This ensures that in the *i-th* position of the `to_join` structure, there is exactly the previous thread compared to the one present in the same position of the `thread_ids` structure.

Once we fully understood the data structure and populated the array, we successfully implemented the `join_prev` and `join_all` functions, which allowed us to reflect on the concept of a thread and its correct usage.

## Encountered Problems
The implementation of the synchronization (join) functions required a considerable amount of time due to some initial misunderstandings:
* In a first version, `join_prev` waited for all threads prior to the one passed as an argument. However, by analyzing where it was called, we realized it only needed to perform the join on the thread immediately preceding the specified one.
* Similarly, `join_all` was initially implemented to wait for all threads. We later realized that since each response thread invokes `join_prev` to wait for the previous response thread before proceeding, `join_all` only needed to be called on the last created response thread.

The final complication emerged during the creation of the dynamic page, which still presents some issues that we are currently trying to resolve 6].

## Debugging
Throughout the debugging process, we frequently adopted the method of printing essential data to the screen in order to understand the values they took on at specific points in the program.

## Code Completeness
Currently, the project ensures the correct functioning of the web server for both the 7.0 and 7.1 features. The POST method is present in the code structure, but the requested dynamic page is still under development.
