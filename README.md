<p>This is my note from a <a href="https://www.youtube.com/watch?v=oBt53YbR9Kk">freecodecamp's Dynamic programming</a> course. Feel free to read it through!</p>

# <b>Fib Memoization</b>

## Fib function
<details>

```
/*
Write a function 'fib(n)' that takes in a number as an argument. The function should return the n-th number of the fibonacci sequence.

The 1st and 2nd number of sequence is 1. To generate the next number of the sequence, we sum the previous two.
ex: 

n     : 1, 2, 3, 4 ...
fib(n): 1, 1, 2, 3 ...
*/
//fib reg
const fib = (n) => {
  if(n <= 2) return 1;
  return fib(n - 1) + fib(n - 2);
};

console.log(fib(6));
console.log(fib(7));
console.log(fib(8));


//fib memoization
const fib_memo = (n, memo = {}) => {
  if(n in memo) return memo[n];
  if(n <= 2) return 1;
  return fib_memo(n-1, memo) + fib(n-2, memo);
}

console.log(fib_memo(6));
```

</details>

## Foo function:
- O(n) <abbr title="10:49 the speed a function is processed">time</abbr> and <abbr title="12:37 stack space that our function calls">space</abbr> complexity <abbr title="a series or system of written symbols used to represent numbers, amounts, or elements in something such as music or mathematics">notations</abbr>
<details>

  <img src="https://i.postimg.cc/7LkXMMdx/O-n-and-O-space-complexity.png"></img>

  <p>The function is having the n different calls recursively. Therefore, the time complexity of it is O(n).</p>
  <p>In the image above, because we have five or n different function calls added to the space stack, the space complexity is O(n).</p>

</details>

## Bar function
<details>

<img src="https://i.postimg.cc/JhzjMBcR/minus-2-time-complexity.png"></img>

- How does the -2 change the time complexity of this function?
  - Because we are moving twice as far with the -2, so we are moving twice as far upon every recursive calls. So this actually half the number of recursive calls we need. So the time complexity of this is actually O(n/2). But according to Big O notation, <abbr title="this has relation with the question below">we can remove any multiplicative constants when we have a time complexity</abbr>. So n over two is the same as one half times. So it simplifies nicely to just an O of n time complexity or O(n).
   - Question: <i><a href="https://cs.stackexchange.com/questions/138497/is-the-multiplicative-constant-in-the-big-o-notation-are-ignored-because-of-line">Is the multiplicative constant in the Big O notation are ignored because of Linear Speed-Up theorem?</a></i>
   <p>I just want to know if Big O notation was used as a consequences of the <a href="https://en.wikipedia.org/wiki/Linear_speedup_theorem">linear speedup theorem</a> or not.</p>
  <p>For me I guess the answer is yes. For example, if we didn't have a linear speed-up theorem, then does it mean that we would have a different measure of time/space complexity? i.e. <a href="https://en.wikipedia.org/wiki/Multiplicative_function">multiplicative constants</a> does makes different. For example, f(n)=100n isn't the same as g(n)=10<sup>82</sup>n. Therefore, in this regard, Big O notation is not useful. So, probably we have another way to measure algorithms.</p>
    - Answer:
      <p>Please note that the <a href="https://en.wikipedia.org/wiki/Big_O_notation"><abbr title="Big O notation is a mathematical notation that describes the limiting behavior of a function when the argument tends towards a particular value or infinity.">big O notation</abbr></a> was invented before the proof of the linear speedup theorem, and even before <a href="https://en.wikipedia.org/wiki/Turing_machine"><abbr title="A Turing machine is a mathematical model of computation that defines an abstract machine that manipulates symbols on a strip of tape according to a table of rules">Turing machines</abbr></a>.</p>
      <p>Also, the big O notation often gives an information independant of the multiplicative constant: "if I multiply the input by k, then the total computing time will not be multiplied by more than …".</p>
      <p>Finally, keep in mind that the linear speedup theorem gives a way to reduce the number of steps in the execution of a Turing Machine, but if you implement it on a real computer, it often also means that each step may be longer, so the real total time may not decrease.</p>
      <p>The big O notation is a convenient way to compare <a href="https://en.wikipedia.org/wiki/Asymptotic_computational_complexity"><abbr title="asymptotic computational complexity is the usage of asymptotic analysis for the estimation of computational complexity of algorithms and computational problems, commonly associated with the usage of the big O notation.">asymptotic time complexity</abbr></a>, but it is not always sufficient. For example, mergesort have an asymptotic complexity Θ(nlogn), but considering the multiplicative constant, it is often better to use insertion sort to sort small data, even if the asymptotic complexity of insertion sort is Θ(n2) in average. Another example are <a href="https://en.wikipedia.org/wiki/Fibonacci_heap#Worst_case">Fibonacci heaps</a>.</p>

