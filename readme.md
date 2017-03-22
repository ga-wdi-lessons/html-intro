# HTML Review


### Building a website

All you need to build a website is a computer, and two pieces of software: a web browser (Chrome, Safari, Firefox, Internet Explorer), and a text editor.

### Text editors

When I started, my text editor was TextEdit, which is in the Applications folder of any Mac. The Windows equivalent is NotePad.

##### Go ahead and open TextEdit on your Mac, or Notepad on your PC. On a Mac, it's inside your Applications folder. You can also use Spotlight to find it.

The text editor you use doesn't matter. The only thing that matters is that it has to be *plain text*.

A text editor is *not* plain text if it secretly hides a bunch of code inside the files you make. This is how Word records whether text should be bold, italic, red, blue, and so on. This is called *rich text*.

A text editor is *plain text* if, when you look at a file, you see *everything* inside it -- no hidden code.

For example, if I create and save a blank Word document, it's actually about 20 kilobytes. If I create and save a blank document in TextEdit, it's 0 bytes. If I look at a Word document in TextEdit, I see a heinous mess, which is all the hidden code.

##### Please go to `File > Preferences` in TextEdit. In the `New Document` tab, make sure `Plain Text` is selected at the top instead of `Rich Text`. Also, un-select all of the `Options` at the bottom. On the `Open and Save` tab, select `Display HTML files as HTML code instead of formatted text`. Then, quit and re-open TextEdit.

### Now we're ready to learn HTML

You may think you know HTML, but you're probably doing it *wrong*. HTML done right makes creating a website a breeze. HTML done wrong means you do lots and lots of deleting, writing a little bit, and deleting again.

