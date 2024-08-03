# CODSOFT
TASK1
import java.util.Scanner;

 class NumberGuessingGame {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int lowerBound = 1;
        int upperBound = 100;
        int maxAttempts = 5;
        int score = 0;
        char playAgain = 'y';

        while (playAgain == 'y'){
            System.out.println("Welcome to the Number Guessing Game!");

            int secretNumber = generateNumber(lowerBound, upperBound);
            boolean win = playRound(scanner, secretNumber, maxAttempts);

            if (win) {
                score++;
            }

            System.out.println("Play again? (y/n): ");
            playAgain = scanner.next().charAt(0);
        }

        System.out.println("Thank you for playing! Your final score is: " + score);
        scanner.close();
    }

    public static int generateNumber(int lowerBound, int upperBound) {
        return (int) (Math.random() * (upperBound - lowerBound + 1)) + lowerBound;
    }

    public static boolean playRound(Scanner scanner, int secretNumber, int maxAttempts) {
        for (int attempts = 0; attempts < maxAttempts; attempts++) {
            System.out.println("Enter your guess (attempts remaining: " + (maxAttempts - attempts) + "): ");
            int guess = scanner.nextInt();

            if (guess == secretNumber) {
                System.out.println("Congratulations! You guessed the number in " + (attempts + 1) + " attempts.");
                return true;
            } else if (guess < secretNumber) {
                System.out.println("Too low, try again.");
            } else {
                System.out.println("Too high, try again.");
            }
        }

        System.out.println("Sorry, you ran out of attempts. The number was " + secretNumber + ".");
        return false;
    }
}
