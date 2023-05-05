Download Link: https://assignmentchef.com/product/solved-cse12-assignment-5-heaps-and-heapsort
<br>
In this assignment you create a heap (backed by an array, actually an ArrayList),  a JUnit framework to help you develop and validate your heap class, and a sorting algorithm that uses the heap (AKA heapsort)

Implementing Heap12, Heap12Tester and HeapSort12<strong> </strong><strong> </strong>

Read the Javadoc documentation of the supplied Heap12.java (you will need to generate the javadoc itself).  Make certain you understand the responsibilities of each public method defined. of each method required by the interface. Sketch a test plan for testing Heap12, which you will be coding completely for part of this assignment. Your plan should involve testing all the public methods defined in the Heap12 class, special cases, and the iterator.

Define a class named Heap12Tester that extends junit.framework.TestCase and that implements your test plan. Keep in mind that while you should definitely think about testing first, you do not need to write a complete tester program before starting to define Heap12. In fact, an iterative process can work well: define some tests in Heap12Tester, and implement the functionality in Heap12 that will be tested by those tests, test that functionality with

Heap12Tester, write more tests, etc. The end result will (hopefully!) be the same: A good tester, and a good implementation of the class being tested.

You <strong>might want to begin defining Heap12Tester by first testing the Java Collections Framework PriorityQueue</strong> class. That way you can develop some tests that you know work on a PriorityQueue because it also extends AbstractQueue.  Please note that if you take this approach to start, that you only need to be writing tests for methods that are defined both for Heap12 and PriorityQueue. Heap12 has many fewer public methods than PriorityQueue.

Also keep in mind that your Heap12Tester must not make use of any Heap12 methods <em>not</em> specified in the Heap12 documentation. This is because we will validate your Heap12Tester on a known good implementation of Heap12.

<strong>Heap12.java </strong>

Define a generic class Heap12&lt;E extends Comparable&lt;? super E&gt;&gt;.  Your Heap12 must properly implement all the public methods defined in the javadoc you generate from the Heap12 starter code.  In addition, your Heap12 must meet these requirements:

<ol>

 <li>Heap12 <strong>must extend the AbstractQueue</strong> class of the Java Collections Framework</li>

</ol>

(<strong>You CANNOT, for example  adapt the already-existing PriorityQueue</strong>)

<ol start="2">

 <li>Heap12 <strong>must use a heap-structured array as its backing store</strong>. (For simplicity use an ArrayList object wherever your assignment simply says “array”. In what follows, when it says array, we really mean ArrayList and array as interchangeable)</li>

 <li>Heap12 must define a <strong>public default constructor which creates an array of length 5 </strong>as its initial backing store.</li>

 <li>Heap12 must define a copy constructor, which takes another Heap12 as an argument, and then initializes the new Heap12 to be a “deep copy” of the argument Heap12. Here “deep copy” means that the new Heap12 and the argument Heap12 will have different backing store arrays, but the data objects pointed to by elements of those arrays will not be copied. (only the references to the objects are copied)</li>

 <li>When the offer() method is called with a non-null argument and the current size of the Heap12 is equal to the length of its backing store array, <strong>the length of its backing store array must double.</strong> (That is, a new array with length twice that of the existing full array must be allocated, elements from the old array copied into it, and the new array then used as the backing store. While ArrayLists will extend automatically, you should explicitly perform a copy) Thus a Heap12 object appears to a client as a priority queue with unlimited capacity.</li>

</ol>

<em>Some suggestions for Heap12 implementation.  </em>

Think about what other methods it might be useful to define in order to implement the required public methods. Since these other methods are not part of the public interface of your Heap12 class, they should have private or protected visibility. For example, methods like:

private void trickleDown(int indx)    private void bubbleUp(int indx)  parent(int indx)

are just a few that are likely convenient helper methods. You almost certainly will want others.  Helper methods are defined to make your code more readable, easier to understand, and reduce “cut-and-paste” code replication.  We are particularly interested in reducing code replication.  Define as many private helper methods as you deem appropriate. You cannot define any public methods other than those specified in the Javadoc/Interface definitions

As you get a little deeper into your implementation, you likely will find it useful to define

<strong>‘trickledown’ and ‘bubbleup’ heap operations so that they can start from any element in the array not just the first or last</strong>. These methods can be defined recursively, or iteratively.

(An additional hint: think about a helper method  that is a wrapper around “compareTo” to reduce the amount of code needed to differentiate between a min-heap and a  max-heap — A good approach is to<em> first write and test a min-heap  implementation</em>.  Then think about how comparisons would need to change to turn this code into a max-heap.   This is where a simple wrapper around compareTo can be useful.  If you approach this correctly, you should only need slightly recode existing comparisons in your bubbleUp() and trickleDown() methods to use a comparison helper method

<strong>Heap12Tester.java</strong>

We are NOT supplying you with any starting code for Heap12Tester.java, but you are required to supply this JUnit-based tester as part of your solution.  We will run your Heap12Tester against a known, good, implementation. Your Tester should help you with the implementation of the Heap12 class, you certainly will want to test all the public methods, your iterator, and places where exceptions should be thrown.    We would expect that <em>at least</em> 10 meaningful tests would indicate a baseline of reasonable coverage.  (You probably need a few more tests for so-called edge conditions).  In the iterative approach to testing/development, when you find a bug in your implementation that your tests did not uncover, write another test that would find that bug.

Some ideas on testing

<ul>

 <li><strong>Don’t forget that your code should support both min-heaps and max-heaps,</strong> you will eventually want test fixtures for both min-heaps and max-heaps (see note above about first developing a min-heap only implementation and then extending that to support both min-heaps and max-heaps)</li>

 <li>Don’t overlook the remove() method of the Iterator interface. This supports the “strange” operation of removing an element that is possibly in the middle of the heap.</li>

 <li>While it’s convenient to test with elements offered to the heap in sorted order, try some test cases where the data isn’t presorted, and then verify that you retrieve the proper min (or max) value.</li>

 <li>It’s helpful to define your iterator to simply return elements in index order, you can print these out in a loop and verify visually that your internal array IS heap-ordered</li>

</ul>

<strong>HeapSort12.java </strong>

Using your PR4 as a guide. Implement HeapSort12.java using your Heap12 class. This should be fewer  than 20  additional lines of code and must implement the Sort12 interface.  If your HeapSort is long and complex, you are not using your Heap12 class appropriately   You can test your HeapSort12.java correctness using SortTimer2 with the “-p” option.

<strong>Testing Heap Sort </strong>

The supplied timing code SortTimer2.java is a modification of SortTimer  from PR4. It now includes the option to call HeapSort12 as algorithm 4. The modification that enables you to sort a text file and print the results with the -p option is still present. The -p option will print  for each iteration, so you likely want to use for a single iteration, and a single timing repetition.

For example, sort the first 100 words of the file random-strings.txt using heap sort and print the resulting sorted list,, you would type in

% java SortTimer2 -p random-strings.txt 4 100 1 1 1

This will use sort algorithm “4”, sort the first 100 strings, extend each test by 1, do just 1 test, and 1 rep/iteration.   For SortTimer2, algorithm 4 is heap sort.   You can use this to verify that your heap sort is sorting properly. By redirecting the output to a file and verifying that the result is properly sorted (We WILL test that your implemented heap sort actually sorts correctly).





