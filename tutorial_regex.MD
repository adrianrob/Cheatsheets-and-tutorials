#Tutorial REGEX

## 1) Search a word starting by Bonjour and ending by revoir  in multiple lines

We want to match the lines starting with Bonjour, and ending with revoir, the regular expression that we will use is :

  * /^Bonjour|revoir$/gm

 /gm : g means global text and m means multiple lines__
 ^ : to search X in the start of the line
 $ : to search Y in the end of the line
 | : to use multiple statements


look the example below

![exp1](screenshots/screen1.png)

## 2) Search a subset of chars sharing some letters

We want to search for these words : mots,mats,mits

We could use this regex
 * mots|mats|mits

But, we can cross this regex, because the three words share the following letters : m,t,s  and we will match the words that have either o OR a OR i between m and ts so it gives us this :
 * /m[oai]ts/gm

this regex can be explained that way : search all the words that starts with __m__ and end with __ts__, and between them, match a word that have either the letter __o, or a, or i__

![exp2](screenshots/screen2.png)

We can use this regex to do the "opposite" of what we want to match this way :

  * /m[^oai]ts/gm

this regex means : search all the words that starts with __m__ and ends with __ts__,  by exluding those which contain either __o,a,i__

![exp3](screenshots/screen3.png)
