Download Link: https://assignmentchef.com/product/solved-eecs-1015-lab-7-writing-testing-code-for-use-with-pytest
<br>



<ol start="2">

 <li><strong>LAB 7 – TASK</strong></li>

</ol>

<strong>Lab 7 – Writing test cases for code </strong>

<strong>STARTING CODE LIN</strong><strong>K</strong><a href="https://www.eecs.yorku.ca/~mbrown/Lab7_start.py">:</a> <a href="https://www.eecs.yorku.ca/~mbrown/Lab7_start.py">https://www.eecs.yorku.ca/~mbrown/Lab7_start.py</a>  <strong> </strong>

The starting code is also shown here.  There are three functions of importance (shown in blue)

import pytest

from typing import List




# Accepts a list of integers

def initializeMinMaxList(myList: List[int]) -&gt; None:   # given     myList.sort()




def insertItem(myList: List[int], item: int) -&gt; None:  # given     myList.append(item)     myList.sort()




def getMinMax(myList: List[int], minormax: str) -&gt; int:   # given — but requires additional assert     assert minormax.upper()==”MAX” or minormax.upper()==”MIN”, “2nd argument must be ‘Min’ or ‘Max’ ”     result: int     if minormax == “MAX”:         result = myList[-1]         del myList[-1]     else:         result = myList[0]         del myList[0]     return result




# Main function is given. def main():     aList = [10, 11, 99, 1, 55, 100, 34, 88]     print(“Starting List: “, aList)     initializeMinMaxList(aList)     min1 = getMinMax(aList, “MIN”)     print(“1st min: %d” % (min1))     min2 = getMinMax(aList, “MIN”)     print(“2nd min: %d” % (min2))     max1 = getMinMax(aList, “MAX”)     print(“1st max: %d” % (max1))     max2 = getMinMax(aList, “MAX”)     print(“2nd max: %d” % (max2))




print(“Insert %d %d %d %d” % (min1 – 1, min2 – 1, max1 + 1, max2 + 1))     insertItem(aList, min1 – 1)     insertItem(aList, min2 – 1)     insertItem(aList, max1 + 1)     insertItem(aList, max2 + 1)




min1 = getMinMax(aList, “MIN”)     print(“1st min: %d” % (min1))     min2 = getMinMax(aList, “MIN”)     print(“2nd min: %d” % (min2))     max1 = getMinMax(aList, “MAX”)     print(“1st max: %d” % (max1))     max2 = getMinMax(aList, “MAX”)     print(“2nd max: %d” % (max2))




print(“DONE.  Please Enter to exit.”)     input()

if __name__ == “__main__”:

main()







<strong>What does the code provided do? </strong>

The code provides a set of functions that implements a “minmax list” of integers.  There are three functions we will use to with the minmax list, namely initializeMinMaxList() , insertItem() , and getMinMax().

The minmax-list works as follows.

(1) Assume you have a list of integers.

e.g., x = [20, 99, 88, 1, 100, 0]




(2) Call function initializeMinMaxList( List[int] ) -&gt; None

e.g., initializeMinMaxList(x)




<ul>

 <li>After it has been initialized, you can insert items into the list using insertItem( List[int], int) -&gt; Noneg., insertItem(x, 10), insertItem(x,-1)</li>

</ul>




<ul>

 <li>To exact the min or max from the list, call function getMinMax( List[int], str=”MIN” or “MAX”) -&gt; int minItem = getMinMax( x, “MIN”) maxItem = getMinMax(x, “MAX”)</li>

</ul>

The function getMinMax() will return the minimum or maximum item from the list, and delete the item from the list.   getMinMax(List[int], str=”MIN” or “MAX”) has two pre-conditions.

<ul>

 <li>The string must be either “MIN” or “MAX” – if not, the code will raise an assertion error.</li>

 <li>The List[int] must not be empty. If it is, the code should raise an assertion error.</li>

</ul>

See main() to see example usage of the minmaxList functions.

Running the code provided to you will give the following output.

Starting List:  [10, 11, 99, 1, 55, 100, 34, 88]

1st min: 1

2nd min: 10

1st max: 100

2nd max: 99

Insert 0 9 101 100

1st min: 0

2nd min: 9

1st max: 101

2nd max: 100

DONE.  Type Enter to exit.See next page for Lab 7’s TASKS




<strong>Lab 7’s TASKs </strong>

<strong>TASK 1 – Checking Pre-condition for empty list [modify </strong>getMinMax() <strong>] </strong>

