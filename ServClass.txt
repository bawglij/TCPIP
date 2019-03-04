import java.io.PrintStream;
import java.net.ServerSocket;
import java.net.Socket;
import java.util.Scanner;

public class ServerClass {

	public static void main(String argv[]) throws Exception{
		int temperatureCelsius, tempFahrenheit;
		double test;
		ServerSocket ServerSocket = new ServerSocket(1343);
		while(true)
		{
			Socket connectionSocket = ServerSocket.accept();
			Scanner scanner = new Scanner(connectionSocket.getInputStream());
			
			temperatureCelsius = scanner.nextInt();
			test = temperatureCelsius * 1.8 + 32;
			tempFahrenheit = (int)test;
			
			PrintStream p = new PrintStream(connectionSocket.getOutputStream());
			p.println(tempFahrenheit);
		}
	}
}