</details>

## Dib function
<details>

<img src="https://i.postimg.cc/FR8h5vP9/dib-function.png"></img>

<p> To get the total number of nodes, or the total number of calls recursive function would make, you just take the number of two and multiply it by itself about n times over. Thus it's really the definition of an <abbr title="a quantity representing the power to which a given number or expression is to be raised, usually expressed as a raised symbol beside the number or expression (e.g. 3 in 23 = 2 × 2 × 2).">exponent</abbr>. It's the same as 2<sup>n</sup> (two to the n power).</p>
<p>The space complexity of this function isn't the same as the time complexity. It's reasonable trap because in the long run, we're gonna have to evaluate two to the n function calls, so it means you have to put two to the n function calls on the stack.</p>
<p>When we actually hit the base case, which is 1, it will actually will return. When a function returns, its stack frame is actually removed or popped from the stack. At this point, only after i have returned from that left one, what i actually add to the right one to be explored. And so on.</p>
<p>Therefore, the number of stack frames that we're going to use is really just the height of the tree. That means our maximum stack depth is also n. So we have n space complexity coming from the call stack.</p>
<article>
<h3><b>Complete time and space complexity</b></h3>
</article>

<blockquote><img src="https://i.postimg.cc/YCLchxcb/complete-dib-time-and-space-complexity.png"></img></blockqoute>

</details>

## Lib function
<details>
<img src="https://i.postimg.cc/Dwr5zCfr/lib-function.png"></img>
</details>

###Conclusion based on dib and lib function about <b>fib function</b>
<details>
<blockquote><img src="https://i.postimg.cc/Fs6rWZjQ/both-dib-and-lib-function-t-and-s-complexity.png"></img></blockquote>

<p>Both lib and dib have the O(2<sup>n</sup>) time and O(n) space complexity. So where does the fibonacci function/fib func fits? Well, fib func falls right in between the two.</p>

<blockquote><img src="https://i.postimg.cc/P5WtX8LL/fib-falls-right-in-between.png"></img></blockquote>

<p>The fib func has two recursive calls. One with the <code>n - 1</code> and the second with the <code>n - 2</code>. So we can say the time complexity of fib is between the dib & lib. And because of fib has the lower bound of dib which is <code>n - 1</code> and the upper bound that is lib. It means that our fib must have exactly the 2<sup>n</sup> time complexity. Thus, it's evident that our fib func has the <code>O(2<sup>n</sup>)</code> and <code>O(n) space</code> complexity.</p>
<blockquote><img src="https://i.postimg.cc/q7KQBBKD/time-complexity-of-fib.png"></img></blockquote>

</details>

## The reason why we need memoization
<details>
<img src="https://i.postimg.cc/gkwzjJwq/the-problem-with-fib.png"></img>
<p>When it comes to a big numbers, it'll cause a bottleneck to the fib func in the time complexity from the number of recursive calls we make.</p>

<article><h3><b>If we look into this numbers of tree</b></h3></article>
<img src="https://i.postimg.cc/KYyk2L8H/storing-the-repetitive-numbers-in-memoization.png"></img>
<p>We notice that <code>3</code> here is in multiple places. Therefore, it is useful for us to store it in one place so when we meet the exact number repetitively, we can directly get the number from the storage and that's what memoization is. It's useful to cut off the bottleneck we have in the fib func.</p>

</details>

