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

### Accessing Values in a Dictionary

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

### Adding New Key-Value Pairs

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

### Starting with an Empty Dictionary

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

### Modifying Values in a Dictionary

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

### Removing Key-Value Pairs

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

### A Dictionary of Similar Objects

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

### Using get() to Access Values

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

### TRY IT YOURSELF: Working with Dictionaries

**6-1. Person**: Use a dictionary to store information about a person you know. Store their first name, last name, age, and the city in which they live. You should have keys such as first_name , last_name , age , and city . Print each piece of information stored in your dictionary.

**6-2. Favorite Numbers**: Use a dictionary to store people’s favorite numbers. Think of five names, and use them as keys in your dictionary. Think of a favorite number for each person, and store each as a value in your dictionary. Print each person’s name and their favorite number. For even more fun, poll a few friends and get some actual data for your program.

**6-3. Glossary**: A Python dictionary can be used to model an actual dictionary. However, to avoid confusion, let’s call it a glossary.

* Think of five programming words you’ve learned about in the previous chapters. Use these words as the keys in your glossary, and store their meanings as values.
* Print each word and its meaning as neatly formatted output. You might print the word followed by a colon and then its meaning, or print the word on one line and then print its meaning indented on a second line. Use the newline character ( \n ) to insert a blank line between each word-meaning pair in your output.

---

## Looping Through a Dictionary

A single Python dictionary can contain just a few key-value pairs or millions of pairs. Python lets us loop through a dictionary with large amounts of data. We can loop through all of a dictionary's key-values pairs, through its keys, or through its values.

### Looping Through All Key-Value Pairs

Let's consider a new dictionary designed to store information about a user on a website. The following dictionary would store one person's username, first name, and last name:

``` python
user_0 = {
    'username': 'efermi',
    'first': 'enrico',
    'last': 'fermi'
    }
```

If we wanted to see everything stored in this user's dictionary, loop through the dictionary using a `for` loop:

``` python
user_0 = {
    'username': 'efermi',
    'first': 'enrico',
    'last': 'fermi',
    }

for key, value in user_0.items():
    print(f"\nKey: {key}")
    print(f"Value: {value}")
```

To write a `for` loop for a dictionary, create names for the two variables that will hold the key and value in each key-value pair. Any names can be used for these two variables. This code would work just as well if we used abbreviations for variable names:

`for k, v in user_0.items()`

The second half of the `for` statement includes the name of the dictionary followed by the method `items()`, which returns a list of key-value pairs. The `for` loop then assigns each of these pairs to the two variables provided. In the preceding example, we use the variables to print each key followed by the associated value. The "\n" in the first `print()` call ensures that a blank line is inserted before each key-value pair in the output:

``` markdown
Key: last
Value: fermi

Key: first
Value: enrico

Key: username
Value: efermi
```

Looping through all key-value pairs works well for dictionaries in a previous example to store each person name and their favorite programming language. The keys always refer to a person's name and the value is always a language. We will use the variables *name* and *language* in the loop instead of *key* and *value*. This will make it easier to follow what is happening inside the loop:

``` python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
    }

for name, language in favorite_languages.items():
    print(f"{name.title()}'s favorite language is {language.title()}.")
```

The code tells Python to loop through each key-value pair in the dictionary. As it works through each pair the key is assigned to the variable *name*, and the value is assigned to the variable *language*.

``` markdown
Jen's favorite language is Python.
Sarah's favorite language is C.
Edward's favorite language is Ruby.
Phil's favorite language is Python.
```

Looping would work even if our dictionary stored the results from polling a thousand or even a million people.

### Looping Through All the Keys in a Dictionary

They `keys()` method is useful when we don't need to work with all of the values in a dictionary. Let's loop through the *favorite_languages* dictionary and print the names of everyone who took the poll:

``` python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
    }

for name in favorite_languages.keys():
    print(name.title())
```

Python pulls all the keys from the dictionary *favorite_languages* and assign them one at a time to the variable *name*. The output shows the names of everyone who took the poll:

``` markdown
Jen
Sarah
Edward
Phil
```

Looping through the keys is actually the default behavior when looping through a dictionary. The output would be the same:

`for name in favorite_languages:`

compared to:

`for name in favorite_languages.keys():`

Use the `keys()` method explicitly if it makes code easier to read, or omit it.

We can access the value associated with any key inside the loop by using the current key. We will loop through the names in the dictionary, and display a message about their favorite language when name matches one of our friends:

``` python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
    }

friends = ['phil', 'sarah']

for name in favorite_languages.keys():
    print(name.title())

    if name in friends:
        language = favorite_languages[name].title()
        print(f"\t{name.title()}, I see you love {language}!")
```

