import java.util.*;

public class OnlineExamSystem {
    private static Scanner scanner = new Scanner(System.in);
    private static boolean isLoggedIn = false;
    private static String username;
    private static String password;

    public static void main(String[] args) {
        showMenu();
    }

    private static void showMenu() {
        int choice;
        do {
            System.out.println("********** Online Exam System **********");
            System.out.println("1. Login");
            System.out.println("2. Update Password");
            System.out.println("3. Update Profile");
            System.out.println("4. Start Exam");
            System.out.println("5. Logout");
            System.out.println("6. Exit");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();
            scanner.nextLine(); 

            switch (choice) {
                case 1:
                    login();
                    break;
                case 2:
                    updatePassword();
                    break;
                case 3:
                    updateProfile();
                    break;
                case 4:
                    if (isLoggedIn) {
                        startExam();
                    } else {
                        System.out.println("Please login first!");
                    }
                    break;
                case 5:
                    if (isLoggedIn) {
                        logout();
                    } else {
                        System.out.println("You are not logged in!");
                    }
                    break;
                case 6:
                    System.out.println("Thank you for using the Online Exam System. Goodbye!");
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
                    break;
            }
            System.out.println();
        } while (choice != 6);
    }

    private static void login() {
        System.out.println("********** Login **********");
        System.out.print("Enter your username: ");
        String enteredUsername = scanner.nextLine();
        System.out.print("Enter your password: ");
        String enteredPassword = scanner.nextLine();

        // Validate the username and password
        if (enteredUsername.equals("admin") && enteredPassword.equals("admin")) {
            isLoggedIn = true;
            username = enteredUsername;
            password = enteredPassword;
            System.out.println("Login successful. Welcome, " + username + "!");
        } else {
            System.out.println("Invalid credentials. Login failed!");
        }
    }

    private static void updatePassword() {
        if (isLoggedIn) {
            System.out.println("********** Update Password **********");
            System.out.print("Enter your current password: ");
            String currentPassword = scanner.nextLine();

            if (currentPassword.equals(password)) {
                System.out.print("Enter your new password: ");
                String newPassword = scanner.nextLine();
                password = newPassword;
                System.out.println("Password updated successfully!");
            } else {
                System.out.println("Incorrect current password. Update failed!");
            }
        } else {
            System.out.println("You are not logged in!");
        }
    }

    private static void updateProfile() {
        if (isLoggedIn) {
            System.out.println("********** Update Profile **********");
            System.out.println("Profile updated successfully!");
        } else {
            System.out.println("You are not logged in!");
        }
    }

    private static void startExam() {
        System.out.println("********** Exam Started **********");

        try {
            Thread.sleep(10); 
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("Time's up! Exam automatically submitted.");

        System.out.println("Exam finished!");
    }

    private static void logout() {
        isLoggedIn = false;
        username = null;
        password = null;
        System.out.println("Logout successful. Goodbye!");
    }
}
