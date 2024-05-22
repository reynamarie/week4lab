# CSE15L Lab Report 3
## Part 1- Bugs



1. Failure-inducing: JUNIT Test and Original Associated Code
   
~~~
   public class ArrayExamples {
       static void reverseInPlace(int[] arr) {
           for(int i = 0; i < arr.length; i += 1) {
               arr[i] = arr[arr.length - i - 1];
         }
      }
   }

   // JUnit Test
   @Test 
   public void testReverseInPlace() {
       int[] input1 = { 1, 2, 3 };
       ArrayExamples.reverseInPlace(input1);
       Assert.assertArrayEquals(new int[]{ 3, 2, 1 }, input1);
   }
~~~



2. Non failure-inducing JUNIT Test and Original Associated Code.

These tests are both on failure-inducing JUNIT Test. At this point in the steps, the `reverseInPlace` method in `ArrayExamples` is producing one of the tests to fail and one of these tests to pass.
~~~
public class ArrayTests {
  @Test
	public void testReverseInPlace() {
    int[] input1 = { 1, 2, 3};
    ArrayExamples.reverseInPlace(input1);
    Assert.assertArrayEquals(new int[]{ 3, 2, 1 }, input1);

	}

  @Test
	public void testReverseInPlace2() {
    int[] input1 = { 1};
    ArrayExamples.reverseInPlace(input1);
    Assert.assertArrayEquals(new int[]{ 1 }, input1);

	}
~~~


3.
![Image](onefailonepass.jpg)





This code runs the two tests, one of them fails and one of them passes. The one that fails is the `testReverseInPlace`. The test that passes is the `testReverseInPlace2`. It passes because there is only one element in the array, so there aren't any numbers to incorrectly sort by. 


4.
Before-and-after code changes are required to fix it, by correctly swapping
 Before

~~~

    public class ArrayExamples {
      static void reverseInPlace(int[] arr) {
        for(int i = 0; i < arr.length; i += 1) {
          arr[i] = arr[arr.length - i - 1];
        }
    }
}
~~~



After
~~~
         public class ArrayExamples {
            public static void reverseInPlace(int[] array) {
                for (int i = 0; i < array.length / 2; i++) {
                    int temp = array[i];
                    array[i] = array[array.length - 1 - i];
                    array[array.length - 1 - i] = temp;
                }
            }
    }
~~~





5. Why the fix addresses the issue?
The issue with the code that caused the fail-inducing test was that it was swapping the element in the array with the entire array. In other words, it was undoing the swapping that it was doing, causing the array to remain the same. The after code addresses the issue because it correctly reverses the array in place, which is the purpose of the method. It correctly implements the `reverseInPlace` method by swapping each element with its corresponding element from the end of the array. 










## Part 2- Researching Commands 
Choice of command: `grep` 

`grep -c`
![Image](thegrep.jpg)

- This  command finds the frequency of the patterns and or words in a file by printing the count of lines that match.






`grep -h` 

![Image](yasqueen.jpg)
![Image](yasqueen2.jpg)

- This command is used to display the matched lines in a file. It is useful for focusing on the content in a file. 



`grep -n`
![Image](alqaeda.jpg)
- This  command searches for a specific pattern and then prints the matching line number. It is useful for locating contents in a file. 


`grep -l`
![Image](sunshine.jpg)
- This command prints the filenames which contain the given contents. It is useful for locating which files contain such patterns and or content. 
  



Source for obtaining `grep` commands: geeksforgeeks.org

- Title Page: grep command in Unix/Linux
 
- Link: https://www.geeksforgeeks.org/grep-command-in-unixlinux/
