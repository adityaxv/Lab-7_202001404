# Lab-7_202001404
# Aditya Patel
# 202001404

## Previous Date Problem

### Equivalence Partitioning Test Cases:

        package tests;
        
        import static org.junit.Assert.assertEquals;
        import java.time.LocalDate;
        import org.junit.Test;

        public class PreviousDateTest {
        @Test
        public void test() {
        
		   // Test case 1: Valid input
        int day1 = 1, month1 = 1, year1 = 1900;
        LocalDate expected1 = LocalDate.of(1899, 12, 31);
        LocalDate result1 = PreviousDate.getPreviousDate(day1, month1, year1);
        assertEquals(expected1,result1);

        // Test case 2: Invalid day
        int day2 = 32, month2 = 12, year2 = 2023;
        LocalDate expected2 = null;
        LocalDate result2 = PreviousDate.getPreviousDate(day2, month2, year2);
        assert result2 == expected2;

        // Test case 3: Invalid month
        int day3 = 15, month3 = 13, year3 = 2024;
        LocalDate expected3 = null;
        LocalDate result3 = PreviousDate.getPreviousDate(day3, month3, year3);
        assert result3 == expected3;

        // Test case 4: Invalid years
        int day4 = 1, month4 = 1, year4 = 1800;
        LocalDate expected4 = null;
        LocalDate result4 = PreviousDate.getPreviousDate(day4, month4, year4);
        assert result4 == expected4;
	    }
    }



**Test Cases**
| Test Case ID | Day | Month | Year | Expected Output |
| -------------|-----|-------|------|-----------------|
| 1 | 1 | 6 | 2000 | 31-5-2000 |
| 2 | 2 | 6 | 2015 | 1-6-2015 |
| 3 | 2 | 6 | 2016 | Invalid |
| 4 | 1 | 1 | 1900 | 31-12-1899 |
| 5 | 31 | 12 | 1899 | Invalid |
| 6 | 31 | 12 | 1900 | 30-12-1900 |
| 7 | 29 | 2 | 2012 | 28-2-2012 |
| 8 | 1 | 3 | 2012 | 29-2-2012 | 
| 9 | 29 | 2 | 2011 | Invalid |
| 10 | 30 | 2 | 2020 | Invalid |


**Equivalence Class Partitions** <br/>
Day:
| Partition ID | Range | Status |
|----------------------|-------|--------|
| E1 | Between 1 and 28 | Valid |
| E2 | Less than 1 | Invalid |
| E3 | Greater than 31 | Invalid |
| E4 | Equals 30 | Valid |
| E5 | Equals 29 | Valid for leap year |
| E6 | Equals 31 | Valid |

Month:
| Partition ID | Range | Status |
|----------------------|-------|--------|
| E7 | Between 1 and 12 | Valid |
| E8 | Less than 1 | Invalid |
| E9 | Greater than 12 | Invalid |

Year: 
| Partition ID | Range | Status |
|----------------------|-------|--------|
| E10 | Between 1900 and 2015 | Valid |
| E11 | Less than 1 | Invalid |
| E12 | Greater than 2015 | Invalid |

## Program 1
**Equivalence partition for linear search**

      import org.junit.Test;
      import static org.junit.Assert.*;

      public class LinearSearchTest {

        @Test
        public void testExistingValue() {
          int[] arr = {1, 2, 3, 4, 5};
          int index = linearSearch(3, arr);
          assertEquals(2, index);
        }

        @Test
        public void testNonExistingValue() {
          int[] arr = {1, 2, 3, 4, 5};
          int index = linearSearch(6, arr);
          assertEquals(-1, index);
        }

        @Test
        public void testFirstElement() {
          int[] arr = {1, 2, 3, 4, 5};
          int index = linearSearch(1, arr);
          assertEquals(0, index);
        }

        @Test
        public void testLastElement() {
          int[] arr = {1, 2, 3, 4, 5};
          int index = linearSearch(5, arr);
          assertEquals(4, index);
        }

        @Test
        public void testEmptyArray() {
          int[] arr = {};
          int index = linearSearch(1, arr);
          assertEquals(-1, index);
        }

        @Test
        public void testNullArray() {
          int[] arr = null;
          int index = linearSearch(1, arr);
          assertEquals(-1, index);
        }
      }

| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [2, 4, 6, 8, 10], v = 2 | 0 |
| [1, 3, 5, 7, 9], v = 2 | -1 |
| [2, 4, 6, 8, 10], v = 11 | -1 |
| [-100, 100] | 0 |
| [1,2,3,4,5,6], v = 6 | 5 |
| [], v = 10 | -1 |
| NULL, v = 111 | -1 |

**Boundary value analysis**
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| NULL | -1 |
| [], v = 5 | -1 |
| [5], v = 5 | 0 |
| [5], v = 60 | -1 |
| [3,5], v = 3 | 0 |
| [3,5], v = 5 | 1 |
| [3,5], v = 14 | -1 |
| [1,3,5], v = 1 | 0 |
| [1,3,5], v = 5 | 2 |
| [1,3,5], v = 10 | -1 |
|[1,2,3,4,5,6,7,8,9,1,0,11,111], v = 1| 0 |
|[1,2,3,4,5,6,7,8,9,1,0,11,111], v = 111| 12 |
|[1,2,3,4,5,6,7,8,9,1,0,11,111], v = 1111| -1 |

## Program 2

      package tests;

      import static org.junit.Assert.*;
      import org.junit.Test;

      public class CountItemTest {

        @Test
          public void testValueCount() {
            int[] arr = {1, 2, 2, 4, 5};
            int count = CountItem.countItem(2, arr);
            assertEquals(2, count);
          }

        @Test
          public void testValueCount2() {
            int[] arr = {1, 2, 2, 4,5,4,5,6,7,5,3,4};
            int count = CountItem.countItem(4, arr);
            assertEquals(3, count);
          }

        @Test
          public void testEmptyArray() {
            int[] arr = {};
            int count = CountItem.countItem(5, arr);
            assertEquals(0, count);
          }

        @Test
          public void testEmptyArray2() {
            int[] arr = {};
            int count = CountItem.countItem(1, arr);
            assertEquals(1, count);
          }
      }
      
**Equivalence Class partitioning for counting occurance**
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [265, 41, 60, 80, 100], v = 100 | 1 |
| [2655, 451, 6560, 1050, 1050], v = 1050 | 2 |
| [[265545, 451, 65460, 1050, 105024]], v = 1 | 0 |
| [[10,10,10,10]], v = 11 | 0 |
| [], v = 100 | 0 |
| NULL, v = 51 | 0 |
| [0], v = 0 | 1 |
| [-89,-89], v = -89 | 2 |

**Boundary value analysis**
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [1, 2, 3, 4], v = 2 | 2 |
| 15, 10, 15, 15], v = 15 | 3 |
| [], v = 100 | 0 |
| NULL, v = 51 | 0 |
|[-100,100,100,100], v = 10000| 0 |
| [-89,89], v = -89 | 1 |
| [-890,890], v = 890 | 1 |

## Program 3
**Equivalent testcases for binary search:**

      package tests;

      import static org.junit.Assert.*;
      import org.junit.Test;

      public class BinarySearchTest {

        @Test
          public void test1() {
            int[] arr = {1, 2, 3, 4, 5,10,12};
            int valueIdx = BinarySearch.binarySearch(5, arr);
            assertEquals(4, valueIdx);
          }

        @Test
          public void test2() {
            int[] arr = {1, 2, 3, 4, 5,10,12};
            int valueIdx = BinarySearch.binarySearch(12, arr);
            assertEquals(6, valueIdx);
          }

        @Test
          public void test3() {
            int[] arr = {1, 2, 3, 4, 5,10,12};
            int valueIdx = BinarySearch.binarySearch(6, arr);
            assertEquals(0, valueIdx);
          }

        @Test
          public void test4() {
            int[] arr = {};
            int valueIdx = BinarySearch.binarySearch(4, arr);
            assertEquals(-1, valueIdx);
          }
      }

| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [1, 21, 30, 40, 50], v = 21 | 1 |
| [10, 20, 30, 40, 50, 60], v = 30 | 2 |
| [10,100,1000,10000], v = 100000 | -1 |
| [,11,22,33,44], v = 444 | -1 |
| [11,20,200,300], v = 11 | 0 |
| [-100,-90,-80,100,1000], v = 10000 | 4 |
| [], v = 12 | -1 |
| NULL, v = 168 | -1 |
| [1,2], v = 3 | -1 |
| [1,3], v = 3 | 1 |

