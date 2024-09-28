Problem Statement
In this assignment, you'll work on a simplified version of Shamir's Secret Sharing algorithm.

Consider an unknown polynomial of degree m. You would require m+1 roots of the polynomial to solve for the coefficients, represented as k = m + 1.
An unknown polynomial of degree m can be represented as:
f(x) = a_m x^m + a_{m-1} x^{m-1} + ... + a_1 x + c
Where:
f(x) is the polynomial function
m is the degree of the polynomial
a_m, a_{m-1}, ..., a_1, c are coefficients (real numbers)
a_m ≠ 0 (since it's the highest degree term, ensuring the polynomial is of degree m)
This representation shows that a polynomial of degree m is a sum of terms, where each term is a coefficient multiplied by a power of x. The highest power of x is m, and the powers decrease by 1 for each subsequent term until we reach the constant term c, which has no x.
The task is to find the constant term i.e, ‘c’ of the polynomial with the given roots. However, the points are not provided directly but in a specific format.
You need to read the input from the test cases provided in JSON format.

code: Java
import java.math.BigInteger;

public class Main {


	public static long bigInteger(String value, int base) {
		return new BigInteger(value, base).longValue();
	}


	public static double lagrangeInterpolation(int[] x, long[] y, int n) {
		double result = 0;

		for (int i = 0; i < n; i++) {
			double term = y[i];
			for (int j = 0; j < n; j++) {
				if (i != j) {
					term *= (0 - x[j]) / (double) (x[i] - x[j]);
				}
			}
			result += term;
		}

		return result;
	}

	public static void main(String[] args) {

		/*test case 1
		 int n1 = 4;
		 int k1 = 3;
		 int[] x1 = {1, 2, 3, 6};
		 long[] y1 = {
		     bigInteger("4", 10),
		     bigInteger("111", 2),
		     bigInteger("12", 10),
		     bigInteger("213", 4)  */

		//test case 2
		int n2 = 9;
		int k2 = 6;
		int x2[] = {1, 2, 3, 4, 5, 6, 7, 8, 9};
		long[] y2= {
			bigInteger("28735619723837", 10),
			bigInteger("1A228867F0CA", 16),
			bigInteger("32811A4AA0B7B", 12),
			bigInteger("917978721331A", 11),
			bigInteger("1A22886782E1", 16),
			bigInteger("28735619654702", 10),
			bigInteger("71AB5070CC4B", 14),
			bigInteger("122662581541670", 9),
			bigInteger("642121030037605", 8)
		};


		//double result1 = lagrangeInterpolation(x1, y1, n1);
		double result2 = lagrangeInterpolation(x2, y2, n2);

		//System.out.println("Interpolated result: " + result1);
		System.out.println("Interpolated result: " + result2);
	}
}
