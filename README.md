# Intro to Testing

## Objectives
1. Explain why we write tests for our applications.
2. Describe high-level approaches to testing.
3. Explain the difference between unit and integration tests.

## The need for testing
![Testing for failures](https://media.giphy.com/media/7MZ0v9KynmiSA/giphy.gif)

For new programmers, testing can seem like a massive undertaking. There's so much stuff to set up at first. Where do we even begin? But we won't be scared off like that; that's not how we roll. Once more unto the breach!

The truth is, testing can be super helpful. It helps us verify that our code works as intended, and provides a nice starting point for other developers to dissect our code (and hopefully contribute). Having automated tests makes us feel confident that our code is robust. Who doesn't like to feel confident?

Another thing that most people new to testing seem to overlook is the time we _gain_ by writing tests. Sure, we have to spend some time setting up our initial testing infrastructure and writing the tests themselves. That, however, pales in comparison to the time we gain by having a machine check our code for us instead of having to retest everything manually every single time we make a small change to our application. Machines are orders of magnitude faster than humans, so the testing is done a lot quicker. This allows us to write **more** code in **less** time!

Let's say we're implementing some kind of card game (think _Uno_ or something similar). We have all this game logic that is intertwined. If player one puts down a red four, player two has to put down a red card, a different-colored four card, or a wild card. That's a lot of different scenarios to test out! Testing this stuff manually (e.g. going through all of the steps required to see the result of what we're working on) would take forever. Creating tests as we go along and running that test suite when we make each change, however, takes **seconds**. Doesn't that sound appealing? Programmers are ~lazy~ efficient by default. It's good to be efficient. Let the machines do the heavy lifting!

## So how does it work?
![How does it work?](https://media.giphy.com/media/xTk9ZMcahswelC60ko/giphy.gif)

Ideally, we start by writing tests first. Everyone thinks about the code they're going to write to a certain degree, but writing tests forces us to put this into words. We're effectively creating a spec for our code — we're writing down how it should behave. Doing this also makes us think about edge cases and error handling a little sooner, which is always good for code quality.

However, in the real world, writing tests isn't always the first thing that's done. Sometimes we already have a bunch of code — whether from an old project, code that was handed down to us, et cetera. Writing tests **after** code has already been written is still a very valuable exercise: it allows us to more deeply understand the code. It also gives us the confidence to refactor things, since, if the tests still pass after our refactoring, it means our program still works!

Something you'll hear often is the 'Red, Green, Refactor' mantra. The 'Red' part stands for writing a test that fails initially (since you don't have any code at that point). Next, we make the tests pass (make them 'Green') in the simplest possible way. When all tests pass, we can go ahead and refactor our simple code to either optimize for performance, make it more readable, or simply tidy it up a bit.

## Different kinds of tests
When talking about testing, you'll notice that there are various sorts of tests. Here, we'll quickly illustrate the difference between them using our card game example from before.

### Unit testing
Unit testing is testing the smallest unit possible of our program. These small units are usually single functions. Functions vary in size and can still be relatively big, so the amount of tests you write for a given function depends on the size of the 'unit' you're testing. For example, in our card game, we
have a function that checks if a card can be legally played:
```js
function canCardBeLegallyPlayed (cardToBePlayed, cardOnTopOfDeck) {
  const isSameColor = cardToBePlayed.color === cardOnTopOfDeck.color;
  const isSameSymbol = cardToBePlayed.symbol === cardOnTopOfDeck.symbol;
  const isBlackBonusCard = cardToBePlayed.color === 'black';

  return isSameColor || isSameSymbol || isBlackBonusCard;
}
```

This is a relatively simple function, but there are already edge cases involved: we can only play a card if the number and/or symbol matches **or** if the card is a black bonus card. We can write several tests for this, each passing different arguments to the function and expecting a different output.

### Integration testing
Integration testing is where we kick things up a notch and start looking at the bigger picture: how do all the units in our program work together? Do they play nice when used in concert with each other? Is the data returned from our functions being stored in the right place?

### End-to-end testing
This is the most similar thing to our slow, laborious, manual testing that we'll find. End-to-end testing is the big kahuna. Think of end-to-end testing like the things we'd do in the browser ourselves: '_When I click this button, the card should appear in this location_'. This kind of testing takes a while to set up, and it's done using specialized tools. These tests are also the _slowest_ to run since they have to do so much work. However, it's still much, much faster than testing things manually!

## Conclusion
Maintaining a robust test suite is how professional developers ensure the quality of their code. It's a massive boost to productivity to be able to run a test suite instead of having to manually check every piece of functionality in your app after every tiny change. Because of that, we want to get you super comfortable around tests.

For now, we're taking a high-level view of testing. Why do we test? What are the basic categories of software tests? We've already done a bit of reading a test suite, looking at the code that tests our code. As we dive deeper into JavaScript, you'll feel more and more at home poking around the test suites in our labs. After all, **every test suite is written in plain, ole' JavaScript**. That's right: JavaScript code testing JavaScript code. As you progress through the curriculum, you'll pick up the skills you need to write your own JavaScript test suites.

We'll encounter several different types of tests over the course of the JavaScript curriculum, but most will fall into the first two categories above, _unit_ and _integration_ tests. If you get stuck on a lab, it's a great idea to open up the file containing the test suite and take a look. Once again: all of the tests are just JavaScript code! You will likely see some concepts and code libraries that are unfamiliar at this point, but the basic tenets of the language hold everywhere. Don't worry too much about understanding every single line in the test suite; just use it as a secondary material to supplement the instructions in the README.

<p class='util--hide'>View <a href='https://learn.co/lessons/js-basics-intro-to-testing-readme'>Intro to Testing</a> on Learn.co and start learning to code for free.</p>
<p data-visibility='hidden'>PHRG Intro to Testing</p>