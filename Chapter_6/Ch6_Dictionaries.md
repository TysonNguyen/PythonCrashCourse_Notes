# Python Crash Course Chapter 6: Dictionaries

Python's dictionaries allow to connect pieces of related information. We will learn how to access the information once it's in a dictionary and how to modify that information. Dictionaries can store an almost limitless amount of information, and show how we will loop through the data in a dictionary. Additionally, learn how to nest dictionaries inside lists, lists inside dictionaries, and even dictionaries inside other dictionaries.

Understanding dictionaries allows to model a variety of real-world objects more accurately. We will be able to create a dictionary representing a person and then store as much information about that person. We can store their name, age, location, profession, and any other aspect of a person. Also, store any two kinds of information that can be matched up, such as a list of words and their meanings, a list of people's names and their favorite numbers, a list of mountains and their elevations, and so forth.

## A Simple Dictionary

Consider a game featuring aliens that can have different colors and point values. This simple dictionary stores information about a particular alien:

``` python
alien_0 = {'color': 'green', 'points': 5}

print(alien_0['color'])
print(alien_0['points'])
```

The dictionary *alien_0* stores the alien's color and point value. The last two print lines access and display that information:

``` markdown
green
5
```

With most new programming concepts, using dictionaries takes practice and see how effective they can model real-world situations.

## Working with Dictionaries

A *dictionary* in Python is a collection of *key-value* pairs. Each *key* is connected to a value, and use a key to access the value associated with that key. A key's value can be a number, as string, a list, or even another dictionary. Any object that can be created in Python can be used as a value in a dictionary.

In Python, a dictionary is wrapped in braces, {}, with a series of key-value pairs inside the braces:

`alien_0 = {'color': 'green', 'points': 5}`

A *key-value* pair is a set of values associated with each other. When a key is provided, Python returns the value associated with that key. Every key is connected to its value by a colon, and individual key-value pairs are separated by commas. With a dictionary, there is no limit to store key-value pairs.

The simplest dictionary has exactly one key-value pair:

`alien_0 = {'color': 'green'}`

This dictionary stores one piece of information about *alien_0* of the alien's color. The string 'color' is a key in this dictionary, and its associated value is 'green'.

## Accessing Values in a Dictionary

To get the value associated with a key, give the name of the dictionary and then place the key inside a set of square brackets:

``` python
alien_0 = {'color': 'green'}
print(alien_0['color'])
```

This returns the value associated with the key 'color' from the dictionary *alien_0*:

`green`

We can have an unlimited number of key-value pairs in a dictionary. For example, here is a dictionary from previous example with two key-value pairs:

`alien_0 = {'color': 'green', 'points': 5}`

If a player shoots down this alien, we can look up how many points they should earn:

``` python
alien_0 = {'color': 'green', 'points': 5}

new_points = alien_0['points']
print(f"You just earned {new_points} points!")
```

Once the dictionary has been defined, the code pulls the value associated with key 'points' from the dictionary. This value is then assigned to the variable *new_points*. The last line prints a statement about how many points the player just earned:

`You just earned 5 points!`

If we run this code every time an alien is hot down, the alien's point value will be retrieved.

## Adding New Key-Value Pairs

Dictionaries are dynamic structures, and we can add new key-value pairs to a dictionary at any time. To add a new key-value pair, give the name of the dictionary followed by the new key in square brackets along with the new value.

Let's add two new pieces of information to the *alien_0* dictionary: the alien's x- and y- coordinates, which will help us display the alien in a particular position on the screen. Let's place the alien on the left edge of the screen. 25 pixels down from the top. Because screen coordinates usually start at the upper-left corner of the screen, place the alien on the left edge of the screen by setting the x-coordinate to 0 and 25 pixels from the top by settings its y-coordinate to positive 25:

``` python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)

alien_0['x_position'] = 0
alien_0['y_position'] = 25
print(alien_0)
```

When we print the modified dictionary, we see the two additional key-value pairs:

``` markdown
{'color': 'green', 'points': 5}
{'color': 'green', 'points': 5, 'y_position': 25, 'x_position': 0}
```

The final version of the dictionary contains four key-value pairs. The original two specify color and point value, and two more specific the alien's position.

***As of Python 3.7, dictionaries retain the order in which they were defined. When we print a dictionary or loop through its elements, we see the elements in the same order in which they were added to the dictionary.***

## Starting with an Empty Dictionary

It is sometimes convenient, or even necessary, to start with an empty dictionary and then add each new item to it. To start filling an empty dictionary, define a dictionary with an empty set of braces and then add each key-value pair on its own line. For example, build the *alien_0* dictionary:

``` python
alien_0 = {}

alien_0['color'] = 'green'
alien_0['points'] = 5

print(alien_0)
```

We define an empty *alien_0* dictionary, and then add color and point values to it. This is the result of the dictionary:

`{'color': 'green', 'points': 5}`

Typically, empty dictionaries are used when storing user-supplied data in a dictionary or when writing code that generates a large number of key-value pairs automatically.

## Modifying Values in a Dictionary

To modify a value in a dictionary, give the name of the dictionary with the key in square brackets and then the new value associated with that key. For example, consider an alien that changes from green to yellow as a game progresses:

``` python
alien_0 = {'color': 'green'}
print(f"The alien is {alien_0['color']}.")

alien_0['color'] = 'yellow'
print(f"The alien is now {alien_0['color']}.")
```

We define a dictionary for *alien_0* that contains only the alien's color; then we change the value associated with the key 'color' to 'yellow'. The output shows that the alien has indeed changed from green to yellow:

``` markdown
The alien is green.
The alien is now yellow.
```

For a more interesting example, let's track the position of alien that can move at different speeds. We'll store a value represented the alien's current speed and then use it to determine how far to the right alien should move:

``` python
alien_0 = {'x_position': 0, 'y_position': 25, 'speed': 'medium'}
print(f"Original x-position: {alien_0['x_position']}")

# Move the alien to the right.
# Determine how far to move the alien based on its current speed.
if alien_0['speed'] == 'slow':
x_increment = 1
elif alien_0['speed'] == 'medium':
x_increment = 2
else:
# This must be a fast alien.
x_increment = 3

# The new position is the old position plus the increment.
alien_0['x_position'] = alien_0['x_position'] + x_increment
print(f"New x-position: {alien_0['x_position']}")
```

With an `if-elif-else` chain determines how far the alien should move to the right and assigns this value to the variable *x_increment*. If the alien's speed is 'slow', it moves one unit to the right; if the speed is 'medium', it moves two units to the right; and if it's 'fast', it moves three units to the right. Once the increment has been calculated, it's added to the value of *x_position*, and the result is stored in the dictionary's *x_position*.

Because this is a medium-speed alien, its position shifts two units to the right:

``` markdown
Original x-position: 0
New x-position: 2
```

By changing one value in the alien's dictionary, we can the overall behavior of the alien. For example, to turn this medium-speed alien into a fast alien, add the line:

`alien_0['speed'] = 'fast'`

The `if-elif-else` block would then assign a larger value to *x_increment* the next time the code runs.

## Removing Key-Value Pairs

When a piece of information is no longer needed in a dictionary, use the `del` statement to completely remove a key-value pair. All `del` needs is the name of the dictionary and the key to remove.

For example, remove the key 'points' from the *alien_0* dictionary along with its value:

``` python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)

del alien_0['points']
print(alien_0)
```

The `del` statement deletes the key 'points' from the dictionary *alien_0* and the value associated with that key as well. The rest of the dictionary is unaffected:

``` markdown
{'color': 'green', 'points': 5}
{'color': 'green'}
```

***Be aware that deleted key-value pair is removed permanently.***

## A Dictionary of Similar Objects

A dictionary can also store information about many objects. For example, a poll of number of people and ask them what their favorite programming language is. A dictionary is useful for storing the results of a simple poll:

``` python
favorite_languages = {
'jen': 'python',
'sarah': 'c',
'edward': 'ruby',
'phil': 'python'
}
```

To use this dictionary, given the name of a person who took the poll, we can easily look up their favorite language:

``` python
favorite_languages = {
'jen': 'python',
'sarah': 'c',
'edward': 'ruby',
'phil': 'python',
}

language = favorite_languages['sarah'].title()
print(f"Sarah's favorite language is {language}.")
```

To see which language Sarah chose, we ask the value at:

`favorite_languages['sarah']`

We use this syntax to pull Sarah's favorite language from the dictionary and assign it to the variable *language*. Creating a new variable makes a cleaner `print()` call. The output shows Sarah's favorite language:

`Sarah's favorite language is C.`

This same syntax can be used for any individual represented in the dictionary.

## Using get() to Access Values

Using keys in square brackets to retrieve the value from a dictionary might cause one potential problem: if the key doesn't exist, an error will occur.

Let's see what happens when we ask for the point value of an alien that doesn't have a point value set:

``` python
alien_0 = {'color': 'green', 'speed': 'slow'}
print(alien_0['points'])
```

This results in a traceback, showing a *KeyError*:

``` markdown
Traceback (most recent call last):
File "alien_no_points.py", line 2, in <module>
print(alien_0['points'])
KeyError: 'points'
```

For dictionaries, use the `get()` method to set a default value that will be returned if the requested key doesn't exist.

The `get()` method requires a *key* as a first argument. As a second optional argument, we can pass the value to be returned if the key does not exist:

``` python
alien_0 = {'color': 'green', 'speed': 'slow'}

point_value = alien_0.get('points', 'No point value assigned.')
print(point_value)
```

If the key 'points' exists in the dictionary, it will return the corresponding value. If it doesn't, the default value is printed. In this case, *points* does not exist, and we get a clean message instead of an error:

`No point value assigned.`

***If the second argument in the call of `get()` and the key does not exist, Python will return the value *None*. This is not an error: it's a special value meant to indicate the absence of a value, "no value exists."***

---

## TRY IT YOURSELF: Working with Dictionaries

**6-1. Person**: Use a dictionary to store information about a person you know. Store their first name, last name, age, and the city in which they live. You should have keys such as first_name , last_name , age , and city . Print each piece of information stored in your dictionary.

**6-2. Favorite Numbers**: Use a dictionary to store people’s favorite numbers. Think of five names, and use them as keys in your dictionary. Think of a favorite number for each person, and store each as a value in your dictionary. Print each person’s name and their favorite number. For even more fun, poll a few friends and get some actual data for your program.

**6-3. Glossary**: A Python dictionary can be used to model an actual dictionary. However, to avoid confusion, let’s call it a glossary.

* Think of five programming words you’ve learned about in the previous chapters. Use these words as the keys in your glossary, and store their meanings as values.
* Print each word and its meaning as neatly formatted output. You might print the word followed by a colon and then its meaning, or print the word on one line and then print its meaning indented on a second line. Use the newline character ( \n ) to insert a blank line between each word-meaning pair in your output.

---