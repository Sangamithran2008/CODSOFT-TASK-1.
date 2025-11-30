import java.util.Random;
import java.util.Scanner;

public class NumberGame {
    
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        Random rand = new Random();

        int score = 0; // Score based on rounds won
        char playAgain;

        System.out.println("===== NUMBER GUESSING GAME =====");

        do {
            int number = rand.nextInt(100) + 1; // Random number 1–100
            int attempts = 0;
            int maxAttempts = 7;
            boolean guessed = false;

            System.out.println("\nI have selected a number between 1 and 100.");
            System.out.println("You have " + maxAttempts + " attempts to guess it!");

            while (attempts < maxAttempts) {
                System.out.print("Enter your guess: ");
                int guess = sc.nextInt();
                attempts++;

                if (guess < number) {
                    System.out.println("Too low!");
                } else if (guess > number) {
                    System.out.println("Too high!");
                } else {
                    System.out.println("🎉 Correct! You guessed it in " + attempts + " attempts!");
                    guessed = true;
                    score++;
                    break;
                }
            }

            if (!guessed) {
                System.out.println("❌ Out of attempts! The correct number was: " + number);
            }

            System.out.println("Your current score (rounds won): " + score);

            System.out.print("\nDo you want to play again? (y/n): ");
            playAgain = sc.next().charAt(0);

        } while (playAgain == 'y' || playAgain == 'Y');

        System.out.println("\nThanks for playing! Your final score is: " + score);
        sc.close();
    }
}
