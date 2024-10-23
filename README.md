# Dice
This is a dice stimulater i made.
import java.util.Scanner;
import java.util.Random;
import java.util.Arrays;

public class MyProgram {
    public static void main(String[] args) {
        int numFaces = getIntFromUser("Enter the number of faces on the dice (greater than 0): ");
        int numDice = getIntFromUser("Enter the number of dice to roll (greater than 0): ");
        int target = getIntFromUser("Enter a target number: ");

        int[] rolls = rollDice(numDice, numFaces);
        System.out.println("You rolled: " + Arrays.toString(rolls));

        int total = calculateSum(rolls);
        System.out.println("TOTAL: " + total);

        checkTarget(total, target);
    }

    // Function to get a valid integer from the user
    static int getIntFromUser(String prompt) {
        Scanner scanner = new Scanner(System.in);
        int value;

        while (true) {
            System.out.print(prompt);
            value = Integer.parseInt(scanner.nextLine());
            if (value > 0) {
                break;
            } else {
                System.out.println("Please enter a valid integer greater than 0.");
            }
        }

        return value;
    }

    // Function to roll the dice and return an array of results
    static int[] rollDice(int numDice, int numFaces) {
        Random random = new Random();
        int[] rolls = new int[numDice];

        for (int i = 0; i < numDice; i++) {
            rolls[i] = random.nextInt(numFaces) + 1; // Generate number between 1 and numFaces
        }

        return rolls;
    }

    // Function to calculate the sum of an array of rolls
    static int calculateSum(int[] rolls) {
        int sum = 0;
        for (int roll : rolls) {
            sum += roll;
        }
        return sum;
    }

    // Function to check if the total meets the target
    static void checkTarget(int total, int target) {
        if (total >= target + 10) {
            System.out.println("CRITICAL SUCCESS!");
        } else if (total >= target) {
            System.out.println("SUCCESS!");
        } else if (total < target - 10) {
            System.out.println("CRITICAL FAILURE.");
        } else {
            System.out.println("FAILURE.");
        }
    }
}   
