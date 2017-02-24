
Recursion

	Problem 1
	
		Consider the following algorithm:
			1. input n
			2. print n
			3. if n = 1 then STOP
			4. if n is odd then n  = 3n + 1
			5. else n  = n/2
			6. GOTO 2
			
		Given the input 22, the following sequence of numbers will be printed
			22 11 34 17 52 26 13 40 20 10 5 16 8 4 2 1
		Given an input n, determine the number of numbers printed before (and including) the 1 is
		printed. For a given n this is called the cycle-length of n. In the example above, the cycle
		length of 22 is 16.
		For any two numbers i and j you are to determine the maximum cycle length over all numbers
		between and including i and j.
		
		Solution:
		
		def recurse(n):
			if n == 1:
				return 1
			return recurse(3*n+1 if n%2 else n/2) + 1
			
		# The above function will calculate the cycle-length for n. So simply calling the function for numbers 
		# in range i to j and finding the maximum will give the solution

	Problem 2
	
		Given a string of N characters, write a function to print all permutations of length N. All characters are unique.
		example: abc
				 abc, acb, bac, bca, cab, cba
	
		Solution:	
	
		def permute(str, start, end): # String, Starting index of the string and Ending index of the string
		
			if start==end:			  # base case
				print toString(str)
			else:
				for i in xrange(start,end+1):
					str[start], str[i] = str[i], str[start]		# swap
					permute(str, start+1, end)					# recurse
					str[start], str[i] = str[i], str[start] 	# backtrack

Greedy

	Problem 1
	
		Given some amount of money M, you want to buy the most number of items from a store. Each item
		you buy must be different. You are given an array of N positive integers, each representing the
		cost of N different items.
		example: M = 6, item costs = [9, 5, 3, 4, 1, 2]
				 The maximum number of items you can buy with the given M is 3. 
				 
		Solution:
		
		sort(item_cost);       # sorting in ascending order
		for i = 0; i < N; i++  # N is the number of elements in item_cost array
		{
			CostSoFar += A[i]
			if(CostSoFar > T)
				break
			numberOfThings++
		}

					
Dynamic Programming

	Problem 1
	
		Given an integer N, write a function which calculates the Nth fibonacci number.
		The Nth number in the Fibonacci series is the sum of the two preceding numbers. 
		The 0th Fibonacci number is 0 and the 1st Fibonacci number is 1. 
		0, 1, 1, 2, 3, 5, 8, 13, 21 etc
		
		Solution:

		def fib(N):
			a, b = 0, 1
			i = 1
			while(i <= N):
			   i = i+1
			   a, b = b, a+b
			print b
			
	Problem 2
		
		Given an array of n integers, output the maximum sum found in any contiguous subarray of the input
		example: 31, -41, 59, 26, -53, 58, 97, -93, -23, 84
				 The maximum sum would be 187, for the subarray [2..6] (59+26-53+58+97)
		The numbers can be positive and negative.
		
		Solution:
		
		Assuming we have solved the problem for x[0..i-1], we can extend it to include x[i]
		maximum-sum subarray ending at x[i] is either in the first i-1 elements or it ends in
		position i
		
		MaxSoFar = 0
		MaxEndingHere = 0
		for i = [0, n)
			MaxEndingHere = max(MaxEndingHere + x[i], 0)
			MaxSoFar = max(MaxSoFar, MaxEndingHere)
			
	
