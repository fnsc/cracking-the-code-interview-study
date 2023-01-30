## Chapter VI - Big O

- **Time complexity** 
  - No matter how big the constant is and how slow the linear increase is, linear will at some point surpass constant.
  - We can describe our runtime for an algorithm in three different ways: 
    * Best Case **O(1)**;
    * Worst Case;
    * Expected Case;
- **Space Complexity**
  - It is the amount of memory -or space- required by an algorithm. This is a parallel concept to time complexity. 
    * Stack space in recursive calls counts, i.e.:
      ```php
      public function sum(int $n): int
      {
          if ($n <= 0) {
              return 0;
          }
      
          return $n + sum($n - 1);
      } 
      ```
      Each call adds a level to the stack and takes up actual memory: 
      ```php
      sum(4)
        -> sum(3)
          -> sum(2)
            -> sum(1)
              -> sum(0)
      ```
      However, in the code below, we have n calls, which doesn't mean it takes O(n): 
      ```php
      public function pairSumSequence(int $n): int
      {
          $sum = 0; 
      
          for ($i = 0; $i < $n; $i++) {
              $sum += $this->pairSum($i, $i + 1);
          }
      
          return $sum;
      }
      
      private function pairSum(int $a, int $b): int
      {
          return $a + $b;
      }
      ```
      There will be roughly O(n) calls to `pairSum`. However, those calls do not exists simultaneously on the call stack, so you only need O(1) space.
- **Drop the Constants**