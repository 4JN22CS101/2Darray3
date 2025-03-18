# 2Darray3
1. Return the Elements of the matrix in spiral order .
   -->package array;

import java.util.Scanner;

public class spiralMatrix {
	static void PrintMatrix(int[][] matrix) {
		for(int i=0;i<matrix.length;i++) {
			for(int j=0;j<matrix[i].length;j++) {
				System.out.print(matrix[i][j]+" ");
			}
			System.out.println();
		}
	}
	static void printSpiralOrder(int[][] matrix, int r, int c) {
		int topRow = 0, bottomRow = r-1, leftCol=0,rightCol=c-1;
		int totalElements=0;
		
		while(totalElements < r*c) {
			for(int j=leftCol;j<=rightCol && totalElements < r*c;j++) {
				System.out.print(matrix[topRow][j]+" ");
				totalElements++;
			}
			topRow++;
			for(int i=topRow; i<=bottomRow && totalElements < r*c;i++) {
				System.out.print(matrix[i][rightCol]+" ");
				totalElements++;
			}
			rightCol--;
			for(int k=rightCol;k>=leftCol && totalElements < r*c;k--) {
				System.out.print(matrix[bottomRow][k]+" ");
				totalElements++;
			}
			bottomRow--;
			for(int l=bottomRow;l>=topRow && totalElements < r*c;l--) {
				System.out.print(matrix[l][leftCol]+" ");
				totalElements++;
			}
			leftCol++;
		}
	}
	public static void main(String[] args) {
		Scanner sc=new Scanner(System.in);
		System.out.println("Enter the number of Rows and Columns");
		int r=sc.nextInt();
		int c=sc.nextInt();
		int[][] matrix=new int[r][c];
		int total=r*c;
		System.out.println("Enter "+total+" values");
		for(int i=0;i<r;i++) {
			for(int j=0;j<c;j++) {
				matrix[i][j]=sc.nextInt();
			}
		}
		System.out.println("Entered matrix is");
		PrintMatrix(matrix);
		
		System.out.println("Spiral order matrix: ");
		printSpiralOrder(matrix,r,c);
	}
}
Enter the number of Rows and Columns
4
4
Enter 16 values
1 2 3 4
5
6 7 8
9 1 2 3
4 5 6 7
Entered matrix is
1 2 3 4 
5 6 7 8 
9 1 2 3 
4 5 6 7 
Spiral order matrix: 
1 2 3 4 8 3 7 6 5 4 9 5 6 7 2 1 


2. For A given positive integer n , generate a n*n matrix , by filling elements upto n*n in spiral order.
   -> package array;
import java.util.Scanner;

public class GenerateSpiralMatrix {
	static void PrintMatrix(int[][] matrix) {
		for(int i=0;i<matrix.length;i++) {
			for(int j=0;j<matrix[i].length;j++) {
				System.out.print(matrix[i][j]+" ");
			}
			System.out.println();
		}
}
	static int[][] GenerateSpiralMatrix(int n) {
		int leftCol = 0, rightCol=n-1, topRow=0, bottomRow=n-1;
		int[][] SpiralMatrix = new int[n][n];
		int elementCount=1;
		while(elementCount <= n*n) {
			for(int i=leftCol;i<=rightCol && elementCount <= n*n;i++) {
				SpiralMatrix[topRow][i]=elementCount++;
			}
			topRow++;
		
		for(int j=topRow;j<=bottomRow && elementCount <= n*n;j++) {
			SpiralMatrix[j][rightCol]=elementCount++;
		}
		rightCol--;	
		
		for(int k=rightCol;k>=leftCol && elementCount <= n*n;k--) {
			SpiralMatrix[bottomRow][k]=elementCount++;
		}
		bottomRow--;
		for(int l=bottomRow;l>=topRow && elementCount <= n*n;l--) {
			SpiralMatrix[l][leftCol]=elementCount++;
		}
		leftCol++;	
	}
		return SpiralMatrix;
}
public static void main(String[] args) {	
	Scanner sc = new Scanner(System.in);
	System.out.println("Enter the Value of n: ");
	int n = sc.nextInt();
	int[][] result=GenerateSpiralMatrix(n);
	PrintMatrix(result);
	sc.close();
}
}

Enter the Value of n: 
4
1 2 3 4 
12 13 14 5 
11 16 15 6 
10 9 8 7 
