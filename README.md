## Introduction

Learning Ren'Py screen language may be a quite a challenge at first, and your best tool will certainly be the documentation. Learning to read and understand the documentation is a skill that will be not only necessary, but a key factor in your learning process. For this reason, I introduce you to this guide which will teach you how to learn to understand and navigate the screen language documentations.

## Reading Screen Language Documentation

Below is a simple example of a screen User Interface Statement.

![Bar documentation](https://i.imgur.com/TdQZZLK.png)

Let's break it down one section at the time.

### User Interface Statement

![](https://i.imgur.com/BfQkD5o.png)

The User Interface Statement. This is the "element" you would add to your screen.

### Properties

![](https://i.imgur.com/T2OjUqB.png)

Properties. Most User Interface Statements require at least one of these, but some don't. They control how the User Interface Statement operates.

### Common / Style Properties

![](https://i.imgur.com/CnDXU2q.png)

A list of optional common, position, or other style properties that the User Interface Statements takes. Common and position properties are properties that are not specific to this particular statement, and are shared across any other User Interface Statements which takes said properties.

The style property may either be specific to this statement, or shared across multiple statements. For example, the `imagebutton` and `button` statements both share the `button` style property. In this particular example however, the style property is specific to the bar, and applies only to the bar statement.

### Example

![Examples](https://i.imgur.com/b3AMZed.png)

Lastly, most User Interface Statements will include an example at the bottom. This can be used as a quick reference, but typically it will only demonstrate a simple, limited usage of the specific statement. Many statements will have multiple uses which are vastly different from one another. This example of a bar uses `Preference()` as its value, but a bar could use a `range` and `value` instead.

## Navigating the Documentation

The screen language documentation can be visualized as a "tree", a bit like when you navigate through directories on a computer. Let's use the `Bar` statement documentation as an example.

* [User Interface Statement (Bar)](https://www.renpy.org/doc/html/screens.html#bar)
    * *Properties*
        * [Common Properties](https://www.renpy.org/doc/html/screens.html#common-properties)
        * [Position Style Properties](https://www.renpy.org/doc/html/style_properties.html#position-style-properties)
        * [Bar Style Properties](https://www.renpy.org/doc/html/style_properties.html#bar-style-properties)

First you locate the desired `User Interface Statement`. Then, you explore its statement-specific `Properties`, before scrolling down to the bullet list which will allow you to navigate to the `Common`, `Position`, or `Style` properties, which are in a different section, or page of the documentation (for example, the [Style Properties](https://www.renpy.org/doc/html/style_properties.html) category has its own page).

It should be noted that while we are referencing to the documentation as a "tree", your screen code will not follow this pattern. Your code should be formatted to have the `User Interface Statement` and then all its properties, regardless if they are the statement, common, position or style properties, will be treated the same.

### Syntax
Screen language can use various types of syntax - you could write the statement in a single line:
```py
bar value 0 range 10 xpos 500
```
Or you could make the statement a block, and put the properties below it:
```py
bar:
    value 0
    range 10
    xpos 500
```
Or even both combined:
```py
bar xpos 500:
    value 0
    range 10
```
In the examples below, we'll use statements as a block which contains properties, as it will better visualize the concept of the documentation "tree".

### The Tree
Now, let's review the "tree" one more time.

* [User Interface Statement (Bar)](https://www.renpy.org/doc/html/screens.html#bar)
    * *Properties*
        * [Common Properties](https://www.renpy.org/doc/html/screens.html#common-properties)
        * [Position Style Properties](https://www.renpy.org/doc/html/style_properties.html#position-style-properties)
        * [Bar Style Properties](https://www.renpy.org/doc/html/style_properties.html#bar-style-properties)

Using this as a reference, let's make a bar, and give it at least one of each properties it can take.

```py
screen example():

    # The User Interface Statement
    bar:

        # Statement Properties
        value 0
        range 10

        # Common Property
        style "my_awesome_bar_style"

        # Position Style Property
        xpos 500

        # Bar Style Property
        bar_vertical True
```

## Actions

Every User Interface Statement which can be interacted with, such as a `button`, can take an `action` property which defines what happens when the element is interacted with. Other User Interface Statements such as the `bar` may also take an optional `action` property which will run in specific conditions, such as `hovered`.

Here is a list of screen actions you may use: [Screen Actions](https://www.renpy.org/doc/html/screen_actions.html)

Let's use the `button` User Interface Statement as our example, this time.

![](https://i.imgur.com/ZnSw6L3.png)

The `button` statement takes an `action` property which is configured to serve multiple purposes. It takes one or more screen action(s) from the page linked above, but also controls if the button is `sensitive` and/or `selected` automatically if these properties have not been explicitly given.

Other optional action properties such as `hovered` also take a screen action, and can sometimes be found in other statements such as the `bar`, which would allow an `action` to run when the bar is hovered.

### Syntax

The proper syntax for the `action` statements is the same as any other User Interface Statements properties. In the example below, we are creating a button which jumps to a label when clicked, and notifies if the button is hovered. Naturally, in a practical use, you should give the button some style properties so that it is an actual button.


```py
screen example():

    # The User Interface Statement
    button:

        # Screen Actions
        action Jump("a_label")
        hovered Notify("Hovering the button!")
```

Both actions used above are random examples from the [Screen Actions](https://www.renpy.org/doc/html/screen_actions.html) documentation, but the actions themselves could be anything from the documentation.

## Conclusion

And there you have it - you should now be a bit more familiar with how to read the screen language documentation. Equipped with newly acquired knowledge, go forth and create!
