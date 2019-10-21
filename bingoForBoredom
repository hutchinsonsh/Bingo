package bingoforboredom;
import java.util.Random;
import java.util.ArrayList;
import javax.swing.JOptionPane;

public class BingoForBoredom 
{
    public static void main(String[] args) 
    {
        int [][] one = createMatrix();
        int [][] two = createMatrix();
        ArrayList cards = new ArrayList();
        boolean gameWon = false;
        int num = 0;
        int iteration = 0;
        
        printOutMatrixOne(one, two);
        String input = JOptionPane.showInputDialog(null, "Draw a card? Y/N?");
        
        while (gameWon == false)
        {
            iteration += 1;
            int cardDrawn = drawCard(cards);
            cards.add(cardDrawn);
            System.out.println("The card draws was: " + cardDrawn);
            checkMatrix(one, two, cardDrawn);
            num = isGameOver(one, two);
            if (num == 1)
                gameWon = true;
            if (num == 2)
                gameWon = true;
            
        input = JOptionPane.showInputDialog(null, "Draw a card? Y/N?");
        }
        if (num == 1)
        {
            System.out.println("You may have won the game but computers are "
                        + "still smarter than you");
            printOutMatrixTwo(one);
        }
        if (num == 2)
        {
            System.out.println("The computers are already winning");
            printOutMatrixTwo(two);
        }
        
    }
    
    // first iteraion, creates a matrix for the computer and user
    public static int[][] createMatrix()
    {
        ArrayList usedNum = new ArrayList();
        int[][] one = new int [5][5]; 
        int limit = 10;
        int min = 1;
        for(int i = 0; i < 5; i++)
        {
            for(int j = 0; j < 5; j++)
            {
                boolean checkUsedNums = true;
                while (checkUsedNums)
                {
                    Random rand = new Random();
                    int  n = rand.nextInt(limit-min +1) + min;
                    if (usedNum.contains(n))
                        checkUsedNums = true;
                    else
                    {
                        one[j][i] = n;  
                        checkUsedNums = false;
                        usedNum.add(n);
                    }
                }
            }
            limit += 10;
            min += 10;
        }
        usedNum.clear();
        return one;
    }
    
    // prints out both the matrixs in the beginning
    public static void printOutMatrixOne(int[][] one, int[][] two)
    {
        System.out.println("Your BINGO board is:");
        System.out.println("B\tI\tN\tG\tO");
        for(int i = 0; i < 5; i++)
        {
            for(int j = 0; j < 5; j++)
            {
                System.out.print (one[i][j] + "\t");
            }
            System.out.println(); 
        }
        System.out.println();
        System.out.println("The Computer's BINGO board is:");
        System.out.println("B\tI\tN\tG\tO");
        for(int i = 0; i < 5; i++)
        {
            for(int j = 0; j < 5; j++)
            {
                System.out.print (two[i][j] + "\t");
            }
            System.out.println(); 
        }
    }
    
    // prints out whichever matrix made a match
    public static void printOutMatrixTwo(int[][] one)
    {
       System.out.println("B\tI\tN\tG\tO");
        for(int i = 0; i < 5; i++)
        {
            for(int j = 0; j < 5; j++)
            {
                System.out.print (one[i][j] + "\t");
            }
            System.out.println(); 
        }
        System.out.println(); 
    }

    // draws a card each time the while loop is iterated
    public static int drawCard(ArrayList cards)
    {
        int cardDrawn = 0;
        boolean alreadyDrawn = true;
        while (alreadyDrawn)
        {
            Random rand = new Random();
            int  n = rand.nextInt(50) + 1;
            if(cards.contains(n))
                alreadyDrawn = true;
            else
            {
                cardDrawn = n;
                alreadyDrawn = false;
            }
        }
        return cardDrawn;
    }
    
    // checks the matrix if the card drawn matches any of the numebrs
    public static void checkMatrix(int[][] one, int[][] two, int cardDrawn)
    {
        boolean oneRight = false;
        boolean twoWrongs = false;
        for(int i = 0; i < 5; i++)
        {
            for(int j = 0; j < 5; j++)
            {
                if(one[i][j] == cardDrawn)
                {
                    one[i][j] = 0;
                    oneRight = true;
                }
                if(two[i][j] == cardDrawn)
                {
                    two[i][j] = 0;
                    twoWrongs = true;
                }
            }
        }
        one = getUsersNewMatrix(one);
        two = getCompsNewMatrix(two);
        if (oneRight)
        {
            System.out.println("Congrats! You made a match");
            printOutMatrixTwo(one);
        }
        if (twoWrongs)
        {
            System.out.println("The computer made a match");
            printOutMatrixTwo(two);
        }
    }
    
    // gets matrix after 'checkMatrix' to make the changes stay
    public static int[][] getUsersNewMatrix(int[][]one)
    {
        return one;
    }
    
    // same as getUsersNewMatrix but for the computer
    public static int[][] getCompsNewMatrix(int[][]one)
    {
        return one;
    }
     
    // checks the rows to see it they are made up of 0's
    public static boolean checkRows(int[][] one)
    {
        boolean rowEqualsZero = false;
        for(int i = 0; i < 5; i++)
        {
            int row = 0;
            for(int j = 0; j < 5; j++)
            {
                row += one[i][j];
            }
            if (row == 0)
            rowEqualsZero = true;
        }
        return rowEqualsZero;
    }
     
    // checks the col to see if they are made up of 0's
    public static boolean checkColumns(int[][] one)
    {
        boolean colEqualsZero = false;
        for(int i = 0; i < 5; i++)
        {
            int col = 0;
            for(int j = 0; j < 5; j++)
            {
                col += one[j][i];
                
            }
            if (col == 0)
                colEqualsZero = true;
        }
        return colEqualsZero;
    }
     
    // checks the diagnal (top left to right bottom) for 0's
    public static boolean checkDiagonalOne(int[][] one)
    {
        boolean digEqualsZero = false;
        int dig = 0;
        for (int i = 4; i >= 0; i--)
        {
             dig += one[i][i];
        }
        if (dig == 0)
            digEqualsZero = true;
        return digEqualsZero;
    }
    
    // checks the diagonal (bottom left to top right) for 0's
    public static boolean checkDiagonalTwo(int[][] one)
    {
        boolean digEqualsZero = false;
        int dig = 0;
        for(int i = 0, j = 4; i < 5; i++, j--)
        {
            dig += one[i][j];    
        }
        if (dig == 0)
            digEqualsZero = true;
        return digEqualsZero;
    }
    
    // checks all the ways the game could be over and returns a num > 0 if true
    public static int isGameOver(int[][]one, int[][]two)
    {
        boolean gameOver = false;
        gameOver = checkRows(one);
        if(gameOver)
            return 1;
        gameOver = checkColumns(one);
        if(gameOver)
            return 1;
        gameOver = checkDiagonalOne(one);
        if(gameOver)
            return 1;
        gameOver = checkDiagonalTwo(one);
        if(gameOver)
            return 1;
        gameOver = checkRows(two);
        if(gameOver)
            return 2;
        gameOver = checkColumns(two);
        if(gameOver)
            return 2;
        gameOver = checkDiagonalOne(two);
        if(gameOver)
            return 2;
        gameOver = checkDiagonalOne(two);
        if(gameOver)
            return 2;
                
        return 0;
    }
}