We check whether the *name* is in the list of *friends*. If it is, we determine the person's favorite language using the name of the dictionary and the current value of *name* as the key. Then, print a special greeting, including a reference to their language of choice.

Everyone's name is printed, but our friends receive a special message:

``` markdown
Hi Jen.
Hi Sarah.
Sarah, I see you love C!
Hi Edward.
Hi Phil.
Phil, I see you love Python!
```

We can also use the `keys()` method to find out if a particular person was polled. Let's find out if Erin took the poll:

``` python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
    }

if 'erin' not in favorite_languages.keys():
    print("Erin, please take our poll!")
```

The `keys()` method isn't just for looping: it actually returns a list of all the keys, and simply checks if 'erin' is in this list. Because she is not, a message is printed inviting her to take the poll:

`Erin, please take our poll!`

### Looping Through a Dictionary's Keys in a Particular Order

Starting in Python 3.7, looping through a dictionary returns the items in the same order they were inserted. Sometimes, we want to loop through a dictionary in a different order.

One way is to sort the keys as they are returned in the `for` loop. Use the `sorted()` function to get a copy of the keys in order:

``` python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
    }

for name in sorted(favorite_languages.keys()):
    print(f"{name.title()}, thank you for taking the poll.")
```

This `for` statement is like other `for` statements except it is wrapped inside the `sorted()` function with *dictionary.keys()* method. This tells Python to list all keys in the dictionary and sort that list before looping through it. The output shows everyone who took the poll, with the names displayed in order:

``` markdown
Edward, thank you for taking the poll.
Jen, thank you for taking the poll.
Phil, thank you for taking the poll.
Sarah, thank you for taking the poll.
```

### Looping Through All Values in a Dictionary

We can use `values()` method to return a list of values without any keys. For example, say we simply want a list of all languages chosen in our programming language poll without the name of the person:

``` python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
    }

print("The following languages have been mentioned:")
for language in favorite_languages.values():
    print(language.title())
```

The `for` statement pulls each value from the dictionary and assigns it to the variable *language*.

``` markdown
The following languages have been mentioned:
Python
C
Python
Ruby
```

This approach pulls all the values from the dictionary without checking for repeats. That might work fine with small number of values, but in a poll with a large number of respondents, this would result in a repetitive list. To see each language chosen without repetition, we can use a set. A `set` is a collection in which each item must be unique:

``` python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
    }

print("The following languages have been mentioned:")
for language in set(favorite_languages.values()):
    print(language.title())
```

When we wrap `set()` around a list that contains duplicate items, Python identifies the unique items in the list and builds a set from those items.

The result is a non repetitive list of languages that have been mentioned by the poll:

``` markdown
The following languages have been mentioned:
Python
C
Ruby
```

***We can build a set directly using braces and separating the elements with commas:***

``` python
>>> languages = {'python', 'ruby', 'c'}
>>> languages
{'ruby', 'python', 'c'}
```

***It is easy to mistake sets for dictionaries because they're both wrapped in braces. When there is no key-value pairs, it is most likely a set. Unlike lists and dictionaries, sets do not retain items in any specific order.***

---

### TRY IT YOURSELF: Looping Through a Dictionary

**6-4. Glossary 2**: Now that you know how to loop through a dictionary, clean up the code from Exercise 6-3 (page 99) by replacing your series of print() calls with a loop that runs through the dictionary’s keys and values. When you’re sure that your loop works, add five more Python terms to your glossary.
When you run your program again, these new words and meanings should automatically be included in the output.

**6-5. Rivers**: Make a dictionary containing three major rivers and the country
each river runs through. One key-value pair might be 'nile': 'egypt'.

* Use a loop to print a sentence about each river, such as The Nile runs through Egypt.
* Use a loop to print the name of each river included in the dictionary.
* Use a loop to print the name of each country included in the dictionary.

**6-6. Polling**: Use the code in favorite_languages.py (page 97).

* Make a list of people who should take the favorite languages poll. Include some names that are already in the dictionary and some that are not.
* Loop through the list of people who should take the poll. If they have
already taken the poll, print a message thanking them for responding.
If they have not yet taken the poll, print a message inviting them to take the poll.

---

## Nesting

Storing multiple dictionaries in a list, or a list of items as a value in a dictionary is called *nesting*. We can nest dictionaries inside a list, a list of items inside a dictionary, or even a dictionary inside another dictionary.

### A List of Dictionaries

We can make a list of aliens in which each alien is a dictionary to store more information on multiple aliens. For example, the following code builds a list of three aliens:

``` python
alien_0 = {'color': 'green', 'points': 5}
alien_1 = {'color': 'yellow', 'points': 10}
alien_2 = {'color': 'red', 'points': 15}

aliens = [alien_0, alien_1, alien_2]

for alien in aliens:
    print(alien)
```

