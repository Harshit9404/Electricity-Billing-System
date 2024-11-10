# Electricity-Billing-System
import java.util.Scanner;

class Customer {
    String name;
    int meterNumber;
    double unitsConsumed;

    Customer(String name, int meterNumber, double unitsConsumed) {
        this.name = name;
        this.meterNumber = meterNumber;
        this.unitsConsumed = unitsConsumed;
    }
}

class Bill {
    Customer customer;

    Bill(Customer customer) {
        this.customer = customer;
    }

    double calculateBill() {
        double amount = 0;
        if (customer.unitsConsumed <= 100) {
            amount = customer.unitsConsumed * 1.5;
        } else if (customer.unitsConsumed <= 300) {
            amount = 100 * 1.5 + (customer.unitsConsumed - 100) * 2.5;
        } else {
            amount = 100 * 1.5 + 200 * 2.5 + (customer.unitsConsumed - 300) * 4.0;
        }
        return amount;
    }

    void generateBill() {
        System.out.println("Electricity Bill for " + customer.name);
        System.out.println("Meter Number: " + customer.meterNumber);
        System.out.println("Units Consumed: " + customer.unitsConsumed);
        System.out.println("Total Bill Amount: $" + calculateBill());
    }
}

public class ElectricityBillingSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter customer name: ");
        String name = sc.nextLine();

        System.out.print("Enter meter number: ");
        int meterNumber = sc.nextInt();

        System.out.print("Enter units consumed: ");
        double unitsConsumed = sc.nextDouble();

        Customer customer = new Customer(name, meterNumber, unitsConsumed);
        Bill bill = new Bill(customer);

        bill.generateBill();
    }
}
