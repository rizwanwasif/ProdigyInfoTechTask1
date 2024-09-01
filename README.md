# ProdigyInfoTechTask1
import java.util.Scanner;

public class TemperatureConverter {

    public static double celsiusToFahrenheit(double celsius) {
        return (celsius * 9 / 5) + 32;
    }

    public static double celsiusToKelvin(double celsius) {
        return celsius + 273.15;
    }

    public static double fahrenheitToCelsius(double fahrenheit) {
        return (fahrenheit - 32) * 5 / 9;
    }

    public static double fahrenheitToKelvin(double fahrenheit) {
        return fahrenheitToCelsius(fahrenheit) + 273.15;
    }

    public static double kelvinToCelsius(double kelvin) {
        return kelvin - 273.15;
    }

    public static double kelvinToFahrenheit(double kelvin) {
        return celsiusToFahrenheit(kelvinToCelsius(kelvin));
    }

    public static void convertTemperature(double value, String unit) {
        if (unit.equalsIgnoreCase("Celsius")) {
            double fahrenheit = celsiusToFahrenheit(value);
            double kelvin = celsiusToKelvin(value);
            System.out.printf("%.2f°C is equal to %.2f°F and %.2fK.%n", value, fahrenheit, kelvin);
        } else if (unit.equalsIgnoreCase("Fahrenheit")) {
            double celsius = fahrenheitToCelsius(value);
            double kelvin = fahrenheitToKelvin(value);
            System.out.printf("%.2f°F is equal to %.2f°C and %.2fK.%n", value, celsius, kelvin);
        } else if (unit.equalsIgnoreCase("Kelvin")) {
            double celsius = kelvinToCelsius(value);
            double fahrenheit = kelvinToFahrenheit(value);
            System.out.printf("%.2fK is equal to %.2f°C and %.2f°F.%n", value, celsius, fahrenheit);
        } else {
            System.out.println("Unknown temperature unit. Please enter Celsius, Fahrenheit, or Kelvin.");
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        try {
            System.out.print("Enter the temperature value: ");
            double temperature = scanner.nextDouble();
            scanner.nextLine(); // consume the newline character
            System.out.print("Enter the unit of the temperature (Celsius, Fahrenheit, Kelvin): ");
            String unit = scanner.nextLine();

            convertTemperature(temperature, unit);

        } catch (Exception e) {
            System.out.println("Invalid input. Please enter a numerical temperature value.");
        } finally {
            scanner.close();
        }
    }
}
