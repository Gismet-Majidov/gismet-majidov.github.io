---
title: Introduction to Swing Java
description: GUI programming with Java Swing 
author: Gismet Majidov
date: 2026-05-13 23:39:00 +0400
categories: [Java, Swing]
tags: [programming, java, gui, swing, graphics, tutorial]
math: true
---

# Introduction to Java Swing GUI Programming

First we need a window on which to build our GUI. `JFrame` is the way to get a window. 

```java

package com.example;

import javax.swing.JFrame;
import javax.swing.WindowConstants;


public class Main {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Be happy!"); //create a window
        frame.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE); //define the close operation
        frame.setSize(700, 700); //set the width and height of the window (by default window size is adjustable)
        frame.setVisible(true); //set the visibility to true to show the window
    }
}

```

This will open up a window. 

Now let's take a look at some **components** that we can add to the window. 

To start with an easy example, let's add a button. Note that we should add any component to the window
before we make it visible. So add the following code before you set the size and visibility of the window in 
the above code.

```java

import javax.swing.JButton; //also add this


JButton button = new JButton("Click here");
frame.add(button);

```
This will display a simple button in the center of the window. Now button takes up the entire window as we didn't set its size. You can click the button. It won't do much as we haven't said it to do something. We will see how to do that later. You can do various things to the button itself. But for now let's keep it simple. Button by default will appear in the center. We will get into layouts in more details. But till that, let's see other components. 

Now let's add a label, which is a piece of uneditable text. We will do something similar to button.

```java

import javax.swing.SwingConstants;
import javax.swing.JLabel;
import java.awt.Font; //We need Font from abstract window toolkit (awt is an old graphics API in Java)

JLabel label = new JLabel("This is a label");
//let's make it a little nice
label.setFont(new Font(Font.SERIF, Font.BOLD, 30)); 
label.setHorizontalAlignment(SwingConstants.CENTER);
frame.add(label);

```
Now we will see a bigger text in the center of the window. 

Let's now add a text box that can be edited by the user. You can customize your components. Check out the Java API for more components and their capabilites. 

```java
import java.awt.Color;

JTextArea textBox = new JTextArea("Type something here...");
textBox.setBackground(Color.LIGHT_GRAY);
textBox.setFont(new Font(Font.SERIF, Font.BOLD, 30));
textBox.setSelectedTextColor(Color.GREEN);
frame.add(textBox);

```

Now let's learn how to add more components to our window. We need a container for your components. That is exactly what `JPanel` is. First we need to create a `JPanel` instance and then add our components to the panel and then add the panel to the window/frame. By default components appear one after the other, wrapping to next row if they can't fit the window. 

```java

import javax.swing.JPanel;

JPanel panel = new JPanel();
JButton buttonOne = new JButton("I am button one");
JButton buttonTwo = new JButton("I am button two");
JLabel label = new JLabel("I am a label");
panel.add(buttonOne);
panel.add(buttonTwo);
panel.add(label);
frame.add(panel);

```

This adds two buttons and a label to the panel and then adds the panel to the window. 

Thus far components showed up in the window in their default places but this doesn't always look good. In fact, it rarely looks good. So we want to change their places to make them look nice. For this we will use **layout managers**. Let's take a look at it. 

