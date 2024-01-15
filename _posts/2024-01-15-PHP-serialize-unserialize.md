# What You Need to Know About PHP's serialize() and unserialize() Functions

You might have seen weird strings in database fields like in WordPress, something like the following:

```
a:1:{s:13:"administrator";b:1;}
```

If you don't understand what this string is or are not sure, do not worry! 

The above string is actually a piece of serialized data that has been created using PHP's `serialize()` function. If you want to know what the original data has been, pass this string to `unserialize()`, another convenient PHP function that reverses the serialization to give you the data before it was serialized. 

Here's the output of `unserialize('a:1:{s:13:"administrator";b:1;}')`: 

```
php > print_r( unserialize('a:1:{s:13:"administrator";b:1;}'));
Array
(
    [administrator] => 1
)

```

So the two functions are complements and can be very handy. Example usecases of the output of these functions has been seen in WordPress tables. 

## How It Works
By looking at the original data and the serialized string, you can guess:  
- First the data type is specified (a:1 is an array of length 1)
- The curly braces open and close the array
- s:13 is a string of length 13
- administrator is the key
- and it has a boolean value of 1

## Another Example 

```
php > echo serialize(['administrator'=>100, 'age' => '30']);
a:2:{s:13:"administrator";i:100;s:3:"age";s:2:"30";}

php > print_r(unserialize('a:2:{s:13:"administrator";i:100;s:3:"age";s:2:"30";}'));
Array
(
    [administrator] => 100
    [age] => 30
)
php > 

```

