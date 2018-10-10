// Problem 1

public class Problem1Sort
{
	public static void main(String[] args)
	{
		Problem1Sort test = new Problem1Sort();
		int[]arr = {-12, 45, -231};
		int hi []; 
		hi = test.sort(arr);
		for ( int d = 0; d<hi.length; d++)
		{
			System.out.println(hi[d]);
        }
    }
public int[] sort(int array1[])
{
		int big = 0;
		int size = array1.length;
		int check;
		int current;

		for(int i = 0; i <size; i++)
		{
			current = array1[i];
			check = String.valueOf(current).length();
			
			if(check > big)
			{
				big = check;
			}
		}
		for(int j = 1; j < big +1; j++)
		{
			for (int b = 0; b < array1.length - 1; b++)	
			{
				int index = b;
				for (int k = b + 1; k < array1.length; k++)	
					if((int)(array1[ k ]%Math.pow(10,j)/10) < ((int)array1[index]%Math.pow(10,j)/10) ) {
						index = k;
						
			int smallerNumber = array1[index];
			array1[index] = array1[b];
			array1[b] = smallerNumber;
        }
        
    }
    
    }

	 return array1;
}
}

// Problem 2
class mergeSort

	{

	void merge(int arr[], int l, int m, int r)

	{

	// Find sizes of two subarrays to be merged

	int n1 = m - l + 1;

	int n2 = r - m;

	/* Create arrays */

	int L[] = new int [n1];

	int R[] = new int [n2];

	/*Copy data to arrays*/

	for (int i=0; i<n1; ++i)

	L[i] = arr[l + i];

	for (int j=0; j<n2; ++j)

	R[j] = arr[m + 1+ j];

	/* Merge the arrays */

	// Initial indexes of first and second subarrays

	int i = 0, j = 0;

	// Initial index of merged subarray array

	int k = l;

	while (i < n1 && j < n2)

	{

	if (L[i] <= R[j])

	{

	arr[k] = L[i];

	i++;

	}

	else

	{

	arr[k] = R[j];

	j++;

	}

	k++;

	}

	/* Copy remaining elements of L[] if any */

	while (i < n1)

	{

	arr[k] = L[i];

	i++;

	k++;

	}

	/* Copy remaining elements of R[] if any */

	while (j < n2)

	{

	arr[k] = R[j];

	j++;

	k++;

	}

	}

	void sort(int arr[], int l, int r)

	{

	if (l < r)

	{

	// Find the middle point

	int m = (l+r)/2;

	// Sort first and second halves

	sort(arr, l, m);

	sort(arr , m+1, r);

	// Merge the sorted halves

	merge(arr, l, m, r);

	}

	}

	static void printArray(int arr[])

	{

	int n = arr.length;

	for (int i=0; i<n; ++i)

	System.out.print(arr[i] + " ");

	System.out.println();

	}

	public static void main(String args[])

	{

	int arr[] = {10, 13, 11, 9, 8, 14, 20};

	System.out.println("Given Array");

	printArray(arr);

	mergeSort ob = new mergeSort();

	ob.sort(arr, 0, arr.length-1);

	System.out.println("\nSorted array");

	printArray(arr);

	}

	}

// Problem 3
import java.util.NoSuchElementException;

class Node<T> {   // Node class has a generic type parameter T
		T data;
		Node<T> next;
		public Node(T data, Node<T> next) { // constructor name does NOT have a <T> next to it
			this.data = data;
			this.next = next;
		}