**Boundary value analysis**
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [1, 2, 3, 4, 5], v = 2 | 1 |
| [1, 2, 2, 351, 551], v = 2 | 2 |
| [1,22,33,44,55], v = 66 | -1 |
| [2, 4, 6, 8, 10], v = 51 | -1 |
| [-100, 0, 1000], v = -100 | 0 |
| [-100, 0, 1000], v = 1000 | 2 |
| [], v = 0 | -1 |
| NULL,v = 4 | -1 |

## Program 4
**Equivalent class test cases of checking the type of triangle**

      package tests;

      import static org.junit.Assert.*;
      import org.junit.Test;

      public class TriangleTest {

         // invalid output
        @Test
          public void test1() {
            int valueIdx =Triangle.triangle(0,0,0);
            assertEquals(3, valueIdx);
          }

        //invalid
        @Test
          public void test2() {
            int valueIdx =Triangle.triangle(3,4,8);
            assertEquals(3, valueIdx);
          }

         // equilateral
        @Test
          public void tes3() {
            int valueIdx =Triangle.triangle(100,100,100);
            assertEquals(0, valueIdx);
          }

        // isosceles
        @Test
          public void test4() {
            int valueIdx =Triangle.triangle(4,4,5);
            assertEquals(1, valueIdx);
          }

        //scalene
        @Test
          public void test5() {
            int valueIdx =Triangle.triangle(5,4,3);
            assertEquals(2, valueIdx);
          }
      }

| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| a=2, b=2, c=2 | EQUILATERAL |
| a=1, b=1, c=1 | EQUILATERAL |
| a=0, b=0, c=0 | INVALID |
| a=-1, b=-1, c=-1 | INVALID |
| a=10, b=10, c=0 | INVALID |
| a=17, b=17, c=5 | ISOCELES |
| a=15, b=2, c=15 | ISOCELES |
| a=6, b=11, c=5 | SCALENE |
| a=16, b=21, c=25 | SCALENE |
| a=-1, b=21, c=25 | INVALID |
| a=2, b=3, c=4 | SCALENE |

**Boundary value analysis**
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| a=2, b=2, c=2 | EQUILATERAL |
| a=0, b=0, c=0 | INVALID |
| a=INT_MAX, b = INT_MAX, c = INT_MAX | EQUILATERAL |
| a=INT_MIN, b=INT_MIN, c=INT_MIN | INVALID |
| a=1, b=1, c=2 | ISOCELES |
| a=15, b=12, c=15 | ISOCELES |
| a = INT_MAX, b = 1, c = INT_MAX | ISOCELES |
| a=1,b=2,c=3 | SCALENE |
| a = INT_MAX, b = 1, c = INT_MAX - 1 | SCALENE |

## Program 5
**Equivalent test cases for prefix searching are as follows:**

      package tests;

      import static org.junit.Assert.*;
      import org.junit.Test;

      public class PrefixStringTest {

        @Test
        public void test1() {
          String s1 = "ad";
          String s2 = "aditya";
          boolean isPrefix = PrefixString.prefix(s1, s2);
          assertEquals(true,isPrefix);
        }

        @Test
        public void test2() {
          String s1 = "a";
          String s2 = "aditya";
          boolean isPrefix = PrefixString.prefix(s1, s2);
          assertEquals(false,isPrefix);
        }

        @Test
        public void test3() {
          String s1 = "abcr";
          String s2 = "a";
          boolean isPrefix = PrefixString.prefix(s1, s2);
          assertEquals(false,isPrefix);
        }

        @Test
        public void test4() {
          String s1 = "abc";
          String s2 = "def";
          boolean isPrefix = PrefixString.prefix(s1, s2);
          assertEquals(true,isPrefix);
        }
      }
      
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| s1= "abcd", s2 = "abcd" | true |
| s1 = "", s2 = "" | true |
| s1 = "ad", s2 = "aditya" | true |
| s1 = "adi", s2 = "ad" | false |
| s1 = "abc", s2 = "" | false |
| s1 = "", s2 = "abc" | true |
| s1 = "o", s2 = "ott" | true |
| s1 = "abc", s2 = "def" | false |
| s1 = "deg", s2 = "def" | false |

