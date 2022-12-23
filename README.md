# Marvolo-Gaunt-Ring
Sample Input 0

5 1 2 -3
-1 -2 -3 -4 -5

Sample Output 0

12

Explanation

Selecting i = j = 1 and k = 5 gives the answer 
12
.

Example
Input
5 1 2 -3
-1 -2 -3 -4 -5
Output
12


//Java

/* package codechef; // don't place package name! */
import java.util.*;
import java.lang.*;
import java.io.*;

/* Name of the class has to be "Main" only if the class is public. */
public class Main
{
    public static void main (String[] args) throws java.lang.Exception
    {
        // your code goes here
		Scanner in = new Scanner(System.in);
		//p*a(i)+q*a(j)+r*a(k)
		int n = in.nextInt();
		long[] arr= new long[n];
		
		long p = in.nextInt();
		long q = in.nextInt();
		long r = in.nextInt();
		
		for(int i = 0;i < n;i++){
			arr[i] = in.nextInt();
		}
		
		long[] pmax= new long[n];
		pmax[0] = p * arr[0];
		
		for(int i = 1;i < n; i++){
			
			pmax[i] = Math.max(pmax[i-1] , (p * arr[i]));
				
		}
		
		long[] smax = new long[n];
		smax[n-1] = r * arr[n-1];
		
		for(int i = n-2;i >= 0;i--){
			
			smax[i] = Math.max(smax[i+1] , (r * arr[i]));
			
		}
		
		long ans = Long.MIN_VALUE;
		for(int i = 0;i < n; i++){
			ans = Math.max(ans , (pmax[i] + (q*arr[i]) + smax[i]));
		}
		System.out.println(ans);
    }
}
