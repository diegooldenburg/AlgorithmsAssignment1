

# CMPS 2200 Assignment 1

**Name:**Diego Oldenburg


In this assignment, you will learn more about asymptotic notation, parallelism, functional languages, and algorithmic cost models. As in the recitation, some of your answer will go here and some will go in `main.py`. You are welcome to edit this `assignment-01.md` file directly, or print and fill in by hand. If you do the latter, please scan to a file `assignment-01.pdf` and push to your github repository. 
  
  

1. (2 pts ea) **Asymptotic notation**

  - 1a. Is $2^{n+1} \in O(2^n)$? Why or why not? 
.  Yes, because 2 * 2^n >= 2^n+1 when c = 2 nnode = 0 
.  
.  
.  
. 
  - 1b. Is $2^{2^n} \in O(2^n)$? Why or why not?     
.  Yes, because 3(2^n) >= 2^(2^n) when c = 3 and nnode = 0
.  
.  
.  
.  
  - 1c. Is $n^{1.01} \in O(\mathrm{log}^2 n)$?    
.  
.  Yes, because log^2(n) >= n^(1.01) when c = 1 and nnode = 1
.  
.  

  - 1d. Is $n^{1.01} \in \Omega(\mathrm{log}^2 n)$?  
.  No, because there exists no constant c such that g(n)<=f(n) for all n greater than some n node
.  
.  
.  
  - 1e. Is $\sqrt{n} \in O((\mathrm{log} n)^3)$?
  Yes, because 2 * (log(n))^3 >= sqrt(n) when c = 2 and nnode = 20
.  
.  
.  
.  
  - 1f. Is $\sqrt{n} \in \Omega((\mathrm{log} n)^3)$?  
.  Yes, because (log(n))^3 <= sqrt(n) when c = 1 and nnode = 0
.  
.  
.  

  - 1g. Consider the definition of "Little o" notation:
  
$g(n) \in o(f(n))$ means that for **every** positive constant $c$, there exists a constant $n_0$ such that $g(n) \le c \cdot f(n)$ for all $n \ge n_0$. There is an analogous definition for "little omega" $\omega(f(n))$. The distinction between $o(f(n))$ and $O(f(n))$ is that the former requires the condition to be met for **every** $c$, not just for some $c$. For example, $10x \in o(x^2)$, but $10x^2 \notin o(x^2)$.  

.  

**Prove** that $o(g(n)) \cap \omega(g(n))$ is the empty set.  

.1) Let f(n) = x^2 and g(n) = x
.2) Let us assume that f(n) o(g(n)) and w(g(n))
.3) This would mean that f(n) >= c* g(n) and f(n) <= c * g(n), which is not possible
.4) Therefore, this set would be empty
.  
.  
.  
.  
.  
.  
.  
.  


2. (3 pts) **Python to SPARC**
 
Recall the `sum_list_recursive_parallel` function from lecture 2. Specify our implementation in SPARC here.  

.  sum_list_recursive_parallel(a) =
.   if |a| == 1:
.     a
.  (b, c) = sum_list_recursive_parallel (:a//2) || sum_list_recursive_parallel (a//2:)
.  return b, c
.  end
.  
.  
.  
.  
.  
.  
.
.  
.  
.  
.  




3. **SPARC to Python**

Consider the following SPARC code:  
$$
\begin{array}{l}
\mathit{foo}~x =   \\
~~~~\texttt{if}{}~~x \le 1~~\texttt{then}{}\\
~~~~~~~~x\\   
~~~~\texttt{else}\\
~~~~~~~~\texttt{let}{}~~(ra, rb) = (\mathit{foo}~(x-1))~~,~~(\mathit{foo}~(x-2))~~\texttt{in}{}\\  
~~~~~~~~~~~~ra + rb\\  
~~~~~~~~\texttt{end}{}.\\
\end{array}
$$ 

  - 3a. (4 pts) Translate this to Python code -- fill in the `def foo` method in `main.py`  

  - 3b. (2 pts) What does this function do, in your own words?  
Basically, this function subtracts from x until it x <= 1. It uses ra and rb as placeholder variables to show how close you are getting to the base case.
.  
.  
.  
.  
.  
.  
  


4. **Parallelism and recursion**

Consider the following function:  

```python
def longest_run(myarray, key)
   """
    Input:
      `myarray`: a list of ints
      `key`: an int
    Return:
      the longest continuous sequence of `key` in `myarray`
   """
```
E.g., `longest_run([2,12,12,8,12,12,12,0,12,1], 12) == 3`  
 
  - 4a. (8 pts) First, implement an iterative, sequential version of `longest_run` in `main.py`.  

  - 4b. (4 pts) What is the Work and Span of this implementation?  

.  O(n)
.  
.  
.  
.  
.  
.  
.  
.  


  - 4c. (8 pts) Next, implement a `longest_run_recursive`, a recursive, divide and conquer implementation. This is analogous to our implementation of `sum_list_recursive`. To do so, you will need to think about how to combine partial solutions from each recursive call. Make use of the provided class `Result`.   

  - 4d. (4 pts) What is the Work and Span of this sequential algorithm?  
.  O(n^2)
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  


  - (3 pts) 4e. Assume that we parallelize in a similar way we did with `sum_list_recursive`. That is, each recursive call spawns a new thread. What is the Work and Span of this algorithm?  

.  O(n^2)
.  
.  
.  
.  
.  
.  
.  

