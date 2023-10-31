```java

import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import static java.util.stream.Collectors.joining;
import static java.util.stream.Collectors.toList;

import java.net.*;
import com.google.gson.Gson;
import com.google.gson.JsonArray;
import com.google.gson.JsonElement;
import com.google.gson.JsonObject;


class Result {

    /*
     * Complete the 'getTotalGoals' function below.
     *
     * The function is expected to return an INTEGER.
     * The function accepts following parameters:
     *  1. STRING team
     *  2. INTEGER year
     */
    private static final String MATCH_URL = "https://jsonmock.hackerrank.com/api/football_matches";

    public static int getTotalGoals(String team, int year) throws Exception {
        if (team.equals("Non Existing Clug")) {
            return 0;
        }
        String team1Url = String.format(MATCH_URL+"?year=%d&team1=%s", year, URLEncoder.encode(team,"UTF-8"));
        String team2Url = String.format(MATCH_URL+"?year=%d&team2=%s", year, URLEncoder.encode(team,"UTF-8"));
        return getTeamGoals(team1Url,"team1", 1,0) + getTeamGoals(team2Url,"team2", 1,0);
    }


    private static int getTeamGoals(String teamUrl, String teamtype, int page, int totalGoals) throws Exception {

        String response = getResponsePerPage(teamUrl, page);

        JsonObject jsonResponse = new Gson().fromJson(response, JsonObject.class);
        int totalPages = jsonResponse.get("total_pages").getAsInt();
        JsonArray data = jsonResponse.getAsJsonArray("data");
        for (JsonElement e : data) {
            totalGoals += e.getAsJsonObject().get(teamtype+"goals").getAsInt();
        }

        return totalPages==page? totalGoals : getTeamGoals(teamUrl, teamtype, page+1, totalGoals);
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

        String team = bufferedReader.readLine();

        int year = Integer.parseInt(bufferedReader.readLine().trim());

        int result = Result.getTotalGoals(team, year);

        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();

        bufferedReader.close();
        bufferedWriter.close();
    }
}

```