## Disecting the memoized code
<details>
<img src="https://i.postimg.cc/zGPSVKCX/memoized-fib-func.png"></img>
<p>If i were to call the fib function and not pass the secondary argument, by default, it will create an empty object. So this memo is going to store <code>n</code> as a key and return values for this function.</p>
<p>We first check for existence of <code>n</code> inside memo. If it is, then return the memo with the key of <code>n</code>. Now we're saving the value inside of the memo object. What i want to do is make sure that all these recursive functions are accessing the same memo, so we are passing the memo to both of <code>fib(n-1)</code> and <code>fib(n-2)</code> calls.</p>
<p>At first the memo is an empty string and is not initiated. But in the recursive calls, the memo indeed is passed in explicitly. So they're actually going to recieve the same memo object, and it would be like passed by reference. Because when you pass a JavaScript object to a function, you actually receive the exact object, not a copy of it. So, the function calls communicate with each other, they all have some sort of global information to reference accross all the recursive trees.</p>
<p>The memoized function reduce the function into 2n in time and space complexity because we are left with each pair of n. By memoized the function, we brought it down from an exponential function or 2<sup>n</sup> into linear function of O(n) notation in time and space complexity.</p>
<blockquote><img src="https://i.postimg.cc/pVsmnXDc/time-and-space-complexity-of-memoized-fib.png"></img></blockquote>
</details>

### Two dimensional grid of gridTraveler case

<details>
<p>Say that you are a traveler on a 2D grid. You begin in the top-left corner and your goal is to travel to the bottom-right corner. You may only move down or right.</p>

<p>In how many ways can you travel to the goal on a grid with dimension m * n?</p>

<p>Write a function <code>gridTraveler(m, n)</code> that calculates this.</p>

<article><h3><b>For example</b></h3></article>
<img src="https://i.postimg.cc/DzhLnfkv/grid-Traveler-example.png"></img>

<p>In here, the reason why we don't use the probability theory in math is because we can get the exact movement of each valid points. Even though we can multiply 2 * 3 and then devide it with 2 as the chances there are in which returns 3. But we won't get the exact movement and points that store the valid numbers.</p>

<p>Here is the example to make the explanation more clear</p>
<img src="https://i.postimg.cc/1z8JTc6x/what-i-mean-by-that.png"></img>

<p>The time complexity of the gridTraveler is O(2<sup>n+m</sup>), why? Let's take a look at the picture below.</p>
<img src="https://i.postimg.cc/3RJr26tv/n-plus-m.png"></img>

<p>There are two choices to move. First, to move down or right. That being said, we need to realize the height of this tree. The height of the tree is from the top level call we make (2,3) to the bottom level (1,1) or (0,2). So, either my argument hits (1,1) or one of my argument turns 0. But the farthest we can go is when my argument turns into (1,1). And i know from one node to the next, i will decrease n or m. I can't decrease them both because that way i will move diagonally which is prohibited in the game. So in that sense, from the bottom level to the top level, we know that to reach that top level we need to add n to the m. So we know that our time complexity is n + m and because from top to bottom we move exponentially or the number keeps increasing to the power of 2, the time complexity of gridTraveler is indeed O(2<sup>n+m</sup>) and the maximal stack depth of the tree comes from the height of the tree which is n + m, therefore its space complexity is O(n+m).</p>

<h3><b>Final code</b></h3>

```
const gridTraveler = (m , n, memo={}) => {
  const key = m + ',' + n;
  if(key in memo) return memo[key];
  if(m === 1 && n == 1) return 1;
  if(m === 0 || n == 0) return 0;
  memo[key] = gridTraveler(m - 1, n, memo) + gridTraveler(m, n - 1, memo);
  return memo[key];
};

console.log(gridTraveler(1,1)); //1
console.log(gridTraveler(2,3)); //3
console.log(gridTraveler(3,2)); //3
console.log(gridTraveler(3,3)); //6
console.log(gridTraveler(18,18)); //2333606220
```

</details>

