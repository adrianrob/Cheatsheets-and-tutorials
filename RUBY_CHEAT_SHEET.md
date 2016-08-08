### check if letter in range ###
~~~ruby
("a".."z").cover?("c")
~~~
### arrays lessons ###
~~~ruby
the_count = [1, 2, 3, 4, 5]
fruits = ['apples', 'oranges', 'pears', 'apricots']
change = [1, 'pennies', 2, 'dimes', 3, 'quarters']

## this first kind of for-loop goes through a list##
## in a more traditional style found in other languages##
for number in the_count
  puts "This is count #{number}"
end

## bestrubypractices##
fruits.each do |fruit|
  puts "A fruit of type: #{fruit}"
end

## also we can go through mixed lists too##
change.each {|i| puts "I got #{i}" }

## we can also build lists, first start with an empty one##
elements = []

## then use the range operator to do 0 to 5 counts##
(0..5).each do |i|
  puts "adding #{i} to the list."
  # pushes the i variable on the *end* of the list
  elements.push(i)
end

## now we can print them out too##
elements.each {|i| puts "Element was: #{i}" }

//bail
gets.split(" ").map(&:to_i).map(&:chr).join
//tableau.convertiToI.convertiToCharCode.concatene
~~~

