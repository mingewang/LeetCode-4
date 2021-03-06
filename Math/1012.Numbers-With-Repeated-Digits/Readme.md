### 1012.Numbers-With-Repeated-Digits

此题本质就是求不大于N的、没有重复数字的数。简单的想法，可以用无脑的DFS，结果会超时。

超时的原因在于，比如N=782581676，如果第一位取了1，后面8位数字其实就是从[0，2-9]这些数字里面任取8个全排列。这就提示我们DFS的时候，不必在每一个分支都用递归来计算，适当的时候直接调用数学公式就行了。

所以本题的解包括两部分：对于M位数的上限，我们先注意考察一位数，两位数，直到M-1位数的解。这些解注定不会大于N，所以直接调用数学公式，计算用10个不同的数字如何排列出k位数的方案数。但需要注意，任何k位数，其首位都不能是0.

第二部分，就是考察M位数的解。主体框架就是DFS，每个位置逐一考察。第k个位置如果选择比num[k]小的数字，那么剩余的部分就可以用全排列来解。如果第k个位置选择了num[k]，那么就递归考察下一个位置。注意，一个必要条件是，第k个位置的选择不能在前k-1个位置上出现过，所以我们需要一个visited来记录使用过的数字，这是一个回溯的过程。