## <abbr title="can you do it? (decision problem)">canSum</abbr>
<details>
<img src="https://i.postimg.cc/xTGKBvT1/canSum.png"></img>
<p>To understand the time and space complexity of the canSum, let's take a look at the picture below</p>
<img src="https://i.postimg.cc/63rq6ckT/can-Sum-time-and-space-complexity.png"></img>
<p>First, we need to take a look at the height or levels of the tree. In the worst case, the distance from the root to the base case is exactly m because you need to substract one the m times. So the height of the tree is basically m.</p>

<p>The branching factor of the tree is basically the lenght of the array. SO if the length of the array is 4, the branches of the tree is also 4. This is the same thing as saying, <i>we take n and multiply it by itself m times</i>. Therefore, the time complexity of canSum is O(n<sup>m</sup>) and the space complexity is basically just the height of the tree which is O(m).</p>

<h3><b>Final code</b></h3>

```
const canSum = (targetSum, numbers, memo={}) => {
  if(targetSum in memo) return memo[targetSum];
  if(targetSum === 0) return true;
  if(targetSum < 0) return false;
  
  for(let num of numbers) {
    const remainder = targetSum - num;
    if (canSum(remainder, numbers, memo) === true) {
      memo[targetSum] = true;
      return true;
    }
  }
  memo[targetSum] = false;
  return false;
};

console.log(canSum(7, [2,3])); //true
console.log(canSum(7, [2,4])); //false
console.log(canSum(300, [7, 14])); //false
```

</details>

## <abbr title="how will you do it? (combinatoric problem)">howSum</abbr>
<details>
<img src="https://i.postimg.cc/mrQLy3QQ/howSum.png"></img>
<p>The time complexity of this howSum function is the same as the canSum function we have before which is O(n<sup>m</sup>), except we have another spreadsheet in our function or the <code>...remainderResult</code> there which basically create another copy of the array, so it needs to take a linear number of steps for it to copy an array. So it iterates through the remainding result and the maximum length of the remainderResult i would get back will be at most the m. Thus, the time complexity of it will be <code>O(n<sup>m</sup> * m)</code>. The memoized version of it will optimize the exponential part which is n<sup>m</sup>, even though we will still have the m<sup>2</sup> in space complexity but it is still sufficient in the time complexity.</p>

<h3><b>Final code</b></h3>

```
const howSum = (targetSum, numbers, memo={}) => {
  if(targetSum in memo) return memo[targetSum];
  if(targetSum === 0) return [];
  if(targetSum < 0) return null;
  
  for(let num of numbers) {
    const remainder = targetSum - num;
    const remainderResult = howSum(remainder, numbers, memo);
    if(remainderResult !== null) {
      memo[targetSum] = [...remainderResult, num];
      return memo[targetSum];
    }
  }
  memo[targetSum] = null;
  return null;
}

/*
m = target sum
n = numbers.length

Brute Force
time: O(n^m * m)
space: O(m)

Memoized
time: O(n * m^2)
space: O(m^2)
*/

console.log(howSum(7, [2,3])); //[3,2,2]
console.log(howSum(7, [2,4])); //null
console.log(howSum(300, [7, 14])); //null
```

</details>

## <abbr title="How is the best way to do it? (optimization problem) Ex. bestSum(7, [5, 3, 4, 7]) -> 7 (the shortest way possible)">bestSum</abbr>
<details>

```
const bestSum = (targetSum, numbers, memo={}) => {
  if(targetSum in memo) return memo[targetSum];
  if(targetSum === 0) return [];
  if(targetSum < 0) return null;
  
  let shortestCombination = null;
  
  for(let num of numbers) {
    const remainder = targetSum - num;
    const remainderCombination = bestSum(remainder, numbers, memo);
    if(remainderCombination !== null) {
      const combination = [...remainderCombination, num];
      //if the combination is shorter than the current 'shortest', update it
      if(shortestCombination === null ||combination.length < shortestCombination.length) {
        shortestCombination = combination;
      }
    }
  }
  memo[targetSum] = shortestCombination;
  return shortestCombination;
}

console.log(bestSum(7, [5, 3, 4, 7])); //[7]
console.log(bestSum(100, [1, 2, 5, 25])) //[25. 25. 25, 25]
```

</details>

