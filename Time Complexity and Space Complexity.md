# Time Complexity vs Space Complexity
The main difference is that **Time Complexity** *measures the amount of computer time that it takes to run a program* while **Space Complexity** *measures the amount of memory space needed by the program*. [link](https://courses.cs.northwestern.edu/311/html/space-complexity.html) or [two](https://www.studytonight.com/data-structures/space-complexity-of-algorithms)
## [Time Complexity](https://en.wikipedia.org/wiki/Time_complexity)
- measures the amount of computer time that it takes to run a program, or in other words, the amount of operations that will be done by the computer
### Big O Notation
- how **Time Complexity** is measured
- is used to classify algorithms according to how their run time or space requirements grow as the input size grows
- characterizes functions according to their growth rates: different functions with the same growth rate may be represented using the same O notation (like how <img src="https://render.githubusercontent.com/render/math?math=x^2"> and <img src="https://render.githubusercontent.com/render/math?math=\sqrt{x^4-1}"> have the same growth rate">
- since it is asymptomatic, or refers to a very large x, it is basically an End Behavior Model(EBM) where we don't care about the smaller terms (i.e if we have O(<img src="https://render.githubusercontent.com/render/math?math=n^2 %2B n">) we would just use O(<img src="https://render.githubusercontent.com/render/math?math=n^2">)
### Constant Complexity
- the best of the best
- operation always completes in the same amount of CPU time regardless of the input size
- ex. 
  ```java
  int returnFirst(int[] arr){
   //arr has a length of n
   arr[0] = 2;
   return arr[0];
   }
  ```
- this is O(1), even though it takes 2 operations to complete (```arr[0]=2;``` and ```return arr[0]```) as it only does a fixed number of operations no matter the input size so it is O(1)
### Logarithmic Complexity
- still very very good
- operation grows logarithmically in relation to the input
- is really <img src="https://render.githubusercontent.com/render/math?math=\log_{a}n"> where *a* is a constant but we just get rid of the *a* and use <img src="https://render.githubusercontent.com/render/math?math=\log{n}">
- ex.
  ```java
    int binarySearch(int arr[], int left, int right, int x)
    {
        if (right>=l)
        {
            int mid = left + (right - left)/2;
  
            // If the element is present at middle of the array
            if (arr[mid] == x)
               return mid;
  
            // If element is smaller than middle, then it has to be to the left
            if (arr[mid] > x)
               return binarySearch(arr, l, mid-1, x);
  
            // Else the element can only be present in the right
            return binarySearch(arr, mid+1, r, x);
        }
  
        // Only reached if element is not in array
        return -1;
    }
    ```
- the binary search is the perfect example because it is technically O( <img src="https://render.githubusercontent.com/render/math?math=\log_{2}n">) which is O(<img src="https://render.githubusercontent.com/render/math?math=\log{n}">)
  - this essentially means that if you double the size of the array, there would only be one more computation needed
### Linear Complexity
- its okay (O(k) hah), could be worse
- the number of computations increases linearly with the number of elements
- ex.
  ```java
  int sum(int[] arr){
    int total = 0;
    int n = arr.length;
    for(int i = 0; i<n; i++){
      total += arr[i];
    }
    return total;
  
  }
  ```
- its linear because the number of computations increases by a set number every time the size of the array increases (if we want to be technical we can say that this is O(<img src="https://render.githubusercontent.com/render/math?math=n %2B 3">) but the *3* doesn't matter so we just say O(<img src="https://render.githubusercontent.com/render/math?math=n">))








[<img align = "right" src="https://github.com/Snipexkillo/notes/blob/fbb9498c1ab5367331fb6c1868e70927b326e408/images/Know%20Thy%20Complexities.jpeg?raw=true" width="700"/>](https://github.com/Snipexkillo/notes/blob/fbb9498c1ab5367331fb6c1868e70927b326e408/images/Know%20Thy%20Complexities.jpeg?raw=true)

