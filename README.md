# CMPS 2200  Recitation 01

**Name (Team Member 1):** Justin Green

**Name (Team Member 2):**_________________________

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`. All tests are in `test_main.py`.

## Install Python Dependency

We need Python library of "tabulate" to visualize the results in a good shape. Please install it by running 'pip install tabulate' or 'pip install -r requirements.txt' in Shell Tab of Repl.  

## Running and testing your code

- To run tests, from the command-line shell, you can run
  + `pytest test_main.py` will run all tests
  + `pytest test_main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Git" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest test_main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

The universal worst case is if the key is not in the list provided. Worst-case input value of 'key' for 'linear_search' would be the very last in the list, since it searches from start to finish of the list. Worst-case input value of 'key' for 'binary_search' would be first or last in the list, since the algorithm has to complete the maximum amount of splits to get to either end of the list.

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

The best case input value of 'key' for 'linear_search' is the first element since linear search will start searching from the first element of the list. The best case input value of 'key' for 'binary_search' is the very middle of the list, since binary search will start there when it initially divides the list into two.
- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest test_main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

|      n |   linear |   binary |
|--------|----------|----------|
| 100000 |    3.490 |    0.009 |

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

With a list size of 100,000, the binary search algorithm has a speedup of 388x. If we use the predicted speed by big O, we get 16.6 steps in binary, meaning linear took 6020x longer with 100,000 steps. While the ratios are not equal, binary is much faster than linear, both theoretically and empirically. 

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? Θ(kn)
  + For binary search? Θ(n² + k log n)
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? n² + k log n < kn -> n² < k(n - log n) -> k > n²/n - log n -> k >~ n since n² / n - log n is basically almost n (ex: n = 10000, n² / n - log n = 10004.0008; n = 100, n² / n - log n = 102.04). So when k is larger or about the same as n, you should sort, then use binary. If k is smaller than n, you should most likely just use linear search.
