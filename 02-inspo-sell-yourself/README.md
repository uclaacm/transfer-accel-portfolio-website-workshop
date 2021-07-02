# ~ inspo interlude ~ and selling yourself

This is a (shorter) portion of the workshop focused on two things:

* showcasing some ~ very cool ~ portfolio websites
* some ~ unsolicited ~ tips on selling yourself!

Let's get started :)

## table of contents

* [why a portfolio?](#why-a-portfolio)
* [what you'll learn](#what-youll-learn)
* [some ~ cool peeps ~](#some--cool-peeps-)
* [tips! and on selling yourself!](#tips-and-on-selling-yourself)
  * [some ~ key ~ web design terms and ideas](#some--key--web-design-terms-and-ideas)
    * [responsiveness](#responsiveness)
    * [above-the-fold](#above-the-fold)
    * [web accessibility](#web-accessibility)
  * [on selling yourself](#on-selling-yourself)
* [Licensing](#licensing)

## why a portfolio?

The best way to learn web development, plain and simple, is to practice. So, let's get to it!

We'll hit two birds with one stone by making a personal portfolio website! These websites are very popular with software engineers, data scientists, product designers, UI/UX designers, and lots of other people involved in tech. It's basically a walking résumé, except *you* get to control **every aspect of it!**

In this doc, we'll outline some suggestions on how you can use what you've learned to make your own personal website. However, you definitely don't *need* to follow any of these steps! In a later workshop, we'll also teach you how to deploy your personal website with GitHub Pages, so anybody can see it!

## what you'll learn

At the end of the day, your personal website is **yours**. We're not going to tell you what has to be on it, what doesn't, or what looks bad or good. **You decide!**

Like the rest of this workshop, the onus is on you to practice what you've learned, and put your best foot out there! That being said, here are some common things that you'll probably end up practicing by making your website:

* general basic understanding of HTML & CSS
* choosing an overall design scheme (with colors, fonts, etc.)
* adding color to your website with `color`, `background-color`, `border`, and other properties
* using `margin`, `padding`, `position`, CSS Grid, or Flexbox to make the spacing on your site *just right!*
* using the `<a>` tag to link to your GitHub, LinkedIn, email, etc.
* using the `<ul>`, `<ol>`, and `<li>` tags to create lists of content (like all your awesome skills!)
* creating complex layouts with flexbox or CSS grid
* creating your own visual components using a combination of HTML and CSS (like a card, tag, or navbar)
* use the right HTML tags to convey your page structure, even to those who use screen readers

Note that using JS is optional: some people use it, and some don't. Do what feels right for you!

We also want you to get used to using `git` and GitHub. We'll talk a bit about these tools in a later workshop, but we'll be a bit brief (there are many, many `git` and GitHub tutorials out there).

## some ~ cool peeps ~

Very quickly, let's run through some examples of cool designs for personal websites (though to be honest, this is also just a chance for Matt to show you some cool people he knows).

Many people choose minimal websites that are content-focused and driven. Here are a few examples:

* [https://krashanoff.com/](https://krashanoff.com/) - Leo's website! It gives you just enough information about him, and a unique feel of what he's like. (Leo helped write the original workshop materials)
* [https://marceloneil.com/](https://marceloneil.com/) - Marcel is one of Matt's high school friends who does amazing stuff with computers, and his website is dead-simple but cool. It's actually a [Hugo](https://gohugo.io/) theme, but you can probably implement it yourself!
* [https://kandrewz.github.io/](https://kandrewz.github.io/) - Andrew is a CS student at UCLA, and also makes very cool interactive stories for Daily Bruin. His website is simple, easy to navigate, and elegant.
* [https://neerajsamtani.me/](https://neerajsamtani.me/) - Neeraj is one of the first people that Matt ever met at UCLA, and is just as awesome today as he was on day 1. His website is simple, but still conveys a lot about his personality, his design choices, and what he does!
* [https://jasonjewik.github.io/](https://jasonjewik.github.io/) - ACM AI's very own superstar Jason Jewik! His website puts all of the important content front-and-center, and you know he's hip with the kids because he uses emojis 👀.
* [https://emmycao.com/](https://emmycao.com/) - Emmy is a previous director of Creative Labs at UCLA, and also one of the coolest designers we know (and she can tell you a lot about Maryland). We think she does an especially great job at using color, spacing, and fonts to create a very visually cohesive website.
* [https://matthewwang.me/](https://matthewwang.me/) - ew, who's this?

These next three are all more blog-focused, but still have good lessons to learn from:

* [https://markdotto.com/](https://markdotto.com/) - Mark Otto is one of the founders of Bootstrap, probably the most popular CSS framework to exist. His website is simple, but great.
* [https://thume.ca/](https://thume.ca/) - Tristan Hume is a Canadian software engineer who works at Jane Street, and writes some of the most interesting blog posts that Matt reads. His website is simple, with nothing flasy, but easy to navigate.
* [https://andrewkelley.me/](https://andrewkelley.me/) - Andrew Kelley is the main developer behind Zig, a new programming language with a large online following and lots of cool features. Note that his website is similarly minimal with Tristan's.

We think sites like the ones we showed above are a great place to start, and probably what you should focus on for this project. The best sites don't necessarily have to be overly complex: minimal but clean is much better than flashy and messy. In particular, you'll notice the phrase "simple and easy to navigate" appears a few times: on a portfolio page, that's probably the most important thing (other than you 😉).

But for fun, let's see a bit more.

Sometimes, you can add small features to make your website just a bit more distinct than others. Here are a few examples:

* [https://carolchen.me/](https://carolchen.me/) - Carol is one of the smartest software engineers that Matt has ever met, and her website shows it! Two features that he loves are the randomization of certain elements on load, and the slider that lets users pick how much information they want.
* [https://sindresorhus.com/](https://sindresorhus.com/) - Sindre Sorhus is one of GitHub's most famous celebrities, creating hundreds of popular open-source packages (mostly for Node.js and Swift). His website gives you a taste of everything he's done, including live (JS) metrics on what he does - you can stalk him realtime!
* [https://nickelder.ca/](https://nickelder.ca/) - Nick was one of Matt's web development mentors in high school. His website just gives you an amazingly clean feeling, one that screams meticulousness and professionalism.
* [https://bryanpan.co/](https://bryanpan.co/) - Bryan is another outgoing lead of Creative Labs and their current tech director; his website feels like you're watching art unfold in front of you, especially with this SVG animations!
* [http://mihirmathur.com/](http://mihirmathur.com/) - Mihir was a previous president of ACM @ UCLA! While his website has the general flow and layout of most websites, there are so many design microinteractions that just make his site pleasant to use.

And sometimes, you can go flashy. Here are some websites that do a lot, and say a lot. We will say, all of these websites have benefits and tradeoffs: as we mentioned earlier, flashy doesn't always mean great (and in particular, accessible):

* [https://lam.io/](https://lam.io/) - Derek was also one of Matt's web development mentors in high school. The amount of unique design customization on this website, down to writing his own sharding library, is insane. This is the kind of website that you don't ever really forget.
* [https://jgthms.com/](https://jgthms.com/) - Jeremy Thomas is the creator of [Bulma](https://bulma.io/), one of the web's most popular CSS frameworks. So it's no doubt that he has an enticing website, with a sense of vibrancy and dynamism that makes you want to hire him. Oh, and a light mode/dark mode toggle!
* [https://www.strml.net/](https://www.strml.net/) - Samuel Reed's website went viral on Twitter, Reddit, and HackerNews, and for good reason. He literally constructs his website, right in front of you. By far one of the most innovative websites we've seen.
* [http://www.rleonardi.com/interactive-resume/](http://www.rleonardi.com/interactive-resume/) - Okay, Robby Leonardi literally made his website an interactive game. He wins.

## tips! and on selling yourself!

You're cool. And we want to show that off to people! Here's some unsolicited advice on how you can do just that.

### some ~ key ~ web design terms and ideas

We'll quickly mention three terms: **responsiveness**, **above-the-fold**, and a quick mention of **web accessibility**.

#### responsiveness

**Responsiveness** typically refers to how your website deals with different **viewports**, a fancy name for screen sizes. In particular, does your website work well on a smartphone? On a tablet? For a small laptop, or a huge monitor? Many websites are only every developed on a computer, and nobody tests them on phones - even though mobile is over 50% of client internet access!

To make your website more responsive, we suggest:

* testing frequently on mobile! you can mimic this by resizing your browser window or using your devtools; but, at the end of the day, nothing beats testing on your phone :)
* designing with mobile in mind - does somebody need to click a button many times? how large is the text? do you need to frequently use a keyboard?

#### above-the-fold

The **above-the-fold** refers to what the user sees on their screen without scrolling; it comes from newsprint, where it represented the articles you could see *above* the *fold* of the paper.

The above-the-fold is a really key part of web development, since it informs the user if they should keep reading or not. Some questions you might want to think about:

* is there a visual hierarchy to the page? a large title to read, then smaller subtitles? or just a jumble of text and images?
* is it clear what the user should do first after seeing the site? ex a button to click, a page to visit, or to scroll down for more?
* how much information is on the page at once? is it overwhelming?
* does it take a long time to load? would the user be waiting for a bit?

TODO - examples?

#### web accessibility

**Web accessibility** is a really important but often undervalued part of the web. Many elements of websites - from colors to typography to images to videos and animations - can actually be exclusive to all sorts of people!

This is a very complicated endeavour, and we can't do it justice in half an hour. However, some questions and thoughts we want to place in your head:

* blind and visually impaired surfers use something called a **screenreader** to read out the elements of a page.
  * do your images have *good* `alt` tags? would they describe the purpose of the image if read out loud?
  * do your headings make *semantic* sense? screenreaders often use heading structure to generate a faux "table of contents" for users.
  * is your link text descriptive? links that say "here" don't tell the end user what the link is!
* **colorblindness** is not uncommon.
  * is there ample color contrast for visual elements of your site? the [WCAG color tester](https://webaim.org/resources/contrastchecker/) is one great resource!
  * are there alternative indicators for visual elements that rely on color? for example "click on the red button"?
* rapid motion and shifting lights can induce motion sickness or epilepsy.
  * ideally, avoid autoplaying videos - get the user's consent!
  * can the user disable animations? do you respect the [`prefers-reduced-motion`](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion) media feature?
  * do you warn the user before fast animations or flashing lights occur?

Of course, we can't encapsulate the entire effect that disability has on end users. Some further reading suggestions:

* a friend of ACM, Karen Yi, did a [guest lecture on accessibility for us last year](https://github.com/uclaacm/learning-lab-crash-course-su20/tree/main/13-accessibility)!
* the Mozilla Developer Network has a great [set of tutorials on accessibility](https://developer.mozilla.org/en-US/docs/Web/Accessibility)
* [Mismatch by Kat Holmes](https://mitpress.mit.edu/books/mismatch) is a great primer on inclusive design!

### on selling yourself

TODO

## Licensing

The contents of this repository are dual-licensed under the [MIT License](https://github.com/uclaacm/transfer-accel-portfolio-website-workshop/blob/main/LICENSE) and the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/); feel free to use whichever license suits your purpose better.

I'd love to hear if you found this helpful, or if you have any suggestions! Please send me an email at [matt@matthewwang.me](mailto:matt@matthewwang.me).
