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
###find prime factors###
~~~javascript
    function getAllFactorsFor(remainder) {
        var factors = [], i;
        
        for (i = 2; i <= remainder; i++) {
            while ((remainder % i) === 0) {
                factors.push(i);
                remainder /= i;
            }
        }
        
        return factors;
    }
~~~
### get the opposite color , hex given ###
~~~js 
var colorHexa = readline();

R = 255- hexToR(colorHexa);
G = 255 -hexToG(colorHexa);
B = 255 -hexToB(colorHexa);

print(rgbToHex(R,G,B))

function hexToR(h) {return parseInt((cutHex(h)).substring(0,2),16)}
function hexToG(h) {return parseInt((cutHex(h)).substring(2,4),16)}
function hexToB(h) {return parseInt((cutHex(h)).substring(4,6),16)}
function cutHex(h) {return (h.charAt(0)=="#") ? h.substring(1,7):h}
function rgbToHex(r, g, b) {
    return "#" + componentToHex(r) + componentToHex(g) + componentToHex(b);
}
function componentToHex(c) {
    var hex = c.toString(16).toUpperCase();
    return hex.length == 1 ? "0" + hex : hex;
}
~~~
