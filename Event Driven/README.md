# Event Driven Programming

- [Event Driven Programming](#event-driven-programming)
  - [Objectives](#objectives)
  - [Introduction](#introduction)
  - [Links and Resources](#links-and-resources)

## Objectives

- Understand the concept of event driven programming
- Understand the concept of event listeners
- Understand the concept of event handlers
- Understand the concept of event objects

## Introduction

Event-driven programming is a paradigm where the program's flow is determined by events, such as user actions (mouse clicks, key presses), sensor outputs, or messages from other programs or threads. This paradigm is rooted in the observer pattern, a design pattern that enables an object, known as the subject or event source, to notify other objects, referred to as observers or event listeners, when its state changes.

In this paradigm, the event source generates events, and the event listeners respond by executing event handlers. This approach is widely used in web development, where events like page loads, form submissions, and button clicks trigger responses from the program.

An event listener is a function triggered when a specific event occurs. It is registered with an event source and is activated when that source generates an event. An event handler, on the other hand, is a function executed when an event listener is activated. Its role is to respond to the event by executing the appropriate code. An event object, which contains information about the occurred event, is passed to the event handler. This object can be used to determine the event type, the event source, and any additional event-related information.

Let's consider a simple example for a simple music player application:

- **Event Source**: The music player application itself. it has several buttons, such as play, pause, and stop, that generate events when clicked.
- **Event Listeners**: The event listeners are the functions that are registered with the buttons. They are activated when the buttons are clicked. For example, the play button has a play event listener, the pause button has a pause event listener, and the stop button has a stop event listener.
- **Event Handlers**: The event handlers are the functions executed when the event listeners are activated. For example, the play event handler starts playing the music, the pause event handler pauses the music, and the stop event handler stops the music.
- **Event Object**: The event object contains information about the event, such as the event type, the event source, and any additional event-related information. For example, the event object for the play button click event contains information about the play button, such as its ID, and the event type, such as "click".

## Links and Resources

- [Event Driven Programming](https://en.wikipedia.org/wiki/Event-driven_programming)
- [TA Video](https://www.aparat.com/v/OubHA)
