public class Can_Balance {

  public static void main(String[] args) {
    System.out.println(canBalance(new int[]{1, 1, 1, 2, 1}));
    System.out.println(canBalance(new int[]{2, 1, 1, 2, 1}));
    System.out.println(canBalance(new int[]{10, 10}));
  }

  public static boolean canBalance(int[] nums) {
    for (int i=0; i<nums.length; i++) {
      int sum = 0;
      for (int j=0; j<i; j++) {
        sum += nums[j];
      }

      for (int j=i; j<nums.length; j++) {
        sum -= nums[j];
      }

      if (sum == 0) return true;
    }

    return false;
  }
}