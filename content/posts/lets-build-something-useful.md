---
title: "Lets Build Something Useful!"
date: 2023-04-21T13:00:00+01:00
draft: false
---

So far, we have talked about, what neurodiversity is, what dyslexia is, and a bit of a side journey into my thoughts on how the written language plays a role in learning. And why that makes it hard for people with dyslexia to learn.

What can we do about it?

One thing which is often brought up is screen readers. Turning the written word into audible sound. 

This is normally done via, some sort of screen reading software which would need to be installed or activated to work. But I found a different solution. While scrolling through twitter, I discovered this tweet: [Technically it’s a web api!](https://twitter.com/trunarla/status/1597641480520503296). JavaScript has a built-in Web Speech API; part of which is called `SpeechSynthesisUtterance` which allows anyone with some HTML and JavaScript knowledge to create a player that can read a selected piece of text.

How does this look?

First, we start with the HTML. 

Technically all we need is a button, with a way of identifying it from other buttons.

```
<button id=”play-speech-synthesis-utterance”>play</button>
```

In this example I have used an ID to identify the button.

The JavaScript is a little bit more complicated, but not by much.

```
const play = document.getElementById(' play-speech-synthesis-utterance ');
const text = “Look Mum! I can Speak without moving my lips!”;
const utterance = new SpeechSynthesisUtterance(text);
play.addEventListener("click", function(){  
    window.speechSynthesis.speak(utterance);
});
```

In the above code we create 3 variable constants. variables in programming are just things which store values, these values can be anything, words, numbers, collections, or code. The constant part comes from math and just means the variable has a fixed value. 

The first `const play` stores a built-in function that gets and stores the element with the ID of `play-speech-synthesis-utterance` which if you haven’t noticed is the ID we gave the button above.

The next `const text` stores some words. `“Look Mum! I can Speak without moving my lips!”` this is what will be said out loud by the speech synthesiser IF everything works.

The last `const utterance` stores a new instance of the `SpeechSynthesisUtterance` function that takes in the `text` variable as a parameter. 

Parameters are sometimes required to make the code within the function they are placed work correctly. For instance in this case `text` is passed as a parameter to a new instance of  `SpeechSynthesisUtterance(text)` so that the function knows what to say when triggered.

The next 3 lines is a built in function, with another function inside of it, which is only run. When the first function is run.

The first function `play.addEventListener(“click”, )` is a built in function that is listening for some one to click on what is defined before the first dot(`.`) in this case `play` which we set to the button in the HTML.

The second function, is anonymous and its only purpose is to contain the code within it.

The line of code this function contains, is what makes the Speech Synthesiser Speak. To do this we first access the `window` model, then the `speechSynthesis` model, that contains the `speak` function. To get it to read our words, set in the `text` constant, we must pass it an instance of the `SpeechSynthesisUtterance` which we have already set and passed in the `text` constant too and stored as the `utterance` variable ` window.speechSynthesis.speak(utterance)`.

Bing, bang boom! When you click on the play button. It speaks!

This is a very simple example of how we can use it. With a little bit more tinkering. You can easily change what the button looks like depends on whether, it is speaking or not.

In fact you can find the code showing you how to do this on my [GitHub]( https://github.com/mejasonatkinson/playground-js-utterance/tree/main/projects/versions/simple). Or just look above in this blog. Because I have added it as an accessibility feature to my blog. 😊 <!-- use codepen -->

It is worth saying there is a lot you can do and explore with this Web API but at the moment it is not fully supported on all browsers. And different browsers have different quirky takes on how it works. But I for one think it’s a brilliant step in the right direction, in making things more accessible for all.

I have also coded, a more feature rich version of this which you can also find on my [GitHub]( https://github.com/mejasonatkinson/playground-js-utterance/tree/main/projects/versions/feature-rich). <!-- use codepen -->

---

Quote of the week - "Coding like poetry should be short and concise"

---

### Resources:

- [Technically it’s a web api!](https://twitter.com/trunarla/status/1597641480520503296)
- [SpeechSynthesisUtterance mdn web docs](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesisUtterance)
- [Experimenting With speechSynthesis](https://www.smashingmagazine.com/2017/02/experimenting-with-speechsynthesis/)


*I have tried to research this post the best I can. IF there is anything wrong, please let me know and I will update and make clear the changes made to this post*
