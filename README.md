# 19.5
## Initializing and Manipulating Arrays

<ul>
  <li>PHP provides the capability to store data in arrays. Arrays are
      </br>divided into elements that behave as individual variables.
      </br>Array names, like other variables begin with the $ symbol.</li>
  <li>Individual array elements are accessed by following the
    </br>array's variable name with an index enclosed in the square
    </br>brackets([]).</li>
  <li><i>If a value is assigned to an array element of an array that
    </br>does not exist, then the array is created.</i> Likewise, assigning a
    </br>value to an element where the index is omitted appends a
    </br>new element to the end of the array.</li>
  <li>Function count returns the total number of elements in the
    </br>array.</li>
  <li>Function array creates an array that contains the arguments
    </br>passed to it. The first item in the argument list is stored as
    </br> the first array element(index 0), the second item is stored as 
    </br>the second array element and so on.</li>
</ul>

### (Cont.)

<ul>
  <li>Arrays with nonnumeric indices are called
    </br>associative arrays.</li>
  <li>You can create an associative array using the
    </br>operator =>, where the value to the left of the
    </br>operator is the array index and the value to the
    </br>right is the element's value.</li>
  <li>PHP provides functions for iterating through the
    </br>elements of an array.</li>
  <li>Each array has a built-in interal pointer, which
    </br>points to the array element currently being
    </br>referenced.</li>
  <li>Function reset sets the interal pointer to the first
    </br>array element. Function key returns the index of
    </br>the element currently referenced by the internal
    </br>pointer, and function next moves the internal
    </br>pointer to the next element.</li>
</ul>