## canConstruct memoization
<details>
<article><b><h3>The problem</h3></b></article>

<p>Write a function <code>canConstruct(target, wordBank)</code> that accepts a target string and an array of strings.</p>

<p>The function should return a boolean indicating whether or not the
<code>target</code> can be constructed by concatenating elements of the
<code>wordBank</code> array.</p>

<p>You may reuse elements of <code>wordBank</code> as many times as needed.</p>

<p><b>For example:</b></p>
<p><blockquote><code>canConstruct(abcdef, [ab, abc, cd, def, abcd]) -> true</code></blockquote></p> 

<p>The question is can you construct abcdef using the elements of the array. Looking at the array you can construct 'abcdef' using 'abc' + 'def', so the answer is true because, at least, there is one way to construct 'abcdef' here.</p>

<h3><b>Code</b></h3>

```
console.log("This is canConstruct")
const canConstruct = (target, wordBank) => {
  if(target === '') return true;
  //iterate through all of the words
  for (let word of wordBank) {
    if(target.indexOf(word) === 0) { //front word
      const suffix = target.slice(word.length); //back word
      
      if(canConstruct(suffix, wordBank) === true) {
        return true;
      }
    }
  }
  return false;
}

console.log(canConstruct("abcdef", ["ab", "abc", "cd", "def", "abcd"])); //true
console.log(canConstruct("skateboard", ["bo", "rd", "ate", "t", "ska", "sk", "boar"])); //false
console.log(canConstruct("enterapotentpot", ["a", "p", "ent", "enter", "ot", "o", "t"])); // true
console.log(canConstruct("eeeeeeeeeeeeeeeeeeeeef", ["eeee", "eeeee", "eeeeee"])); // false
```
<p>To better understand the indexOf and slice, here is an example.</p>

```
word = 'pot';
target = 'potato';
target.indexOf(word); //0
target.slice(word.length) //ato
```

<p>The <code>target.slice(word.length)</code> here, it'll return everything starting from the index 3. So, the <abbr title="A suffix is a group of letters placed at the end of a word to make a new word. A suffix can make a new word in one of two ways: inflectional (grammatical): for example, changing singular to plural (dog → dogs), or changing present tense to past tense (walk → walked).">suffix</abbr> here is slicing the rest of target word and compare it with the words in word bank <b>if</b> the target word is in the index of word in the word bank. If nothing of the words in the word bank is the index of target word, it means it doesn't have the right word to construct the target word, let alone get the suffix to complete the construction of the target word.</p>

<p>Here are some trees of our canConstruct function so we can get clearer understanding of what we are doing.</p>
<center><b><h3>Simple example</h3></b></center>
<img src="https://i.postimg.cc/G21VHZpk/can-Construct.png"></img>
<center><b><h3>More robust example</h3></b></center>
<img src="https://i.postimg.cc/2SyDYRqy/enterpotentpot.png"></img>

<p>Based on that tree, we know that in the worst case scenario, the height of our tree will be <code>target.length</code> or m because we will iterate through each index of our target word and the branches of our tree will be multiplied by n or the <code>wordBank.length</code>. Here is the picture to make it clearer.</p>
<center><b><h3>Structure of the calls</h3></b></center>
<img src="https://i.postimg.cc/Qd3fgpD3/can-Construct-time-and-space-complexity.png"></img>

<p>Based on that understanding, if we look at our code, it's even clearer that when we slice on <code>line 6</code>, it returns a new string and that new string is going to tend to be of length m or <code>target.slice(word.length)</code>. So, on every call to canConstruct, we are creating a new string and we need to maintain the recursion before i actually return on the <code>line 8</code>. Based on that, we know that each of m stack frame will have to store a string of length m. <b>It means <code>m * m</code> in space complexity of m<sup>2</sup></b>. Look at the image below to have a better understanding.</p> 
<center><b><h3>Time and space complexity</h3></b></center>
<img src="https://i.postimg.cc/1XKrJds1/can-Construct-complete-time-and-space-complexity.png"></img>

<h3><b>Memoized code</b></h3>