		public String toString() {
			return data.toString();
		}
	}

	public class LinkedList<T> {
		Node<T> front;
		int size;
		
		public LinkedList() {  // empty linked list to start with
			front = null;
			size = 0;
		}
		
		public void addFront(T item) {
			front = new Node<T>(item, front);
			size++;
		}

		public void deleteFront() 
		throws NoSuchElementException {
			if (front == null) {
				throw new NoSuchElementException();
			}
			front = front.next;
			size--;
		}

		public boolean search(T target) {
			for (Node<T> ptr=front; ptr != null; ptr=ptr.next) {
				if (target.equals(ptr.data)) {
					return true;
				}
			}
			return false;
		}
		
		// while loop version, stylized single-line output
		public void traverse() {
			if (front == null) {
				System.out.println("Empty list");
				return;
			}
			System.out.print(front.data);  // first item
			Node<T> ptr=front.next;    // prepare to loop starting with second item
			while (ptr != null) {
				System.out.print(" --> " + ptr.data);
				ptr = ptr.next;
			}
			System.out.println();
		}
		
		public int getSize() {
			return size;
		}
		
		public boolean isEmpty() {
			return size == 0;
		}
		
		public static void main(String[] args) {
			LinkedList<Integer> intll = new LinkedList<>();
			int x=5;
			intll.addFront(x);  // auto boxes value of x into an Integer object
			intll.addFront(new Integer(15));
			intll.addFront(-10);  // auto boxes -10 into an Integer object
			intll.traverse();
			intll.deleteFront();
			intll.traverse();
			intll.deleteFront();
			intll.traverse();
			intll.deleteFront();
			intll.traverse();
			intll.deleteFront(); // trying to delete from an empty list
		}

	public void add(int a)
	{
		list.add(a);
	}
	public void printList()
	{
		System.out.println(list);
	}
	public void quickSort()
	{
		if(head==null || head.next==null)
			return;	
		head=shuffle(head);
		System.out.print("unsorted shuffled list: ");
		printList(head);
	
		Node pivot;
		if(getSize(head)>3) 
			pivot=medianOf3(head);	//calls helper method to find median value and makes that the pivot
		else 
			pivot=head;
		
		head=recur_sort(head, pivot);
		System.out.print("sorted list: ");
		printList(head);
	}
	private static Node shuffle(Node head) {
		int rand = (int) ((Math.random()*size));
		Node ptr = head;
		for(int i = 0;i<rand;i++ ) {
			ptr = ptr.next;
		}
		Node second = head;
		if(ptr.next != null)
			head = ptr.next;
		ptr.next= head.next;
		head.next=second;
		return head;
	}
	private static Node getTailNode(Node head) {
		Node ptr=head;
		while(ptr.next!=null) {
			ptr=ptr.next;
		}
		return ptr;
	}
	private static Node medianOf3(Node head) {
		/*System.out.println(size);
		if(size<3) {
			return head;
		}*/
		Node first=head;
		Node last= getTailNode(head);
		
		Node ptr=head;
		int mid=size/2;
		while(mid>0) {
			ptr=ptr.next;
			mid--;
		}
		if((ptr.value>=first.value && ptr.value<=last.value) || (ptr.value>=last.value && ptr.value<=first.value)) {
			return ptr;
		}
		else if((first.value>=ptr.value && first.value<= last.value) || (first.value>=last.value && first.value<= ptr.value)) {
			return first;
		}
		else
			return last;
		
	}
	
	private static int getSize(Node head) {
		if(head==null)
			return 0;
		Node ptr=head;
		int size=0;
		while(ptr!=null) {
			size++;
			ptr=ptr.next;
		}
		return size;
	}
	
	private static Node recur_sort(Node head, Node pivot) {
		if(head==null || head.next==null)
			return head;	
//		Node pivot;
		/*
		if(getSize(head)>3) 
			pivot=medianOf3(head);
		else */
			pivot=head;
		//System.out.println(pivot.value);
		Node lo=null, hi = null;
	    Node temp = head.next;
        pivot.next = null;
        LinkedList sorted = new LinkedList();
        while(temp != null){
            Node second = temp.next;
            temp.next = null;
            if(temp.value < pivot.value) {
            	lo = sorted.addthisNode(temp, lo);
            //	sorted.printList(lo);
            }
            else {
            	hi = sorted.addthisNode(temp, hi);
            //	sorted.printList(hi);
            }
            temp = second;
        }
        
        lo = recur_sort(lo, lo);
        hi = recur_sort(hi, hi);
        
        Node tl = lo;
        
        while(tl != null && tl.next != null){
            tl = tl.next;
        }
        
        if(lo == null){
            pivot.next = hi;
            sorted.printList(head);
            return pivot;
        }
        else{
        	tl.next = pivot;
            pivot.next = hi;
           sorted.printList(head);
            return lo;

	}	
	}
}

// Problem 4
import java.lang.Object;
import java.util.Arrays;

public class ProblemSolving {

	public static void main(String[] args) {
		int[] a= {8, 9, 0, 3, 1};
		int arraySize=a.length;
		int[] output=ProblemSolving1(a, arraySize);
		printArr(output);
	}
	public static void printArr(int[] output) {
		System.out.print("[ ");
		for(int i=0; i<output.length; i++) {
			System.out.print(output[i] + " ");
		}
		System.out.println("]");
	}
	public static int[] ProblemSolving1(int[] a, int arraySize){
		Arrays.sort(a);
//		printArr(a);
		int[] minMax=new int[arraySize];
		int midIndex;
		boolean oddSize;
		if(arraySize%2==0) {
			oddSize=false;
			midIndex=arraySize/2;
		}
			
		else {
			oddSize=true;
			midIndex=(arraySize/2)+1;
		}
		
		int[] maxes=new int[arraySize-midIndex];
		int[] mins=new int[midIndex];
		
		int count=midIndex;
		for(int i=0; i<arraySize-midIndex; i++) {
			maxes[i]=a[count];
			count++;
		}
		for(int i=0; i<midIndex; i++) {
			mins[i]=a[i];
		}
		//printArr(maxes);
		//printArr(mins);
		int count2=0;
		for(int i=0; i< mins.length; i++) {
			minMax[count2]=mins[i];
			count2+=2;
		}
		int count3=1;
		for(int i=0; i< maxes.length; i++) {
			minMax[count3]=maxes[i];
			count3+=2;
		}
		
	return minMax;
	}
}
