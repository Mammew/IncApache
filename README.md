# incApache Report

**Authors:**
* Elena Deidda - 5448731[cite: 4]
* Marco Mammoliti - 5564736[cite: 4]
* Filippo Pedullà - 5575626[cite: 4]

**Date:** 29/12/2023[cite: 4]

## Laboratory Objective
The incApache laboratory consists of creating a web server in C[cite: 4].

## Introduction
This report outlines the methodology used both to implement the code and for the debugging phase[cite: 4]. The current version of the project includes working 7.0 and 7.1 methods, plus an initial draft for handling the POST method[cite: 4].

## Methodology Used
Starting from the `main` function, we examined the logic of the already implemented functions[cite: 4]. Any gaps were addressed and resolved by consulting the manual, watching dedicated videos, and delving into the explanations provided in class[cite: 4]. Discussing things within the group allowed us to find suitable solutions for the missing parts, thereby improving the overall robustness of the code and ensuring that each function was implemented accurately and completely[cite: 4].

In version 7.0, the main time-consuming obstacle was understanding and implementing the `send_response` function[cite: 4]. Once that was completed and understood, the rest of the flow became much smoother and simpler[cite: 4]. Regarding version 7.1, the data structure posed a challenge, particularly figuring out how to use the `to_join` array to include the thread preceding the one just created[cite: 4].

### Using the `to_join` array
The `to_join` array was populated using direct array addressing[cite: 5]. The first four cells were reserved for the last created response thread, while the previous thread was inserted into an unused cell (`new_thread_idx`) of the array[cite: 5]. This ensures that in the *i-th* position of the `to_join` structure, there is exactly the previous thread compared to the one present in the same position of the `thread_ids` structure[cite: 5].

Once we fully understood the data structure and populated the array, we successfully implemented the `join_prev` and `join_all` functions, which allowed us to reflect on the concept of a thread and its correct usage[cite: 5].

## Encountered Problems
The implementation of the synchronization (join) functions required a considerable amount of time due to some initial misunderstandings[cite: 5]:
* In a first version, `join_prev` waited for all threads prior to the one passed as an argument[cite: 5]. However, by analyzing where it was called, we realized it only needed to perform the join on the thread immediately preceding the specified one[cite: 5].
* Similarly, `join_all` was initially implemented to wait for all threads[cite: 5]. We later realized that since each response thread invokes `join_prev` to wait for the previous response thread before proceeding, `join_all` only needed to be called on the last created response thread[cite: 5].

The final complication emerged during the creation of the dynamic page, which still presents some issues that we are currently trying to resolve[cite: 5, 6].

## Debugging
Throughout the debugging process, we frequently adopted the method of printing essential data to the screen in order to understand the values they took on at specific points in the program[cite: 5].

## Code Completeness
Currently, the project ensures the correct functioning of the web server for both the 7.0 and 7.1 features[cite: 6]. The POST method is present in the code structure, but the requested dynamic page is still under development[cite: 6].