First, we create three dictionaries, each representing a different alien, and store each of them in a list called *aliens*. Finally, we loop through the list and print out each alien:

``` markdown
{'color': 'green', 'points': 5}
{'color': 'yellow', 'points': 10}
{'color': 'red', 'points': 15}
```

A more realistic example would involve more than three aliens with code that automatically generates each alien. In the following example we use `range()` to create a fleet of 30 aliens:

``` python
# Make an empty list for storing aliens.
aliens = []

# Make 30 green aliens
for alien_number in range(30):
    new_alien = {'color': 'green', 'points': 5, 'speed': 'slow'}
    aliens.append(new_alien)

# Show the first 5 aliens.
for alien in aliens[:5]:
    print(alien)
print("...")

# Show how many aliens have been created.
print(f"Total number of aliens: {len(aliens)}")
```

The example begins with an empty list to hold all the aliens that will be created. At `range()` returns a series of numbers to tell Python how many times we want the loop to repeat. Each time the loop runs we create a new alien and then append each new alien to the list. Then we finally use a slice to print the first five aliens, and print the length to prove all 30 aliens exist:

``` markdown
{'speed': 'slow', 'color': 'green', 'points': 5}
{'speed': 'slow', 'color': 'green', 'points': 5}
{'speed': 'slow', 'color': 'green', 'points': 5}
{'speed': 'slow', 'color': 'green', 'points': 5}
{'speed': 'slow', 'color': 'green', 'points': 5}
...

Total number of aliens: 30
```

These aliens all have the same characteristics, but Python considers each one a separate object, which allows us to modify each alien individually.

To change colors , we can use a `for` loop and an `if` statement to change the color of aliens. For example, to change the first three aliens to yellow, medium-speed aliens worth 10 points each:

``` python
# Make an empty list for storing aliens.
aliens = []

# Make 30 green aliens.
for alien_number in range(30):
    new_alien = {'color': 'green', 'points': 5, 'speed': 'slow'}
    aliens.append(new_alien)

for alien in aliens[:3]:
    if alien['color'] == 'green':
        alien['color'] = 'yellow'
        alien['speed'] = 'medium'
        alien['points'] = 10

# Show the first 5 aliens.
for alien in aliens[:5]:
    print(alien)
print("...")
```

We want to modify the first three aliens, we loop through slice that includes only the first three aliens. All of the aliens are green but that won't always be the case, so we write an `if` statement to make sure only modifying green aliens. If the alien is green, we change the color to 'yellow', the speed to 'medium', and the point value to 10.

``` markdown
{'speed': 'medium', 'color': 'yellow', 'points': 10}
{'speed': 'medium', 'color': 'yellow', 'points': 10}
{'speed': 'medium', 'color': 'yellow', 'points': 10}
{'speed': 'slow', 'color': 'green', 'points': 5}
{'speed': 'slow', 'color': 'green', 'points': 5}
...
```

We could expand this loop by adding an `elif` block that turns yellow aliens into red, fast-moving ones worth 15 points each. The loop would look like this:

``` python
aliens = []

# Make 30 green aliens.
for alien_number in range(30):
    new_alien = {'color': 'green', 'points': 5, 'speed': 'slow'}
    aliens.append(new_alien)

for alien in aliens[:3]:
    if alien['color'] == 'green':
        alien['color'] = 'yellow'
        alien['speed'] = 'medium'
        alien['points'] = 10
    elif alien['color'] == 'yellow':
        alien['color'] = 'red'
        alien['speed'] = 'fast'
        alien['points] = '15
```

It is common to store a number of dictionaries in a list when each dictionary contains many kinds of information about one object. For example, we might create a dictionary for each user on a website. All of the dictionaries in the list should have an identical structure so it is possible to loop through the list and work with each dictionary object in the same way.

### A List in a Dictionary

Rather than putting a dictionary inside a list, it is sometimes useful to put a list inside a dictionary. For example, consider how to describe a pizza that someone is ordering. If were to use only a list, the only item to store is a list of the pizza's toppings. With a dictionary, a list of toppings can be just one aspect of the pizza.

In the following example, two kinds of information are stored for each pizza: type of crust and a list of toppings. The list of toppings is a value associated with the key 'toppings'. Instead of returning a single value, we get a list of toppings:

``` python
# Store information about a pizza being ordered.
pizza = {
'crust': 'thick',
'toppings': ['mushrooms', 'extra cheese'],
}

# Summarize the order.
print(f"You ordered a {pizza['crust']}-crust pizza with the following toppings:")

for topping in pizza['toppings']:
    print("\t" + topping)
```

