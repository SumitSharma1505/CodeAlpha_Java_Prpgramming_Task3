# CodeAlpha_Java_Prpgramming_Task3
// Task:3 Travel Itinerary Planner

// Create a travel itinerary planner that allows users to
// input destinations, dates, and preferences to generate
// a detailed travel plan. Include features like maps,
// weather information, and budget calculations.

import java.util.*;

class Destination {
    String name;
    String date;
    String preferences;

    public Destination(String name, String date, String preferences) {
        this.name = name;
        this.date = date;
        this.preferences = preferences;
    }

    @Override
    public String toString() {
        return "Destination: " + name + ", Date: " + date + ", Preferences: " + preferences;
    }
}

class Itinerary {
    List<Destination> destinations = new ArrayList<>();
    double budget;

    public void addDestination(Destination destination) {
        destinations.add(destination);
    }

    public void setBudget(double budget) {
        this.budget = budget;
    }

    public void displayItinerary() {
        System.out.println("Travel Itinerary:");
        for (Destination destination : destinations) {
            System.out.println(destination);
        }
        System.out.println("Total Budget: Rs " + budget);
    }
}

public class TravelItineraryPlanner {
    private static Scanner scanner = new Scanner(System.in);
    private static Itinerary itinerary = new Itinerary();

    public static void main(String[] args) {
        System.out.println("Welcome to the Travel Itinerary Planner!");

        while (true) {
            System.out.println("\n1. Add Destination");
            System.out.println("2. Set Budget");
            System.out.println("3. Display Itinerary");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");

            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline

            switch (choice) {
                case 1:
                    addDestination();
                    break;
                case 2:
                    setBudget();
                    break;
                case 3:
                    itinerary.displayItinerary();
                    break;
                case 4:
                    System.out.println("Exiting the planner. Safe travels!");
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }

    private static void addDestination() {
        System.out.print("Enter destination name: ");
        String name = scanner.nextLine();
        System.out.print("Enter date of visit (e.g., YYYY-MM-DD): ");
        String date = scanner.nextLine();
        System.out.print("Enter preferences (e.g., food, adventure, etc.): ");
        String preferences = scanner.nextLine();
        
        Destination destination = new Destination(name, date, preferences);
        itinerary.addDestination(destination);
        System.out.println("Destination added!");
    }

    private static void setBudget() {
        System.out.print("Enter your total budget: Rs ");
        double budget = scanner.nextDouble();
        itinerary.setBudget(budget);
        System.out.println("Budget set to Rs " + budget);
    }
}