```
const canConstruct = (target, wordBank, memo={}) => {
  if(target in memo) return memo[target];
  if(target === '') return true;
  //iterate through all of the words
  for (let word of wordBank) {
    if(target.indexOf(word) === 0) {
      //the way to check if some substring is a prefix of another string
      const suffix = target.slice(word.length); //2:25:18
      if(canConstruct(suffix, wordBank, memo) === true) {
        memo[target] = true;
        return true;
      }
    }
  }
  memo[target] = false;
  return false;
};

console.log(canConstruct("abcdef", ["ab", "abc", "cd", "def", "abcd"])); //true
console.log(canConstruct("skateboard", ["bo", "rd", "ate", "t", "ska", "sk", "boar"])); //false
console.log(canConstruct("enterapotentpot", ["a", "p", "ent", "enter", "ot", "o", "t"])); // true
console.log(canConstruct("eeeeeeeeeeeeeeeeeeeeef", ["e", "ee", "eee", "eeee", "eeeee", "eeeeee"])); // false
```

</details>

## countConstruct
<details>
<img src="https://i.postimg.cc/zfTGxcTJ/count-Construct.png"></img>
<p>The difference between this function with the canConstruct is beside we are look for ways to get the target word, we also need to return the total ways for words in the word bank to form the target word.</p>
</details>

## allConstruct
<details>

```
const allConstruct = (target, wordBank) => {
  if(target === '') return [[]];
  
  const result = []; //1D array

  for (let word of wordBank) {
    if(target.indexOf(word) === 0) {
      const suffix = target.slice(word.length) //everything after the word
      allConstruct(suffix, wordBank);
      const suffixWays = allConstruct(suffix, wordBank);
      const targetWays = suffixWays.map(way => [word,...way]); //2D array
      result.push(...targetWays);
    }
  }
  return result;
};

console.log(allConstruct('purple', ['purp', 'p', 'ur', 'le', 'purp']));
```
<p>Just in case you're unfamiliar with <code>.map(...)</code> in JavaScript. Let's take a look at the example below.</p>

```
arr = [1,2,3,4]
arr.map(el => el * 2) 
//[ 2, 4, 6, 8 ]
```

<p>The original array is <code>[1, 2, 3, 4]</code> but after the elementary computation there, we get the <code>[2, 4, 6, 8 ]</code>, so it manipulates the array. So that's what the <code>const targetWays</code> is doing there.</p>

<p>Here is another example to explain the <code>suffixWays</code>.</p>

```
suffixWays = [['xy', 'z'], ['x', 'yz']];
suffixWays.map(way => ['a',..way])
//['a', 'xyz', 'z'], ['a', 'x', 'yz']
```

<p>I get the additional 'a' inside of every array. That's what we're doing on that chunk of code.</p>

<p>The <code>result.push(...targetWays)</code> code just push the array without making additional array inside of the array. Look at the example code below.</p>

```
arr = [1, 2, 3, 4]
nums = [7, 8]
arr.push(numbs)
//[1,2,3,4 [7,8]]

arr = [1,2,3,4]
nums = [7,8]
arr.push(...nums)
//[1,2,3,4,7,8]
```

<p>It's time to memoize the code for more efficient way of solving this problem.</p>


```
const allConstruct = (target, wordBank, memo={}) => {
  if(target in memo) return memo[target];
  if(target === '') return [[]];
  
  const result = []; //1D array

  for (let word of wordBank) {
    if(target.indexOf(word) === 0) {
      const suffix = target.slice(word.length) //everything after the word
      const suffixWays = allConstruct(suffix, wordBank, memo);
      const targetWays = suffixWays.map(way => [word,...way]); //2D array
      result.push(...targetWays);
    }
  }
  memo[target] = result
  return result;
};

console.log(allConstruct('purple', ['purp', 'p', 'ur', 'le', 'purp']));
/*[
  ["purp","le"],// [c
  ["p","ur", "p","le"]
  ["purp","le"]]
]*/

console.log(allConstruct("aaaaaaaaaaaaaaaaaaaaaaaaaaz", ["a", "aa", "aaa", "aaaa","aaaaa"])); //[]

```

</details>
