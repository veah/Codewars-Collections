# Codewars-Collections
codewas代码总结

## 1.Array.diff
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
## 2.Dubstep
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
## 3.Largest 5 digit number in a series
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

