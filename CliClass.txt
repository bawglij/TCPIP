
import java.io.PrintStream;
import java.net.Socket;
import java.util.Scanner;

public class ClientClass {

	 public static void main(String argv[]) throws Exception {
		  int temperatureCelsius, temp;
		  Scanner sc = new Scanner(System.in);
		  
		  Socket clientSocket = new Socket("localhost", 1343);
		  Scanner scanner = new Scanner(clientSocket.getInputStream());
		  System.out.println("Celsius (°C) to Fahrenheit (°F)");
		  System.out.println("Enter Celsius (°C) temperature");
		  temperatureCelsius = sc.nextInt();
		  PrintStream p = new PrintStream(clientSocket.getOutputStream());
		  p.println(temperatureCelsius);
		  temp = scanner.nextInt();
		  System.out.println("Server response: " + temp + " Fahrenheit (°F)");
		  clientSocket.close();
		  sc.close();
		  scanner.close();
		 }
}
