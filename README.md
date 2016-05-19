# Codewars-Collections
codewas代码总结

## 【6 kyu】1.Array.diff
#### Description
  > Your goal in this kata is to implement an difference function, which subtracts one list from another  
  It should remove all values from list a, which are present in list b  
  difference([1,2],[1]) == [2]  
  If a value is present in b, all of its occurrences must be removed from the other:  
  difference([1,2,2,2,3],[2]) == [1,3].
  
#### Solution 
  ```
  function array_diff(a, b){
    return a.filter(function(x) { return b.indexOf(x) == -1; });
  }
  ```
***  
## 【6 kyu】2.Dubstep
#### Description
  >Complete the function:
	songDecoder("WUBWEWUBAREWUBWUBTHEWUBCHAMPIONSWUBMYWUBFRIENDWUB")
  // =>  WE ARE THE CHAMPIONS MY FRIEND

#### Soution 1
```
function songDecoder(song){
  return song.replace(/(WUB)+/g," ").trim()
}
```

#### Solution 2
```
function songDecoder(song){
  return song.split('WUB').filter(Boolean).join(' ');
}
```
***
## 【5 kyu】3.Largest 5 digit number in a series
#### Description
>Complete the solution so that it returns the largest five digit number found within the number given.. The number will be passed in as a string of only digits. It should return a five digit integer. The number passed may be as large as 1000 digits.

#### My Solution
```
//题目digits以字符串的形式给出
function solution(digits){
  var c=[],b = digits.split('');
  var maxNum = Math.max.apply(null,b);//找数组中最大的数
  function run(x,i){
    if(x==maxNum&&i+4<=b.length){
    var temp = b.slice(i,i+5).join('');
    c.push(temp);
    }
  } 
  b.forEach(run);
  return Math.max.apply(null,c);
}
```
	
#### Best Solution
```
function solution(digits){
  if (digits.length <= 5) return Number(digits);
  //使用递归
  return Math.max(Number(digits.substring(0, 5)), solution(digits.substring(1)));
}
```
## 【6 kyu】4.Replace With Alphabet Position
#### Description
  >  In this kata you are required to, given a string, replace every letter with its position in the alphabet. If anything in the text isn't a letter, ignore it and don't return it. a being 1, b being 2, etc. As an example:
	alphabet_position("The sunset sets at twelve o' clock.")
	Should return "20 8 5 19 21 14 19 5 20 19 5 20 19 1 20 20 23 5 12 22 5 15 3 12 15 3 11" (As a string.)

#### Solution 
  ```
  function alphabetPosition(text) {
  var result = "";
  for (var i = 0; i < text.length; i++){
    var code = text.toUpperCase().charCodeAt(i)
    if (code > 64 && code < 91) result += (code - 64) + " ";
  }

  return result.trim();
}
  ```
***  
## 【6 kyu】5.longest_palindrome
#### Description
  > Longest Palindrome
  Find the length of the longest substring in the given string s that is the same in reverse.
  As an example, if the input was “I like racecars that go fast”, the substring (racecar) length would be 7.
  If the length of the input string is 0, return value must be 0.
  Example:
"a" -> 1 
"aab" -> 2  
"abcde" -> 1
"zzbaabcd" -> 4
"" -> 0

#### Solution 
  ```
  longestPalindrome=function(s){
  var longest = 0;
  var length = s.length;

  for(var i=0; i < length; i++){
    for(var j = i+1; j <= length; j++) {
      var str = s.slice(i,j);
      var l = str.length
      if(isPalindrome(str) && longest < l) {
        longest = l;
      }
    }
  }
  return longest;
}

function isPalindrome(s) {
  var arr = s.split("");
  return s == arr.reverse().join("");
}
  ```
***  