We begin with a dictionary that holds information about a pizza that has been ordered. One key in the dictionary is 'crust', and the associated value is the string 'thick'. The next key, 'toppings', has a list as its value that stores all requested toppings. To print the toppings, we write a `for` loop to access the list of the key 'toppings'. The output summarizes the pizza that we plan to build:

``` markdown
You ordered a thick-crust pizza with the following toppings:
mushrooms
extra cheese
```

We can nest a list inside a dictionary any time we want more than one value to be associated with a single key in a dictionary. In the earlier example of favorite programming languages, we could store more than one favorite language for each person's responses. When we loop through the dictionary, the value associated with each person would be a list of languages. Inside the dictionary's `for` loop, we use another `for` loop to run through the list of languages associated with each person:

``` python
favorite_languages = {
'jen': ['python', 'ruby'],
'sarah': ['c'],
'edward': ['ruby', 'go'],
'phil': ['python', 'haskell'],
}

for name, languages in favorite_languages.items():
    print(f"\n{name.title()}'s favorite languages are:")
    for language in languages:
        print(f"\t{language.title()}")
```

Now each person can list as many favorite languages as they like:

``` markdown
Jen's favorite languages are:
Python
Ruby

Sarah's favorite languages are:
C

Edward's favorite languages are:
Ruby
Go

Phil's favorite languages are:
Python
Haskell
```

To refine this program even further, an `if` statement at the beginning of the dictionary's `for` loop to see whether reach person has more than one favorite language by examining the value of `len(languages)`.

### A Dictionary in a Dictionary

We can nest a dictionary inside another dictionary, but code can get complicated quickly. For example, if we have several users for a website, each with a unique username, we can use the usernames as the keys in a dictionary. Then store information about each user by using a dictionary as the value associated with their username. We store three pieces of information about each user:

* First name
* Last name
* Location

We can access this information by looping through the usernames and the dictionary of information associated with each username:

``` python
users = {
    'aeinstein': {
        'first': 'albert',
        'last': 'einstein',
        'location': 'princeton',
    },

    'mcurie': {
        'first': 'marie',
        'last': 'curie',
        'location': 'paris',
    },
}

for username, user_info in users.items():
    print(f"\nUsername: {username}")
    full_name = f"{user_info['first']} {user_info['last']}"
    location = user_info['location']

    print(f"\tFull name: {full_name.title()}")
    print(f"\tLocation: {location.title()}")
```

We first define a dictionary called *users* with two keys: one each of the usernames *'aeinstein'* and *'mcurie'*. The value associated with each key is a dictionary that includes each user's first name, last name, and location. We loop through the *users* dictionary where Python assigns each key to the variable *username*. The dictionary associated with each username is assigned to the variable *user_info*. Once inside the `for` loop, we start accessing the inner dictionary which contains the user information to generate a summary about each user.

``` markdown
Username: aeinstein
    Full name: Albert Einstein
    Location: Princeton

Username: mcurie
    Full name: Marie Curie
    Location: Paris
```

---

### TRY IT YOURSELF: Nesting

**6-7. People**: Start with the program you wrote for Exercise 6-1 (page 99). Make two new dictionaries representing different people, and store all three dictionaries in a list called people. Loop through your list of people. As you loop through the list, print everything you know about each person.

**6-8. Pets**: Make several dictionaries, where each dictionary represents a different pet. In each dictionary, include the kind of animal and the owner’s name. Store these dictionaries in a list called pets . Next, loop through your list and as you do, print everything you know about each pet.

**6-9. Favorite Places**: Make a dictionary called favorite_places . Think of three names to use as keys in the dictionary, and store one to three favorite places for each person. To make this exercise a bit more interesting, ask some friends to name a few of their favorite places. Loop through the dictionary, and print each person’s name and their favorite places.

**6-10. Favorite Numbers**: Modify your program from Exercise 6-2 (page 99) so each person can have more than one favorite number. Then print each person’s name along with their favorite numbers.

**6-11. Cities**: Make a dictionary called cities. Use the names of three cities as keys in your dictionary. Create a dictionary of information about each city and include the country that the city is in, its approximate population, and one fact about that city. The keys for each city’s dictionary should be something like country , population , and fact . Print the name of each city and all of the information you have stored about it.

**6-12. Extensions**: We’re now working with examples that are complex enough that they can be extended in any number of ways. Use one of the example programs from this chapter, and extend it by adding new keys and values, changing the context of the program or improving the formatting of the output.

---

## Summary

What we learned in this chapter:

* How to define a dictionary.
* How to work with information stored in a dictionary.
* Access and modify individual elements in a dictionary.
* Loop through a dictionary's key-value pairs, its keys, and its values.
* Nest multiple dictionaries in a list, nests lists in a dictionary, and nest a dictionary inside a dictionary.
