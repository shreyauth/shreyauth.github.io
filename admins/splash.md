# Splash release guide

We offer you full control over how your splash releases function, and it can get a bit daunting. In this guide I'll explain everything you need to know about setting up a splash release exactly as you'd like it.

Firstly, let me explain how splash releases work. You set a number range from 0-`x`, and set a frequency of requests (1 request every `y` seconds). When you create a release, we randomly select a number from 0-`x` and save it as the "correct number". When a user is on the splash page waiting to purchase, their browser will make a request every `y` seconds. If they make a request, and the splash page is open, a random number between 0-`x` will be picked. If the random number picked is the "correct number", they're shown the purchase page and are prompted to check out.

All of this happens completely behind the scenes, and neither the user or the user's browser is aware of what's going on.

### Parameters

#### Splash open by default

This parameter controls whether the splash is open or not. If set to `no`, users that go to purchase will be shown the splash page but will not be let in. As soon as you set this to `yes`, requests that users make will begin "guessing" for the correct number.

We recommend utilizing [google analytics](http://analytics.google.com/) to measure how many users are on your splash page in real time. Set your tracking ID in your site settings.

#### Time between guesses

This parameter sets the time (in seconds) between user requests to the splash page. The lower the number, the more frequent user requests will be.

#### Largest guess number

This parameter sets the largest possible "guess", and controls how many requests a user will make before eventually getting the purchase page.

---

### Tie it all in

As a general rule of thumb, the maximum amount of time (in seconds) a single user will wait in the splash page can be calculated by **time between guesses** x **largest guess number**. If users make requests every 2 seconds, and the largest guess number is 25, it'll take users a maximum of **50** seconds to get through the splash page. We recommend using a lower guess rate, and a larger maximum guess number when deciding how lengthy you want to make your splash page.

---

If you have feedback about this guide or any other questions, feel free to [contact us](https://shreyauth.com/contact)
