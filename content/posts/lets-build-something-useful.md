---
title: "Lets Build Something Useful!"
date: 2023-04-21T13:00:00+01:00
draft: false
---

So far, I have talked about what neurodiversity is, what dyslexia is and a bit of a side journey into my thoughts on how the english alphabetical language plays a role in learning and why that makes it hard for people with dyslexia to learn.

What can we do about it?

One thing which is often brought up is screen readers.

This is normally done via some sort of screen reading software. Which would need to be installed or activated to work but I found a different solution! While scrolling through twitter I saw this tweet: [Technically it’s a web api!](https://twitter.com/trunarla/status/1597641480520503296) by [mewtru](https://twitter.com/trunarla). JavaScript has a built-in Web Speech API; part of which is called `SpeechSynthesisUtterance` which allows anyone with some HTML and JavaScript knowledge to create a player that can read a selected piece of text.

How does this work?

First, we start with the HTML. 

```
<button id="play-speech-synthesis-utterance">play</button>
```

Technically all we need is a button, with a way of identifying it from other buttons. In this example I have used an ID to identify the button.

The JavaScript is a little bit more complicated, but not by much.

```
const play = document.getElementById('play-speech-synthesis-utterance');
const text = "Look Mum! I can Speak without moving my lips!";
const utterance = new SpeechSynthesisUtterance(text);
play.addEventListener("click", function(){  
    window.speechSynthesis.speak(utterance);
});
```

In the above code we create 3 variable constants. Variables in programming are just things which store values, these values can be anything words, numbers, collections, or code. The constant part comes from math and just means the variable has a fixed value. 

The first `const play` stores a built-in function that gets and stores the element with the ID of `play-speech-synthesis-utterance` which if you haven’t noticed is the ID we gave the button above.

The next `const text` stores some words: `"Look Mum! I can Speak without moving my lips!"`. This is what will be said out loud by the speech synthesiser IF everything works.

The last `const utterance` stores a new instance of the `SpeechSynthesisUtterance` function (which is part of the web speech API) and takes in the `text` variable as a parameter. 

Parameters are sometimes required to make the code within the function they are placed work correctly. For instance in this case `text` is passed as a parameter to a new instance of `SpeechSynthesisUtterance()` so that the function knows what to say when triggered.

The next 3 lines is a built in function, with another function inside of it, which is only run, when the first function is run.

The first function `play.addEventListener("click", )` is a built in function that is listening for some one to click on what is defined before the first dot(`.`) in this case `play` which we set to the button in the HTML.

The second function, is anonymous and its only purpose is to contain the code within it.

The line of code this function contains, is what makes the Speech Synthesiser Speak. To do this we first access the `window` model, then the `speechSynthesis` model, that contains the `speak` function. 

To get it to read our words, set in the `text` constant, we must pass it an instance of the `SpeechSynthesisUtterance` which we have already set and passed in the `text` constant and stored as the `utterance` variable `window.speechSynthesis.speak(utterance)`.

Bing, bang boom! When you click on the play button. It speaks!

This is a very simple example of how we can use it. With a little bit more tinkering, you can easily change what the button looks like depending on whether it is speaking or not. and much much more.

You can find the code showing you how to do this on my [codepen](https://codepen.io/mejasonatkinson/pen/VwEPaEd) Or just look above in this blog because I have added it as an accessibility feature here. 😊 

It is worth saying there is a lot you can do and explore with this Web API but at the moment it is not fully supported on all browsers and different browsers have different quirky takes on how it works. But I for one think it’s a brilliant step in the right direction, in making things more accessible for all.

I have also coded a more feature rich version of this which you can find on my [codepen](https://codepen.io/mejasonatkinson/pen/poxRyez) as well as a selection of other variants I have created.

- [Simple, Speech Synthesiser](https://codepen.io/mejasonatkinson/pen/MWPJybW) this is the version being used on this blog.
- [Multi-Input, Simple, Speech Synthesiser (1-to-All)](https://codepen.io/mejasonatkinson/pen/oNaBxME)
- [Multi-Input, Simple, Speech Synthesiser (1-for-Each)](https://codepen.io/mejasonatkinson/pen/GRYrZXw)
- [List of Title Speech Synthesiser Voices](https://codepen.io/mejasonatkinson/pen/WNaRpKy)
- A Web Component version is in the works.

I hope you found this useful. 😊 

<!-- https://codepen.io/collection/ZMoemG -->

---

"Coding like poetry should be short and concise"

---

### Resources:

- [Technically it’s a web api!](https://twitter.com/trunarla/status/1597641480520503296)
- [SpeechSynthesisUtterance mdn web docs](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesisUtterance)
- [Experimenting With speechSynthesis](https://www.smashingmagazine.com/2017/02/experimenting-with-speechsynthesis/)

<!-- posted -->

<!-- 
LinkedIn
Let’s Build Something Useful! Building a Speech synthesiser, using a JavaScript web API. 
Read more about it here: https://blog.jasonatkinson.co.uk/posts/lets-build-something-useful/ 
-->

<!-- 
Twitter
Let’s Build Something Useful! Building a Speech synthesiser, using a JavaScript web API. 
Read more about it here: https://blog.jasonatkinson.co.uk/posts/lets-build-something-useful/ 
-->