# Comp303: Computer Architecture Assignment 2
###### Sitare Arslantürk
In this assignment, insertion sort algorithm with duplicate removal and reduction is implemented using MIPS assembly language via the MARS MIPS simulator. 

## Section 1: Sorting

### Size of the List
The user is prompted to enter the size of the list. The given input is checked if it is a possible size (N>0). If N is an invalid input, the program gives the error message of "Argument error" and exits.Then N is saved to $s0 to be used for the remaining of the program.  

### Data Inputs
The following pseudocode represents the logic of saving the data inputs into the input_data array. n is the size of the list, until all the inputs are saved into the array, the loop continues. The inputs have to be integers so each is checked for the conditions input>0 and input<9. If not, the program gives the error message of "Argument Error" and exits.

```JAVA
for(int i=0; i < n; n++){
    input_data[i] = user input
}
```
### Print Unordered List
Inside a for loop similar to the one used in getting the data inputs, each input inside the input_data is went through and printed to the console in the order they were entered by the user. To be style-friendly, one space is left between each of the integers. 

### Insertion Sort
The insertion sort algorithm is based on the following JAVA pseudocode. 

```JAVA
void insertionSort(int arr, int size) {
    int i, j;  
    for(i=1; i<size; i++) {  
         j=i;     
         while(j>0 && arr[j]<arr[j-1]) {
               swap(arr, j, j-1);          
               j--;    
         } 
    }
}
```

### Print Ordered List
Inside a for loop similar to the one used in getting the data inputs, each input inside the input_data is went through and printed to the console. Since the input_data is an ordered list of numbers, they are printed in increasing order. For style-friendliness, one space is left between each of the integers. 

## Section 2: Removing Duplicates
The duplicates inside the ordered list are removed following the below pseudocode. Since it is an ordered list, it is sufficient to check only the neighboring integer. Inside a for loop, each neighboring element is checked whether it equals to its neighbor or not. If it does not equal to the right neighbor than it is added to the new array input_data_removed. I created a new array for the new list to be put into. The last integer is not checked for this reason and added directly to the end of the new list. The new array's length is checked by j and is stored in $s2.

```JAVA
void removeDuplicates(int arr[], int n) 
{ 
    int temp[n]; 
    int j = 0; 
    for (int i=0; i<n-1; i++) {
        if (arr[i] != arr[i+1]) { 
            temp[j] = arr[i]; 
            j++;
        }
    }
    temp[j] = arr[n-1]; 
    j++;
} 
```
### Print Ordered List
Inside a for loop similar to the one used in printing previous data inputs, each input inside the input_data_removed is went through and printed to the console. The size for the loop is the new size of the new array input_data_removed. Since the input_data_removed is an ordered list of numbers, they are printed in increasing order. For style-friendliness, one space is left between each of the integers. 

## Section 3: Reduction
For reduction, all the elements inside the input_data_removed are iterated through and added to the sum. Following is the JAVA pseudocode for the MIPS implementation.

```JAVA
void sum(){ 
         int sum = 0; 
         for (int i = 0; i < arr.length; i++) {
            sum +=  arr[i]; 
         }
} 
```
The result is summed up in $t3 and printed in the end.

## End

After performing all of the three sections, the program terminates.