Let's say you want to make a webpage of your favorite jokes. We're going to do this using **fake HTML**. (Don't bother writing it down!)

```
What does a cloud wear on its butt?
Thunderpants.

What do you call a cow with no legs?
Ground beef.
```

You want the jokes' set-ups to attract attention, so let's make them orange:

```html
<orange>What does a cloud wear on its butt?</orange>
Thunderpants.

<orange>What do you call a cow with no legs?</orange>
Ground beef.
```

This is what HTML looks like. You take some text, and at each end of it you put **tags**. The tag at the end -- the closing tag -- looks like the tag at the start -- the open tag -- but with a slash in it.

Two tags make one **element**.

Elements have to **nest**. That is, every element has to be completely inside another element (like those Russian dolls).

So if I wanted to make the jokes' set-ups orange and underlined, I might do this:

```html
<orange><underline>What does a cloud wear on its butt?</underline></orange>
```

However, this would be **wrong**:

```html
<orange><underline>What does a cloud wear on its butt?</orange></underline>
```

Now the `underline` element ends sort-of inside the `orange` element and also sort-of outside it.
Nested HTML Elements must be **completely** enclosed by their **parent** element.

So now our whole webpage looks like this:

```html
<orange><underline>What does a cloud wear on its butt?</underline></orange>
Thunderpants.

<orange><underline>What do you call a cow with no legs?</underline></orange>
Ground beef.
```

This looks pretty good! Looking at it, you can tell what's going on.

##### Let's say instead of 2 jokes, you have 100 jokes. Then you decide that instead of orange and underlined, you want the set-ups to be green and underlined. What do I have to do?
##### To give you a hint: how many times do I have to do it?

Wouldn't it be nice if we could just make a rule that says, "OK, I want every set-up to be orange and underlined." Then, if we want to change all the set-ups, we can just change that rule! One thing to change, instead of 100.

## We do this using a language *different* from HTML called **CSS**:

```html
<div class="setup">What does a cloud wear on its butt?</div>
Thunderpants.

<div class="setup">What do you call a cow with no legs?</div>
Ground beef.
```

```css
.setup{
  color: green;
  text-decoration:underline;
}
```

Here, we're using actual HTML. `div` stands for `division`, as in, "a chunk of a webpage."

The tags look a little different. I've given the `div` elements an **attribute**.

##### What is an 'attribute' of a person?

An attribute of an element is a small modification to it. In this case, we're giving the divs a "class", which is like a "type". *(Note that attributes are only in the start tag, not the close tag.)*

In my CSS, the `.` before `setup` is a **selector**. `.setup` means "select every element with a `class` of `setup`, and then do something to it".

The "somethings" we're "doing" here is changing the color to green, and decorating the text with an underline.

This is how all CSS looks: you have a selector, followed by the **properties** you want to change and the **values** you want to give them.

There are many selectors. For example, if I wanted to just select all `div` elements, I would write `div` without the `.`. If I forget the `.` before `setup`, it would mean "select all `setup` elements", and `setup` isn't a kind of element.

Now, if I want to change the color of all my setups, I just need to change one line of code!

### Here's an example of bad HTML and CSS:

```html
<div class="green">What does a cloud wear on its butt?</div>
Thunderpants.

<div class="green">What do you call a cow with no legs?</div>
Ground beef.
```
```css
.green{
  color: green;
}
```

##### Why is this "bad" HTML and CSS?

If I want to change the color of the setups, I can still just change one line of code. But now I have something like this:

```css
.green{
  color: red;
}
```

That is, the things with the `class` of `green` are now `red`. That's really confusing for web designers looking at your code -- including you!

## This introduces the separation of semantics and style

This is one of the most important rule of web design: *you should never put anything indicative of style in your HTML*. That is, you should never give elements classes of `centered` or `big` or `pink`. Instead, you should give them classes like `header` or `paragraph` or `punchline`.

This is called **semantic naming**: naming things according to their *function*, rather than how you want them to look. This is because *form follows function*: the way you want elements to look is *always* based on the purpose of the element on the page.

HTML is usually written first in one file, and then its CSS is written in another. *If you write HTML perfectly, you'll never need to touch it once you start writing CSS.*

For example, here's semantically-named, *good* HTML:

```html
<div class="page">
  <div class="header">Robin's Favorite Jokes</div>

  <div class="joke">
    <div class="setup">What does a cloud wear on its butt?</div>
    <div class="punchline">Thunderpants.</div>
  </div>

  <div class="joke">
    <div class="setup">What do you call a cow with no legs?</div>
    <div class="punchline">Ground beef.</div>
  </div>
</div>
```

This brings up another way of making your code good and easy-to-read:

## Indent. Indent. Indent.

The way the code above has been indented, it's really easy to see which elements are inside which other elements. Indentation is a visual cue.

**This is really important.** This is the easiest, simplest way to make your code look good to everyone else. Indent. It seems silly, but it can make all the difference between someone hiring you and someone tossing your resume in the trash. If they can't read your code, they can't tell whether you're any good at what you do, and won't hire you.

## Writing `class` all the time gets old

This is why HTML comes built-in with many elements beyond just `div` that have implied classes: they tell you the purpose *of whatever's inside them* without you needing to write `class` everywhere.

For instance, the humble `<p>` tag. `p` stands for "paragraph". This might be a good substitute in place of `<div class="punchline">`. It still makes semantic sense, and it's a lot easier to write.

There are over 130 HTML elements that come standard on every web browser. Don't worry -- you'll use about 20 of them for 90% of things, the same way you use the same 100 words for 90% of conversations.

### HTML also comes built-in with special characters

A **special character** is a character other than `a` through `z`, `0` through `9`, and the most common punctuation marks, like comma, period, and hyphen.

One example is the trademark "tm" symbol. To include it on a webpage, you'd write `&trade;`.

This is because different computers have different ways of translating 0s and 1s into text. On Macs, the "tm" symbol might be a certain sequence of 0s and 1s. On PCs, it might be another. Writing `&trade;` tells a web browser, "Just show a trademark symbol with whatever sequence of 0s and 1s you want."

##### Have you ever seen a Microsoft Word document where the quotation marks or apostrophes were all replaced with a few characters of gibberish?

This is an example of an **encoding error**: different computers recording quotation marks or apostrophes as different sequences of 0s and 1s.

Regular straight quotes, `"`, are a standard character. But curved quotes -- which Word uses -- are a special character (hence why I can't include them in these notes). To use them on a webpage, you'd write `&ldquo;` or `&rdquo;`.

Special characters all have the same form: an ampersand, followed by an abbreviation, followed by a semicolon.

Interestingly, ampersand is also a special character. This is because web browsers always think ampersands indicate a special character, so if you just want to display an ampersand, you have to tell it that you just want to *show* an ampersand, not actually use it to create another special character. It's written as `&amp;`.

Same for the angle brackets used in HTML. A web browser thinks anything inside angle brackets is an HTML tag. To have the browser show angle brackets instead of reading them as HTML, you'd write `&lt;` (less than) and `&gt;` (greater than).

One thing you'll see on many pages is a...

## Comment

A comment is a piece of code that is *ignored* by the browser. It's still in the code, it just doesn't do anything.

```html
<!-- Comments look like this. -->
```

For a great example, go to http://www.theoatmeal.com, and look at the source code. In Chrome, you can do this by pressing `Command + Option + U`, or going to `View > Developer > View Source`.

##### What's the purpose of comments?

- They're often used to leave notes to other developers (including jokes), and yourself
- You can "comment out" pieces of code. This lets you test different pieces of code without needing to delete and copy and paste things.
- However, you should **always** get rid of commented out code before deploying it online

## Common HTML Tags

Remember: an element's name is usually an abbreviation. Click the blue circle on the bottom-right to scramble the items.

- `<a>`: One of my least favorite tags, because an "anchor" is what we always think of as a "link" -- and there's a `<link>` that does something completely unrelated. Remember: **an anchor is a link**. To make an anchor actually go somewhere when you click on it, you give it an attribute called `href` (which stands for *hypertext reference*, which isn't important). For example: `<a href="http://google.com">Google</a>`

- `<img />`: Like `<a>`, an image also needs an attribute in order to work. This attribute is `src`, as in "source":
```
<img src="http://images.com/image.jpg" alt="This is an image" />
```
The `alt` attribute is what text is shown when the image can't be seen by the user: if the image doesn't load, or if the user is blind. For any website owned or associated with the government, this is **required by law** as a result of the Americans With Disabilities act, even though most "seeing" people will never know it's there.

`<img />` is an example of a **self-closing tag**. There are only a couple of these. They're elements that don't have any text content, so there's not any point in having an open *and* a close tag.

- `<h1>`: The `h` stands for "headline", which is a bit of text that introduces other text. There's `<h1>` through `<h6>`, which the numbers indicating the level of "importance". For example:

```html
<h1>The US Constitution</h1>
  <h2>Article I</h2>
    <h3>Section A</h3>
    <h3>Section B</h3>
  <h2>Article II</h2>
    <h3>Section A</h3>
    <h3>Section B</h3>
      <h4>Subsection 1</h4>
        <h5>Clause i</h5>
          <h6>Subclause a</h6>
```

Generally, a page will have only one `<h1>` because that's the *most important* headline, meaning it should introduce the rest of the page.

Don't skip from `<h1>` to `<h6>`. Go in order.

- In web design, a **block** element is an element that occupies its own main "chunk" of the page. The other **block elements** include `<p>`, `<div>`, and `<h1>` through `<h6>`.

Elements that go inside blocks and do not take up space across the entire page are called **inline**. Other **inline elements** include `<em>`, `<strong>`, and `<a>`.

- `<em>` and `<strong>`: The difference is that things that are "emphasized" aren't necessarily loud (or "strong"), and things that are strong are not necessarily emphasized.

- `<ul>` and `<ol>`:

##### What's the difference in the *meaning* of these two lists?

```
My favorite things:
- Whiskers on kittens
- Brown paper packages
- Schnitzel with noodles
```
```
My favorite things:
1. Whiskers on kittens
2. Brown paper packages
3. Schnitzel with noodles
```

The second list implies that "whiskers on kittens" are *more* my favorite thing than packages and noodles, whereas the first list implies they have equal weight. This is the difference between an **ordered** and an **unordered** list.

Lists can only contain **list items**. That is, this is *good*:
```html
<h1>My favorite things</h1>
<ul>
  <li>Whiskers on kittens</li>
  <li>Brown paper packages</li>
  <li>Schnitzel with noodles</li>
</ul>
```

This is *bad*:
```html
<ul>
  <h1>My favorite things</h1>
  <li>Whiskerse on kittens</li>
  <li>Brown paper packages</li>
  <li>Schnitzel with noodles</li>
</ul>
```

## HTML stands for Hypertext Markup Language

##### If a teacher "marks up" a paper you wrote, what does that mean?

It might mean they're adding comments, crossing things out, writing suggestions... They're not changing the words you wrote; they're *adding a layer of meaning on top of them*. This is the purpose of HTML: to take words, and add a layer of meaning on top of them.

Writing HTML is more like writing a script: taking a bunch of dialogue and splitting it up into lines, with actor suggestions, like "This is delivered off-stage", "This is happy", and so on.

HTML's purpose is to tell you the **function** of words, also known as words' **semantic value**.

When writing HTML, *think only of the semantics*. If you find yourself thinking, "This should be centered", "This should be red", "I'll put a sweet background image here"... Ignore those thoughts! Just think about what the words *mean*.

This is why HTML is usually written first in one file, and then its CSS is written in another.

Remember: *If you write HTML perfectly, you'll never need to touch it once you start writing CSS.*

# Structure of a webpage

## The Joke page, in good HTML
```html
<header>
  <h1>Robin's Favorite Jokes</h1>
</header>
<main>
  <ul class="jokes">
    <li>
      <h2>What does a cloud wear on its butt?</h2>
      <p>Thunderpants.</p>
    </li>

    <li>
      <h2>What do you call a cow with no legs?</h2>
      <p>Ground beef.</p>
    </li>
  </ul>
</main>
<footer>
  <p><a href="mailto:hello@robertakarobin.com">Contact me!</a></p>
</footer>
```

Note that I've separated things into `<header>`, `<main>`, and `<footer>`. The `main` stands for "main content". Most webpages are split into these three sections.

This *looks* pretty good. But we can actually...

## Check to make sure the HTML is good

`http://w3.validator.org` lets you paste in HTML, and tells you what's wrong with it. If we paste in the code above, it yells at us about a lot of things.

The problem is there are certain elements *every* webpage needs to have. The complete version of my joke page would look like this:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Sweet Joke Page</title>
  </head>
  <body>
    <header>
      <h1>Robin's Favorite Jokes</h1>
    </header>
    <main>
      <ul class="jokes">
        <li>
          <h2>What does a cloud wear on its butt?</h2>
          <p>Thunderpants.</p>
        </li>
        <li>
          <h2>What do you call a cow with no legs?</h2>
          <p>Ground beef.</p>
        </li>
      </ul>
    </main>
    <footer>
      <p><a href="mailto:hello@robertakarobin.com">Contact me!</a></p>
    </footer>
  </body>
</html>
```

- `<!DOCTYPE html>`: The first line on every single webpage. This really bothers me. It doesn't look like other tags. You don't need to close it. Its job is to tell the browser, "Hey, everything after this is HTML." Aside from knowing that you need to have this as the first line of every webpage, you can ignore it.

- `<html>`: The *second* line on every webpage. `</html>` is the *last* line on every webpage.

- `<head>`: Every webpage has two main "body parts": the `<head>` and the `<body>`. The `head` contains **meta-data**: that is, data the user won't actually see in the webpage. There are a couple different things we can put in here, but for now we'll stick with...

- `<title>`: The name of the webpage as it appears at the top of the window, or in your bookmarks bar, or history, or in Google searches. It's in the `<head>` because it *doesn't actually show up on the webpage itself*.

- `<body>`: Where all everything you "see" lives.

## You must have exactly one of each of these elements on every webpage.

##### Quick review: What's the difference between `<head>`, `<h1>` (headline), and `<header>`?

# Paths and external files

You can make a complete webpage without being connected to the Internet. First, open a new plain text file, and paste into it the source of that Will Smith page:

https://github.com/ga-dc/belair_biography/blob/master/index.html

Then, save your file to your Desktop (or somewhere) as "belair.html".

Finally, drag and drop that `belair.html` file onto your web browser's icon.

It works! Sort of.

##### What isn't working?
- The image is broken
- The styles aren't working

But note that there are still some styles -- the `<h1>` is big and the `<strong>` is bold. These is caused by the browser's **default stylesheet**. Google made up a stylesheet for Chrome to use when you, the web designer, doesn't give it a different one to use. Microsoft did the same for Internet Explorer.

## Default stylesheets are all different.

Internet Explorer will make things look slightly different from Chrome. This is why you *can't rely on default stylesheets*. Any CSS you write will override the browser's default stylesheet. If you want things that are `<strong>` to show up bold, you'd better include that in your CSS.

Web designers often use **CSS normalizers** to completely remove the effects of the default stylesheet. A popular one is `normalize.css`.

So how can I get the styles back?

## There are three ways to write styles

### The first is to give an element a `style` attribute

```html
<div style="color: red;">What does a cloud wear on its butt?</div>
```

This is just taking some CSS and putting it in the HTML.

##### Why might this be discouraged?

It's an awful lot like putting `<orange>` in your HTML: it puts style and semantics in the same place and makes your code hard to read.

### The second is to use an inline stylesheet

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Sweet Joke Page</title>
    <style>
      h2{
        color: red;
        text-decoration: underline;
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Robin's Favorite Jokes</h1>
    </header>
    <main>
      <ul class="jokes">
        <li>
          <h2>What does a cloud wear on its butt?</h2>
          <p>Thunderpants.</p>
        </li>
        <li>
          <h2>What do you call a cow with no legs?</h2>
          <p>Ground beef.</p>
        </li>
      </ul>
    </main>
    <footer>
      <p><a href="mailto:hello@robertakarobin.com">Contact me!</a></p>
    </footer>
  </body>
</html>
```

This keeps semantics and style much more separate. But stylesheets tend to get really, really long. That would make this page annoying to edit.

### The third is to use an external stylesheet

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Sweet Joke Page</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    ...
  </body>
</html>
```

And in a file called `styles.css`:
```css
h2{
  color: red;
  text-decoration: underline;
}
```

This is the tidiest and "best" way to use styles.


# Browser compatibility

(AKA "Why everyone hates Internet Explorer")

## Back in the early days of the web...

There was just HTML. The purpose of the Internet was for scientists to share research.

Then, someone was like, "Hey, we want colors and images!"

So they added attributes like `bgcolor`, `border`, and `face`.

The result was sites like this:

http://www2.warnerbros.com/spacejam/movie/jam.htm

...and this (scroll down):

https://web.archive.org/web/20040608010343/http://www.sewingandembroiderywarehouse.com/embtrb.htm

As the visual needs of web designers increased, the complexity of their code increased. Then, someone was like, "Hey, man, having semantics and style all mixed together is getting really annoying." And thus, CSS was born.

## But all was not good.

People hadn't really agreed on standards for HTML and CSS. Some browsers supported certain HTML tags but not others, and so on.

So the people of the world got together and decided on standards to govern web design. They agreed that they would all use the same elements and CSS properties and so on. No one *had* to -- a company could invent a web browser any way they wanted -- but that would be like you saying a foot is 11 inches while the rest of the country says it's 12.

But Microsoft thought to itself, "I'm going to invent my own standards for the Internet! So many people use my web browser that everyone will be forced to use my standards, and then I'll basically rule the Internet!"

But the people did not comply. Instead, they just stopped using Internet Explorer. And Microsoft learned a valuable lesson and has been playing catch-up ever since.

## What that means for today

...is that there's still some variety from browser to browser. It's most obvious in the default stylesheets browsers use. A "submit" button will look one way on Chrome and another way on Firefox. This is why, again, **you can't rely on default stylesheets**. If you want `<em>` elements to be italicized, you need to specify that in your CSS, because Apple might choose to make `<em>` elements in Safari underlined instead of italicized.

The biggest difference is in how Internet Explorer renders CSS versus how the rest of the world does it. It's fairly common for a web designer to make a page that looks beautiful in Chrome, then to open it in Internet Explorer, and to find that it now looks very different (although Internet Explorer's much better about this now than it used to be).

## Your best best

...is to guess what web browser your users are most likely to be using.

If you cater to a younger or more high-tech crowd, just worry about making your site look good on Chrome and Safari, and Firefox.

If you cater to old folks, the government, and those who are more likely to use whatever browser came with their computer, it would behoove you to test your site on Internet Explorer.

## A great site for testing compatibility

...is BrowserStack: https://www.browserstack.com
