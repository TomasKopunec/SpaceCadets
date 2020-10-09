import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.net.URL;
import java.util.Scanner;

public class emailFetch {
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        System.out.print("Enter emailID to get name: ");
        long timeStart = System.currentTimeMillis();
        try {
            System.out.print(fetchName(scan.nextLine()));
        } catch (Exception e) {
            e.printStackTrace();
        }
        System.out.println(" , finished in " + String.valueOf(System.currentTimeMillis() - timeStart) + "ms");
    }

    public static String fetchName(String ID) throws Exception {
        String webAdress = "https://www.ecs.soton.ac.uk/people/";
        URL url = new URL(webAdress + ID);

        //BufferedReader for the url to read each line of HTML code of the website
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(url.openStream()));
        String inputLine = "";
        String matchedIn = "";
        int i = 0;

        //Loop through the html lines until finds <title>Name | ...</title>
        while((inputLine = bufferedReader.readLine()) != null){
            if(i == 7){
                matchedIn = inputLine;
                matchedIn = matchedIn.substring(matchedIn.indexOf(">") + 1, matchedIn.length());
                matchedIn = matchedIn.substring(0, matchedIn.indexOf("|") - 1);
                break;
            }
            i++;
        }
        bufferedReader.close();
        return matchedIn;
    }
}
