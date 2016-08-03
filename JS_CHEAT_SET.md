CODINGAME CHEATSET :
=====================

### binary to hexa ###

~~~javascript
// js
x = 1011
y = parseInt(x,2).toString(16)
~~~
### string to binary to string ###
~~~javascript
binary = (str>>>0).toString(2);
parseInt(binary, 2).toString();
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