Modify the function getMinMax(List[int], str) to include an assert statement to check the pre-condition that the list is not empty.   There is already an assert checking if the str is either “MIN” or “MAX”.

<strong>TASK 2 – Test functions for our code. [write five (5) Pytest functions] </strong>

Modify the starting code to include the following five (5) test functions for use with Pytest.

These functions should appear at the end of the current code.   Please name your functions exactly as shown below.

(1) def test_getMinMaxCase1():

<em>This function will test a standard use case for our minmaxList.</em>

<ul>

 <li>Create a list with two items that are different.</li>

 <li>Call initializeList() with (a).</li>

 <li>Use getMinMax() to get the mimimum item. Use an assert statement to check if this is correct.</li>

</ul>

Error message should be “Min should be x”, where x is the minimum item in the list specified in (a).

<ul>

 <li>Use getMinMax() to get the maximum item. Use an assert statement to check if this is correct.</li>

</ul>

Error message should be “Max should be x”, where x is the maximum item in the list specified in (a).

(2) def test_getMinMaxCase2():

<em>This function will test an edge case where the list only has a single item.</em>

<ul>

 <li>Create a list with only 1 item, let’s call this item y.</li>

 <li>Call initializeList() with (a).</li>

 <li>Use getMinMax() to get the mimimum item (which is y). Use an assert statement to check if this is correct.</li>

</ul>

Error message should be “Min should be y”, where y is the single item in your list in (a).

<ul>

 <li>Use insertItem() to insert the same item y back into the list in (a).</li>

 <li>Use getMinMax() to get the maximum item (which is y). Use an assert statement to check if this is correct.</li>

</ul>

Error message should be “Max should be y”, where y is the maximum item in the list specified in (a).

(3) def test_getMinMaxCase3():

<em>This function will test an edge case where the list starts out empty. </em>

<ul>

 <li>Create an empty list.</li>

 <li>Call initializeList() with (a).</li>

 <li>Insert an item x into (a) using insertItem().</li>

 <li>Insert an item y into (a) using insertItem(). <em>Item y should be larger than x.</em></li>

 <li>Use getMinMax() to get the mimimum item. Use an assert statement to check if this is correct.</li>

</ul>

Error message should be “Min should be x”, where x is the minimum item inserted into (a).

<ul>

 <li>Use getMinMax() to get the maximum item. Use an assert statement to check if this is correct. Error message should be “Max should be y”, where y is the maximum item inserted into (a).</li>

</ul>

(4) def test_getMinMaxRequestError()

<em>This function will test to see if </em><em>getMinMax()</em> <em>properly causes an assertion error when the string argument is not correct.</em>

<ul>

 <li>Create a list with 3 items.</li>

 <li>Call initializeList() with (a).</li>

 <li>Call getMinMax() with a, but using “MID” instead of “MIN” or “MAX”. This will cause getMinMax() to raise an AssertionError.</li>

 <li>Check if the AssertionError was raised. Assert on this condition, if the condition was not rasie, your error should be:</li>

</ul>

“Should raise AssertionError!”

<strong>Continues on next page.                                                                         </strong>




(5) def test_getMinMaxEmptyError():

<em>This function will test to see if </em><em>getMinMax()</em> <em>properly causes an assertion error when the list is empty.</em>

<ul>

 <li>Create an empty list.</li>

 <li>Call initializeList() with (a).</li>

 <li>Call getMinMax(). If you did Task 1 correctly, this will cause getMinMax() to raise an AssertionError.</li>

 <li>Check if the AssertionError was raised. Assert on this condition, if the condition was not rasie, your error should be:</li>

</ul>

“Should raise AssertionError!”

<strong>VERIFYING YOU TEST FUNCTIONS WITH PYTEST </strong>

Remember to first install Pytest using the pip command as described in the notes.  Now, verify that your test functions work by using “pytest lab7.py” from PyCharm’s terminal.

To the best of our knowledge, the code provided to you does not have any bugs, so the 5 test should all pass if written correctly.

The expected output would look as follows.

(venv) C:UsersmbrownPycharmProjectspythonProject1&gt;pytest Lab7.py ==================== test session starts ====================  platform win32 — Python 3.8.5, pytest-6.1.2, py-1.9.0, pluggy-0.13.1 rootdir: C:UsersmbrownPycharmProjectspythonProject1

collected 5 items




Lab7.py …..

[100%]




==================== 5 passed in 0.04s ====================




NOTE: You can force a failure of your test cases by commenting out one of the assert statements in the function getMinMax().








