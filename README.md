# PRODIGY_AD_03
Stopwatch app
import java.util.Scanner;

public class StopwatchApp {
    private static final long MILLISECONDS_IN_MINUTE = 60000;
    private static final long MILLISECONDS_IN_SECOND = 1000;

    private static long startTime = 0;
    private static long pauseTime = 0;
    private static boolean isRunning = false;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            displayMenu();
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    startTimer();
                    break;
                case 2:
                    pauseTimer();
                    break;
                case 3:
                    resetTimer();
                    break;
                case 4:
                    System.out.println("Exiting the stopwatch app. Goodbye!");
                    scanner.close();
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }

    private static void displayMenu() {
        System.out.println("\n==== Stopwatch Menu ====");
        System.out.println("1. Start");
        System.out.println("2. Pause");
        System.out.println("3. Reset");
        System.out.println("4. Exit");
        System.out.print("Enter your choice: ");
    }

    private static void startTimer() {
        if (!isRunning) {
            startTime = System.currentTimeMillis();
            isRunning = true;
            System.out.println("Stopwatch started.");
        } else {
            System.out.println("Stopwatch is already running.");
        }
    }

    private static void pauseTimer() {
        if (isRunning) {
            pauseTime += System.currentTimeMillis() - startTime;
            isRunning = false;
            System.out.println("Stopwatch paused.");
        } else {
            System.out.println("Stopwatch is not running.");
        }
    }

    private static void resetTimer() {
        startTime = 0;
        pauseTime = 0;
        isRunning = false;
        System.out.println("Stopwatch reset.");
    }

    private static String formatTime(long milliseconds) {
        long minutes = milliseconds / MILLISECONDS_IN_MINUTE;
        long seconds = (milliseconds % MILLISECONDS_IN_MINUTE) / MILLISECONDS_IN_SECOND;
        long millis = milliseconds % MILLISECONDS_IN_SECOND;
        return String.format("%02d:%02d:%03d", minutes, seconds, millis);
    }
}
