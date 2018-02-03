import java.io.*;
import java.util.*;

public class Solution {
    char s;
    char q;
    Stack<String> stack;
    Queue<String> qu;
    
    Solution(){
    stack=new Stack<String>();
    qu=new LinkedList<String>();
    }
    
   void pushCharacter(char s)
   {
       String h=String.valueOf(s);
       stack.push(h);
   }
    void enqueueCharacter(char q)
    {
       String g=String.valueOf(q);
        qu.add(g);
      
    }
    char popCharacter()
    {
      String r=stack.pop();
       char a=r.charAt(0);
      return a;
    }
    char dequeueCharacter()
    {
        String w=qu.remove();
        char b=w.charAt(0);
        return b;
    }
 public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String input = scan.nextLine();
        scan.close();

        // Convert input String to an array of characters:
        char[] s = input.toCharArray();

        // Create a Solution object:
        Solution p = new Solution();

        // Enqueue/Push all chars to their respective data structures:
        for (char c : s) {
            p.pushCharacter(c);
            p.enqueueCharacter(c);
        }

        // Pop/Dequeue the chars at the head of both data structures and compare them:
        boolean isPalindrome = true;
        for (int i = 0; i < s.length/2; i++) {
            if (p.popCharacter() != p.dequeueCharacter()) {
                isPalindrome = false;                
                break;
            }
        }

        //Finally, print whether string s is palindrome or not.
        System.out.println( "The word, " + input + ", is " 
                           + ( (!isPalindrome) ? "not a palindrome." : "a palindrome." ) );
    }
}