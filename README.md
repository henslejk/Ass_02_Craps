import java.util.Scanner;
import java.util.Random;
public class Ass_02_Craps {

    public static void main (String[]args){

        Scanner input = new Scanner(System.in);
        Random rnd = new Random();

        boolean playAgain = true;

        while (playAgain) {

            // Roll the two dice
            int die1 = rnd.nextInt(6) + 1;
            int die2 = rnd.nextInt(6) + 1;
            int sum = die1 + die2;
            int point = sum;
            boolean gameOver = false;


            IO.println("\n Craps Game ");
            IO.println("Die 1: " + die1);
            IO.println("Die 2: " + die2);
            IO.println("Sum: " + sum);

            // Check roll
            if (sum == 2 || sum == 3 || sum == 12) {

                IO.println("Craps! You lost.");

            } else if (sum == 7 || sum == 11) {

                IO.println("Natural! You won.");

            } else {


                IO.println("The point is " + point + ".");
                IO.println("Trying for point...");

                // Rolling until the player wins or loses
                while (!gameOver) {

                    die1 = rnd.nextInt(6) + 1;
                    die2 = rnd.nextInt(6) + 1;
                    sum = die1 + die2;

                    IO.println("\nDie 1: " + die1);
                    IO.println("Die 2: " + die2);
                    IO.println("Sum: " + sum);

                    if (sum == point) {

                        IO.println("Made point and won!");
                        gameOver = true;

                    } else if (sum == 7) {

                        IO.println("Got a seven and lost.");
                        gameOver = true;

                    } else {

                        IO.println("Trying for point...");
                    }
                }
            }


            IO.print("\nDo you want to play again? (Y/N): ");
            String answer = input.nextLine().trim();

            while (!answer.equalsIgnoreCase("Y")
                    && !answer.equalsIgnoreCase("N")) {

                IO.print("Please enter Y or N: ");
                answer = input.nextLine().trim();
            }

            if (answer.equalsIgnoreCase("N")) {
                playAgain = false;
            }
        }

        IO.println("\nThanks for playing!");
        input.close();
    }
}
