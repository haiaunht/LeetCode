public class Sum_Numbers {

public static void main(String[] args) {
System.out.println(sumNumbers("abc123xyz"));
System.out.println(sumNumbers("aa11b33"));
System.out.println(sumNumbers("7 11"));
}

public static int sumNumbers(String s) {
int result = 0;
String currentNum = "";

    for (char c : s.toCharArray()) {
      if (!Character.isDigit(c)) {
        if (!currentNum.isEmpty()) {
          result += Integer.parseInt(currentNum);
          currentNum = "";
        } else {
          continue;
        }
      } else {
        currentNum += c + "";
      }
    }

    //in case the last chars is number so i need to check here
    if (!currentNum.isEmpty()) result += Integer.parseInt(currentNum);
    return result;

}
}
