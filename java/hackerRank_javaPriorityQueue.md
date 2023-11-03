```java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;
/*
 * Create the Student and Priorities classes here.
 */
 import java.util.Queue;
 import java.util.PriorityQueue;
 
 class Student implements Comparable<Student>{
     
     public Student(int id, String name, double cgpa){
         this.id = id;
         this.name = name;
         this.cgpa = cgpa;
     }
     
     private int id;
     private String name;
     private double cgpa;
     
     public int getID() {
         return this.id;
     }
     
     public String getName() {
         return this.name;
     }
     
     public double getCGPA() {
         return this.cgpa;
     }
     
     @Override
    public int compareTo(Student student) {

        int cgpaCompare = Double.compare(student.cgpa, cgpa);
        
        if (cgpaCompare == 0) {
            int nameCompare = name.compareTo(student.name);
            if(nameCompare == 0) {
                return Integer.compare(student.id, id);
            }
            return nameCompare;
        }
        return cgpaCompare;
    }
 }
 
 class Priorities {
     private Queue<Student> queue = new PriorityQueue<>();
     
     public List<Student> getStudents(List<String> events) {
         
         for (String event : events) {
            String[] s = event.split(" ");
            if (s[0].equals("ENTER")) {
                Student student = new Student(Integer.parseInt(s[3]), s[1], Double.parseDouble(s[2]));
                queue.add(student);
            } else {
                queue.poll();
            }
         }
         List<Student> list = new ArrayList<>();
         
         while (!queue.isEmpty()) {
             list.add(queue.poll());
         }
         
         return list;
     }
 }

public class Solution {
    private final static Scanner scan = new Scanner(System.in);
    private final static Priorities priorities = new Priorities();
    
    public static void main(String[] args) {
        int totalEvents = Integer.parseInt(scan.nextLine());    
        List<String> events = new ArrayList<>();
        
        while (totalEvents-- != 0) {
            String event = scan.nextLine();
            events.add(event);
        }
        
        List<Student> students = priorities.getStudents(events);
        
        if (students.isEmpty()) {
            System.out.println("EMPTY");
        } else {
            for (Student st: students) {
                System.out.println(st.getName());
            }
        }
    }
}

```
