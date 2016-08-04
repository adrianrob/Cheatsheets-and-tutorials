### binary to hexa ###

~~~javascript
// js
x = 1011
y = parseInt(x,2).toString(16)
~~~
### hex to char ###
~~~javascript
// js
x = 'F6'
char = String.fromCharCode( parseInt(x,2).toString(16) )
~~~
### string to binary to string ###
~~~javascript
str = 'yolo';
binary = (str>>>0).toString(2);
strconverted = parseInt(binary, 2).toString();
~~~
### determine if N is prime ###
~~~javascript
function isPrime (n){
    if (n < 2) return false;
    var q = Math.floor(Math.sqrt(n));
    for (var i = 2; i <= q; i++)
    {
        if (n % i == 0)
        {
            return false;
        }
    }
    return true;
}
~~~
###fill array from 1...n ###
~~~javascript
Array.from({length: 5}, (v, k) => k);    
// [0, 1, 2, 3, 4]
//pour une suite geometrique il suffit de multiplier k par la raison
~~~
###fill array n-times with X value ###
~~~javascript
Array(n).fill(X);  
~~~

