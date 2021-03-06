本課題演示了 前置/後置 型式是怎麼在比較時導致不同結果。

1. **從 1 到 4**

    ```js run
    let i = 0;
    while (++i < 5) alert( i );
    ```

    一開始的值為 `i = 1`，因為 `++i` 會先遞增 `i` 再回傳新的值。所以第一個比較是 `1 < 5`，而 `alert` 將顯示 `1`。

    接著 `2, 3, 4...` 這些值一個個顯示出來。比較總是會使用遞增後的值，因為 `++` 被放在變數之前。

    最後，`i = 4` 遞增至 `5`，比較 `while(5 < 5)` 失敗了而迴圈停止，所以 `5` 不會被顯示。
2. **從 1 到 5**

    ```js run
    let i = 0;
    while (i++ < 5) alert( i );
    ```

    一開始的值也是 `i = 1`，後置型式 `i++` 遞增 `i` 並回傳 *原本* 的值，所以比較 `i++ < 5` 將會使用 `i = 0`（與 `++i < 5` 不同）。

    但 `alert` 是分開呼叫的，它在遞增和比較之後的另一個述語內執行，所以得到 `i = 1`。

    接下來是 `2, 3, 4...`

    讓我們先在 `i = 4` 停下來。使用前置型式 `++i` 將會遞增並使用 `5` 做比較，但這裡我們使用的是後置型式 `i++`，所以它遞增了 `i` 至 `5`，但回傳舊的值。因此事實上比較的是 `while(4 < 5)` -- 為真，故控制權依然給了 `alert`。

    `i = 5` 是最後一個值了，因為下一步 `while(5 < 5)` 為假。

