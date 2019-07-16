![Demo gif](https://raw.githubusercontent.com/ianisborn/simple-messages/master/demo.gif)

## README
This is a really simple page that uses PubNub to send messages between two users, Alice and Bob.

## Setup
* You need a modern browser (this project uses ES6). [Firefox](https://www.mozilla.org/en-US/firefox/) is good.

#### Configuration
1. Open up the page with your browser. You can do this by running `open index.html` in a terminal.

#### Testing
There are no tests for this app. If I wanted to test it, I would use a tool like [Jest](https://jestjs.io/) and test the following:
* Does the app subscribe and publish to PubNub? I would mock out the `PubNub` global and make sure that it does.
* Does sending a message create a `sent` message in the sender's messages with the appropriate text?
* Does receiving a message create a `received` message in the recipient's messages with the appropriate text?

An integration test might be overkill for this app. However, PubNub is a pretty reliable service to use in an integration testing context, so I don't think it would be a terrible idea (just more work than is necessary).

#### Domain
The Message object has this structure:
```
{
  "author": "Alice",
  "recipient": "Bob",
  "text": "This is a message body 🎈"
}
```

## Reflection

I think I was able to satisfy the requirements of the project: make an app that sends messages between two users. I spent about an hour on the code for the app and something like 15 minutes styling it.

Design decisions I made:
* I ended up checking in a pair of PubNub keys into the repo because they're demo keys and present zero risk if someone gets ahold of them. It would be better to use environment variables, though.
* I used PubNub because I have used it before and knew it could be used to send messages between two clients. It can send arbitrary JSON objects, so it can encode data like who sent the message. It is fast and reliable. I don't think I've ever seen it go down.
* I inlined all my CSS, HTML and JS because the requirements for this project are simple so my code was still easy to reason about the whole time.
* I used ES6 since it's really useful for doing things like destructuring message objects.
* I hard-coded the users (Alice and Bob) in HTML, but my javascript code is somewhat abstracted and I think it could support arbitrary users without too much effort.
* I kept my styling code pretty simple and only tested the app in Firefox. I would use a [CSS reset](https://bitsofco.de/a-look-at-css-resets-in-2018/) to keep styles more consistent between browsers were that a requirement.

Future work:
* Would be nice to use something like [dotenv](https://www.npmjs.com/package/dotenv) to set PubNub keys.
* Split out JS, HTML and CSS into their own files.
* Abstract out the idea of users so that they're not hardcoded.
* Use [Lodash](http://lodash.com/) to do things like iterate over DOM elements.
* If the frontend needed to become more complicated I would probably add [React](https://reactjs.org/).
* If I needed cross-browser compatibility I would use [Babel](https://babeljs.io/).
* If I had to add JS packages (like Lodash or React), I would use [Webpack](https://webpack.js.org/) to build a JS bundle.
* If I needed to manage a bunch of JS modules, I would use [Yarn](https://yarnpkg.com/en/) to do so.
