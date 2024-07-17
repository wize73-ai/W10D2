# W10D2 equal stacks problem hackerrank #

You have three stacks of cylinders where each cylinder has the same diameter, but they may vary in height. You can change the height of a stack by removing and discarding its topmost cylinder any number of times.

Find the maximum possible height of the stacks such that all of the stacks are exactly the same height. This means you must remove zero or more cylinders from the top of zero or more of the three stacks until they are all the same height, then return the height.

Example

There are  and  cylinders in the three stacks, with their heights in the three arrays. Remove the top 2 cylinders from  (heights = [1, 2]) and from  (heights = [1, 1]) so that the three stacks all are 2 units tall. Return  as the answer.

    Note: An empty stack is still a stack.

Function Description

    Complete the equalStacks function in the editor below.

        equalStacks has the following parameters:

            int h1[n1]: the first array of heights
            int h2[n2]: the second array of heights
            int h3[n3]: the third array of heights
        Returns
            int: the height of the stacks when they are equalized

Input Format

The first line contains three space-separated integers, , , and , the numbers of cylinders in stacks , , and . The subsequent lines describe the respective heights of each cylinder in a stack from top to bottom:

The second line contains  space-separated integers, the cylinder heights in stack . The first element is the top cylinder of the stack.
The third line contains  space-separated integers, the cylinder heights in stack . The first element is the top cylinder of the stack.
The fourth line contains  space-separated integers, the cylinder heights in stack . The first element is the top cylinder of the stack.
Constraints

Sample Input

STDIN       Function
-----       --------
5 3 4       h1[] size n1 = 5, h2[] size n2 = 3, h3[] size n3 = 4  
3 2 1 1 1   h1 = [3, 2, 1, 1, 1]
4 3 2       h2 = [4, 3, 2]
1 1 4 1     h3 = [1, 1, 4, 1]
Sample Output

5


# Complete the 'equalStacks' function below.
#
# The function is expected to return an INTEGER.
# The function accepts following parameters:
#  1. INTEGER_ARRAY h1
#  2. INTEGER_ARRAY h2
#  3. INTEGER_ARRAY h3
#

def equalStacks(h1, h2, h3):
    
    import math
import os
import random
import re
import sys



submission one final _____  elegant O(n) possible space complexity of O(n)

Time Complexity: O(n1 + n2 + n3)
Space Complexity: O(n1 + n2 + n3)



def equalStacks(h1, h2, h3):
    # set up stacks
                    stacks have been passed in correct fashion, set up sum values
                    
    sum1, sum2, sum3 = map(sum, (h1, h2, h3))
    
    while not (sum1 == sum2 == sum3):           will iterate while the sums are unequal
        if sum1 >= sum2 and sum1 >= sum3:           if sum1 is biggest pop index 0
            sum1 -= h1.pop(0)
        elif sum2 >= sum1 and sum2 >= sum3:         if sum2 is biggest pop index 0
            sum2 -= h2.pop(0)
        else:
            sum3 -= h3.pop(0)                       if sum1 and sum2 arent biggest, sum3 is so pop index 0
    return sum1        
                                                    all sums equal by this evaluation so return any one value


________Brute force attempt would not pass all cases.. streamlined the logic to the above

import math
import os
import random
import re
import sys

def equalStacks(h1, h2, h3):
    # set up stacks
    st1 = h1
    st2 = h2
    st3 = h3
    # top of stack is index 0
    # find the sum of three stacks
    length_stack1 = n1
    length_stack2 = n2
    length_stack3 = n3
    
    
    sum_stack1 = sum(st1)
    sum_stack2 = sum(st2)
    sum_stack3 = sum(st3)
    
    min_stack = min(sum_stack1, sum_stack2, sum_stack3)
    max_stack = max(sum_stack1, sum_stack2, sum_stack3)
    
   
    
    # compare the sums to find the highest sum and lowest sum
    # print(sum_stack1, sum_stack2, sum_stack3)
    
    
    print("stp:", st1, sum_stack1, st2, sum_stack2, st3, sum_stack3)
    while ((min_stack+max_stack)/2) > min_stack:
        min_stack = min(sum(st1), sum(st2), sum(st3))
        max_stack = max(sum(st1), sum(st2), sum(st3))
    
        if max_stack == min_stack:
            return min_stack
            
        if sum_stack1 == max_stack:
           
            if sum_stack1 > min_stack and length_stack1 > 0:
                st1 = st1[1:]
                sum_stack1 = sum(st1)
                print(f"sum str1 updated to {sum_stack1}")
        if sum_stack2 == max_stack:
            
            if sum_stack2 > min_stack and length_stack2 > 0:
                st2 = st2[1:]
                sum_stack2 = sum(st2)
                print(f"sum str2 updated to {sum_stack2}")
        if sum_stack3 == max_stack:
            if sum_stack3 > min_stack and length_stack3 > 0:
                st3 = st3[1:]
                sum_stack3 = sum(st3)
                print(f"sum str3 updated to {sum_stack3}")
        print("stp:", st1, sum_stack1, st2, sum_stack2, st3, sum_stack3)
                
        if sum_stack1 == sum_stack2 == sum_stack3 == min_stack:
            
            return min_stack
            
        
    