**Boundary value analysis**
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| s1= "abcd", s2 = "abcd" | true |
| s1= "", s2 = "" | true |
| s1= "abcd", s2 = "" | false |
| s1= "", s2 = "abcd" | true |
| s1 = "aef", s2 = "def" | false |
| s1 = "def", s2 = "deg" | false |
| s1 = "a", s2 = "att" | true |
| s1 = "poojan", s2 = "patel" | false |

## Program 6
**(a) All equivalent classes**
| Class ID | Class |
|----------|-------|
| E1 | All sides are positive |
| E2 | two of its sides are zero |
| E3 | One of its sides are negative |
| E4 | Sum of two sides is less than third side |
| E5 | Any of the side/sides is negative |

**(b) Identify test cases to cover the identified equivalence classes. Also, explicitly mention which test case would cover which equivalence class.**
| Test Case ID | Class ID | Test Case |
|--------------|----------|-----------|
| T1 | E1 | A = 1, B = 1, C = 1 |
| T2 | E1 | A = 3, B = 4, C= 5 |
| T3 | E2 | A = 0, B = 0, C = 1 |
| T4 | E3 | A = 0, B = 1, C = 2 |
| T5 | E4 | A = 1, B = 3, C = 8 |
| T6 | E5 | A = -1, C = 1, D = 5 |

**(c) For the boundary condition A + B > C case (scalene triangle), identify test cases to verify the boundary.** <br/>
A = 1, B = 3, C = 2

**(d) For the boundary condition A = C case (isosceles triangle), identify test cases to verify the boundary.** <br/>
A = 3,B = 2, C = 3

**(e) For the boundary condition A = B = C case (equilateral triangle), identify test cases to verify the boundary.**<br/>
A = 30, B = 30, C = 30

**(f) For the boundary condition A2 + B2 = C2 case (right-angle triangle), identify test cases to verify the boundary.** <br/>
A = 6, B = 8, C = 10

**(g)  For the non-triangle case, identify test cases to explore the boundary.**
A = 20, B = 10,C = 5

**(h) For non-positive input, identify test points.**

A = 0, B = 10, C = 0 <br/> 

A = 0, B = 0, C = 0 <br/>

A = 0, B = -1, C = 10 <br/>

# Section B
**1. Control Flow Graph (CFG)**:

![control-flow-diagram drawio](https://github.com/adityaxv/Lab-7_202001404/blob/main/Copy%20of%20Untitled%20Diagram.drawio.png)


## (2) Test Cases
### (a) Statement coverage test set:  In this all the statements in code should be covered

| Test Number | Test Case |
|-------------|-----------|
| 1 | p is empty array |
| 2 | p has one point object |
| 3 | p has two points object with different y component |
| 4 | p has two points object with different x component |
| 5 | p has three or more point object with different y component |

### (b) Branch Coverage test set: In this all branch are taken atleast once
<br/>

| Test Number | Test Case |
|-------------|-----------|
| 1 | p is empty array |
| 2 | p has one point object |
| 3 | p has two points object with different y component |
| 4 | p has two points object with different x component |
| 5 | p has three or more point object with different y component |
| 6 | p has three or more point object with same y component |
| 7 | p has three or more point object with all same x component |
| 8 | p has three or more point object with all different x component |
| 9 | p has three or more point object with some same and some different x component |

### (c) Basic condition coverage test set: Each boolean expression has been evaluated to both true and false

| Test Number | Test Case |
|-------------|-----------|
| 1 | p is empty array |
| 2 | p has one point object |
| 3 | p has two points object with different y component |
| 4 | p has two points object with different x component |
| 5 | p has three or more point object with different y component |
| 6 | p has three or more point object with same y component |
| 7 | p has three or more point object with all same x component |
| 8 | p has three or more point object with all different x component |
| 9 | p has three or more point object with some same and some different x component |
| 10 | p has three or more point object with some same and some different y component |
| 11 | p has three or more point object with all different y component |
| 12 | p has three or more point object with all same y component |

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
