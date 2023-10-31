```java
import java.io.*;
import java.math.*;
import java.net.HttpURLConnection;
import java.net.MalformedURLException;
import java.net.ProtocolException;
import java.net.URL;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import com.google.gson.Gson;
import com.google.gson.JsonArray;
import com.google.gson.JsonElement;
import com.google.gson.JsonObject;

class Result {

    /*
     * Complete the 'getNumDraws' function below.
     *
     * The function is expected to return an INTEGER.
     * The function accepts INTEGER year as parameter.
     */

    private static final String MATCH_URL = "https://jsonmock.hackerrank.com/api/football_matches";

    public static int getNumDraws(int year) throws Exception{

        int maxGoal = 10;
        int totalMatch=0;

        for(int goal=0; goal<=maxGoal; goal++) {
            totalMatch += getDrawMatchbyGoals(MATCH_URL+"?year="+year, goal);
        }

        return totalMatch;
    }

    private static int getDrawMatchbyGoals(String url, int goal) throws Exception{

        String endpoint = String.format(url+"&team1goals=%d&team2goals=%d",goal,goal);
        String response = getResponsePerPage(endpoint, 1);

        JsonObject res = new Gson().fromJson(response, JsonObject.class);
        return res.get("total").getAsInt();
    }

    private static String getResponsePerPage(String endpoint, int page) throws MalformedURLException, IOException, ProtocolException {

        System.out.println(String.format(" URL: %s and page: %d", endpoint, page));

        URL url = new URL(endpoint+"&page="+page);
        HttpURLConnection con = (HttpURLConnection) url.openConnection();
        con.setRequestMethod("GET");
        con.addRequestProperty("Content-Type", "application/json");

        int status = con.getResponseCode();
        if(status<200 || status>=300) {
            throw new IOException("Error in reading data with status:"+status);
        }

        BufferedReader br = new BufferedReader(new InputStreamReader(con.getInputStream()));
        String response;
        StringBuilder sb = new StringBuilder();
        while((response = br.readLine())!=null) {
            sb.append(response);
        }

        br.close();
        con.disconnect();

        return sb.toString();
    }
}

public class Solution {
    public static void main(String[] args) throws Exception {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int year = Integer.parseInt(bufferedReader.readLine().trim());

        int result = Result.getNumDraws(year);

        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();

        bufferedReader.close();
        bufferedWriter.close();
    }
}


```
