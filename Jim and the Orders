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

class Result {

    /*
     * Complete the 'jimOrders' function below.
     *
     * The function is expected to return an INTEGER_ARRAY.
     * The function accepts 2D_INTEGER_ARRAY orders as parameter.
     */
    public static HashMap<Integer, Integer> sortByValue(Map<Integer, Integer> hm)                        // comparator foundation begin
    {
        // Create a list from elements of HashMap
        List<Map.Entry<Integer, Integer>> list =
               new LinkedList<Map.Entry<Integer, Integer>>(hm.entrySet());
 
        // Sort the list
        Collections.sort(list, new Comparator<Map.Entry<Integer, Integer>>() {
            public int compare(Map.Entry<Integer, Integer> o1,
                               Map.Entry<Integer, Integer> o2)
            {   
                if(o1.getValue()==o2.getValue())return o1.getKey()-o2.getKey();                           //the Map is serial_orderno. - sum_oftimetaken
                return o1.getValue()-o2.getValue();                                          // order in asc by sum_oftimetaken if its equal asc by serial_orderno.
            }
        });
         
        // put data from sorted list to hashmap
        HashMap<Integer, Integer> temp = new LinkedHashMap<Integer, Integer>();
        for (Map.Entry<Integer, Integer> aa : list) {
            temp.put(aa.getKey(), aa.getValue());
        }
        return temp;                                                                                        //foundation end
    }
    public static List<Integer> jimOrders(List<List<Integer>> orders) {
    // Write your code here
    List<Integer> sumList=new ArrayList<Integer>();int custNo=1;
    Map<Integer,Integer>sequence=new HashMap<Integer,Integer>();
    for(List<Integer> details: orders){
        sequence.put(custNo++,details.get(0)+details.get(1));
    }
    HashMap<Integer,Integer> hm1 = sortByValue(sequence);
    for(int key:hm1.keySet()){
        sumList.add(key);    
    }
    return sumList;
    }

}

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int n = Integer.parseInt(bufferedReader.readLine().trim());

        List<List<Integer>> orders = new ArrayList<>();

        IntStream.range(0, n).forEach(i -> {
            try {
                orders.add(
                    Stream.of(bufferedReader.readLine().replaceAll("\\s+$", "").split(" "))
                        .map(Integer::parseInt)
                        .collect(toList())
                );
            } catch (IOException ex) {
                throw new RuntimeException(ex);
            }
        });

        List<Integer> result = Result.jimOrders(orders);

        bufferedWriter.write(
            result.stream()
                .map(Object::toString)
                .collect(joining(" "))
            + "\n"
        );

        bufferedReader.close();
        bufferedWriter.close();
    }
}
