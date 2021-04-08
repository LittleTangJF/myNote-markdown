## 字符串查找：请使用最基本的遍历来实现判断字符串 a 是否被包含在字符串 b 中，并返回第一次出现的位置（找不到返回 -1）。

1. ```js
   例如
   a='34';b='1234567'; // 返回 2
   a='35';b='1234567'; // 返回 -1
   a='355';b='12354355'; // 返回 5
   isContain(a,b);
   
   题解
   function isContain(a, b) {
     for(let i in b){
       	if(a[0] == b[i]){
           	let tmp = true
             	for(let j in a){
                 	if(a[j] !== b[~~i + ~~j]){
                      tmp = false
                   }
                 if(tmp){
                   return i
                 }
               }
         }
     }
     return -1;
   }
   
   ```

   