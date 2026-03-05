---
tags:
  - computer-science
  - workshop
---
This is an introduction to web development with HTML and CSS to make your own websites. It was written with non-programmers in mind, mostly artists. Yours truly wrote it by hand with no AI assistance.
# Resources
- Marighoul on YT: [HTML/CSS for Beginners](https://youtu.be/9z8FP8ear2Y?si=2oeYOETBuc8x_Fcv) (Good step-by-step)
- Talkshowbot on YT: [HTML FOR DUMMIES](https://youtu.be/V1BqNbckZYg?si=Xozvyr3xlMBpRXwH) (more on Neocities and CSS)
- Luvstarkei on YT: [Customize your Website - Graphics and Resources](https://youtu.be/0WsYvNDrGHc?si=76TdjV6HrMPN6Z4P)
- Flickarity on YT: [Simple Website Layout from Scratch](https://youtu.be/vlDAQXqOqKo?si=86qcwz0wEanU07ln)

- W3Schools: https://www.w3schools.com/html/html_intro.asp (dummy simple)
- Neocities's HTML Tutorial: https://neocities.org/tutorial/html/1 (might need an account)
- All the Webdev links you'll ever need: https://discourse.32bit.cafe/t/resources-list-for-the-personal-web/49
# Before starting
- I recommend you install `git` for version control: https://git-scm.com/install/windows.
- If you wanna host on Github (I recommend), make an account there (Github is Microsoft's). Github Desktop is a good user-friendly GUI for git version control and you don't need an account to use it.
- If you wanna host on Neocities, make an account there as well, and do the tutorial (5 mins).
- Download Visual Studio Code (or use some other IDE, as long as it has syntax checking). It's also a great GUI for git version control. Here's VSCodium, a version without trackers: https://github.com/VSCodium/vscodium/releases
- Clone my repository to your machine as a base.

---
# HTML / CSS
When your website is served, the home page will be a file named `index.html`. Let's create that file (the base project should have it already created).

HTML is used to describe the layout of your page, what elements are included and in what order. The HTML file needs a skeleton like the one below. In VSC you can quickly create this with _emmet_ by typing `!` and pressing enter.
```html
<!doctype html>
<html>
  <head>
    <!-- this is a comment. -->
    <!-- meta stuff goes here -->
  </head>

  <body>
    <!-- text and visuals go here -->
  </body>
</html>
```
You can save and open this file in the browser. We'll be refreshing it (F5 in most browsers) whenever we save changes to preview them.

HTML is built by nesting _tags_ inside other tags. I may also call them _elements_ throughout the workshop. You usually open a tag by writing its name in angle brackets, then close the tag by doing the same but with a forward slash before the tag name. Variables will go inside the opening angle brackets. Here, we have the body tag with a style attribute.
```html
<body style="color: blue;">
  **Stuff goes inside**
</body>
```
Text and visuals need to be inside the body tag, which is inside the html tag. When putting something inside tags we want to add some indentation to show what's inside what.
### HTML Text tags
You can write text wherever by just typing it, but there's purpose-built tags to handle standardizing styling text. The `<p>` tag makes paragraphs, and the `<h1>` to `<h6>` make headings.
```html
<!-- This is all inside the body tag. -->
<h1>Welcome to my Website</h1>
<p>this is where I post what I do with my free time, feel free to browse!</p>
```

> [!tip] 
> if text appears side by side and you want a line break, you can either press enter twice, or add a `<br>` break tag. Pressing enter once will wrap the text for your convenience but it will still render continuously.

You can make text bold or italic with the `<b>` or `<i>` tags. Put them around the text you wanna change, and you can put them inside paragraphs and headings. There's other tags like this you can Google for.
```html
<p>
  writing html isn't <i>that</i> hard, but it is <b>finicky</b>.
</p>
```

To make lists, use `<ul>` for unordered lists and `<ol>` for ordered lists. You can add items by adding the list item `<li>` tag and adding text inside those.
```html
<ul>
	<li>Go for a walk</li>
	<li>Buy an ice cream</li>
	<li>Finish the <i>workshop</i></li>
</ul>
```
### Links, Pages, Images
To add a link to your page, we'll use the `<a>` tag. The name isn't memorable but just go with it. To make it link somewhere, we'll need to fill the `href` attribute with the link. Attributes or variables go inside the opening tag, with an equal sign, and the value inside double quotes.
```html
<a href="https://www.youtube.com/@shar">Shar's Youtube Channel</a>
```

We can also use this to link to other pages in our website using relative addresses. Let's create a new page called ``connections.html`` in the same folder as the home page.
```html
<!doctype html>
<html>
	<head>
	
	</head>
	
	<body>
		<h1>Connections</h1>
		<h3>socials</h3>
		
		<h3>buttons</h3>
		
		<h3>friends</h3>
	</body>
</html>
```
In our ``index.html`` we want to reach this Connections page. To do this, we can create a new link element. Because the connections page is in the same folder, its relative link is just the file name:
```html
<a href="connections.html">My Connections</a>
```
We also probably want a way to return to our home page inside the connections page. As they are in the same folder, just link to the index file.
```html
<a href="index.html">Back to home</a>
```

Let's add some images! Like with links, we can include images both from the outside web as well as from our own files. The repository has some images included in the ``images`` folder already.
> [!warning] 
> If hosting on Github pages, files inside folders starting with underscore (`_`) will not be shared. Make sure folders with public files have valid names.

Images are made with the `<img>` tag. **This is one of the few tags that doesn't take a closing tag**. We will link the image using the `src` attribute. Many hosting providers will also require an `alt` attribute that contains a short text description of the image (you'll see it when the image doesn't load). You can display GIFs with this too.
```html
<img alt="kirby plush" src="images/kirby_plush.avif">
<img alt="kirby sleep" src="https://c.tenor.com/89OdEJSdgZwAAAAC/tenor.gif">
```
### Styling with Cascading Style Sheets (CSS)
Maybe the text or background aren't the right color. Maybe the images are too big. Maybe you want your elements to align horizontal instead of vertical. That's what styles are for.

You can add the ``style`` attribute to any HTML element. They use inlined CSS syntax, which we'll see in a bit, but all you need to know is it uses ``kebab-case``, and properties are separated with semicolons. There are [lots and lots of properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties) but we'll check the more basic ones.
```html
<img style="width: 100px; height: 200px" alt="kirby plush" src="images/kirby_plush.avif">
<p style="color: darkmagenta">very cute plushies</p>
```
- width, height: these set the element's size directly. you can use 20px for straight pixel size, 20% for "a fifth of the size of the parent element", or 20vw for "a fith of the size of the screen". there's other measures as well.
- color: this sets the color of _text_ of this element and all its children.
- background-color: this sets the background color of elements, which goes behind the text.

If you have a lot of styles, these can get hard to read. For this purpose, we can create an external ``styles.css`` file. Create it, and add this to your HTML's head section (not the body!):
```html
<link rel="stylesheet" href="styles.css">
```

If we want all our website to be white text on black background we can write as such:
```scss
//always use brackets. it's recommended you indent the inner contents as well. you can't nest definitions

body { 
	color: white;
	background-color: black;
}

h1 {
	font-weight: bold;
	font-size: 40px;
}
```
A style defined here will apply for any elements of the defined tag type. If you need to apply a style to all elements you can use the `*` wildcard.

> [!info] 
> They're called Cascading Style Sheets because the styles apply in the order they're declared in the document, top down, so later styles override earlier ones.
### CSS Classes (and IDs)
To not have to redeclare commonly used styles every time, or have to write them in the html file which feels clunky, we can use IDs and Classes.

IDs are used for unique elements in any given screen. Only one element per html page can have a certain ID. These will be more useful when you're using Javascript but are here for definition. An ID is defined with a `#` hashtag symbol:
```scss
#home-button {
	font-size: 32px;
	box-shadow: 0px 4px 4px black;
}
```
IDs are defined in the id attribute, and any element can have an id, as long as no other element has the same one.
```html
<button id="home-button">Home</button>
```

Classes are way more powerful for styling. These define multiple reusable sets of styles that can be reused and combined. Classes are defined with a `.` period before the class name:
```scss
.rounded {
	border-radius: 16px;
}

.art-frame {
	border-style: inset;
	border-color: gold;
}
```
Classes are applied inside a `class` attribute. You can add multiple classes separated by spaces.
```html
<img class="rounded" alt="kirby plush" src="images/kirby_plush.avif">
<img class="art-frame" alt="kirby plush" src="images/kirby_plush.avif">
<img class="rounded art-frame" alt="kirby plush" src="images/kirby_plush.avif">
```
### The Notorious D I V
The `<div>` tag lets you create a generic empty element that can be styled as desired. These are great for panels, containers, dividers, and all sorts of structural components.
```html
<div style="background-color: beige; border-radius: 16px; width: 200px; padding: 16px;">
	<p>This is a cool panel!<p>
</div>
```

We can use css _classes_ to make these into almost self-contained components that are easy to reuse. You can still add some styles manually in addition to the classes.
```scss
.beige-panel {
	background-color: beige;
	border-radius: 16px;
	padding: 8px; //internal
	margin: 16px; //external
}

.tech-panel {
	background-color: black;
	color: cyan;
	padding: 16px;
	font-family: monospace;
}

.aspect-square {
	aspect-ratio: 1 / 1;
}

.aspect-card {
	aspect-ratio: 63 / 89;
}
```
Now our divs will have clear styles:
```html
<div class="beige-panel aspect-card" style="height: 300px">
	<h4>Card Name</h4>
	<div class="tech-panel aspect-square" style="height: 100px">
		<p>illustration here</p>
	</div>
</div>

<div style="width:10px; height: 100px;"></div> 

<div class="tech-panel aspect-card" style="rotate: 45deg">
	<p>angled</p>
</div>
```
While here, you may want to learn about margins and paddings. Margins are the distances between two elements (outside the div), and paddings are the distance between the edges of an element and its internal children (inside the div). These will help make your layouts more readable and less cramped.

This is all I have for this workshop as far as code goes. This is just the start and there's so much more you can do with these technologies that I'll save for another time.

---
# Hosting
This guide also includes how to put your website on the internet for everyone else to see. Or maybe just your friends? It's up to you!
### Hosting on Github Pages
First, create a new repository // upload your files to a repository on Github. Then, go to your repository's webpage. In the _Settings_ tab, find the _Pages_ sidetab.

For hosting static html files, select "Source: Deploy from a branch", then "Branch: main" and press Save. This should create a _build and deploy_ Action that you can find in the Actions tab.

The site url will be ``https://<your-github-username>.github.io/<your-repo-name>/``.

> [!info] 
> A Github account is allowed up to 7 private repositories. If a repository is public (they are by default), every file will be available to the public to read, so **don't include information like passwords and credit card details or images/videos not meant to be shared**. Even private repositories may have their files scraped through HTTP like any other website, so keep this in mind.

> [!tip] 
> If your repository has the same name as your github username, the address will simply be ``https://your-github-username.github.io``!

### Hosting on Neocities
Make an account on Neocities. You'll be deciding your page url as you make your account, like with Github: ``https://<your-username>.neocities.org``.

Apparently you also need to finish their HTML tutorial (which is very nice but will take 5 minutes).

You can access your dashboard to edit your site by clicking on the top right corner where your username is, then Edit, or just follow this link: https://neocities.org/dashboard

At the dashboard, just upload all the files you have locally. Neocities will also let you edit the files right in your browser with a semi-live preview (you still need to click Save, and reload your website on a new tab, but no build step is needed).

> [!tip] 
> Neocities has a really nice community of artists both learning and teaching cool stuff to do with websites. I suggest taking a look at those online!

---
# What to research next?
I recommend you pick one of these themes to learn and experiment with. Take it as a fun challenge!
- Javascript for the Web (or HTML + JS). It can make your static websites a bit more reactive, with buttons that bring up hidden sections, random animations and effects, or even little games.
- Grid and Flexbox. These are the main appeals for using HTML + CSS in responsive contexts like websites for all sorts of screen sizes.
- CSS property "position". This will give you a lot of freedom on placing things on the page like stickers and floating banners.
- Embedding games and other websites with _iframes_. This can make your website even more unique with fun stuff.
- Static Site Generators like Jekyll. If you want to make a blog with hundreds of posts, these take care of indexing, linking and tagging all the pages for you. There's templates on Github!
- "Buttons" for the indie web! Little animated icons that take you to other websites. This is how you can connect friends people to your website!
- Webrings. A funky way to group websites together so someone browsing through your site can get into all your friends' sites as well.
---
# Websites for inspiration!
_(As a reminder, if you're curious about an element or style or effect, you can always Inspect Element on it to check the HTML + CSS)._
https://seashrine.neocities.org/
https://www.sirmilkman.com/index
http://www.kirbysrainbowresort.net/index2.html
https://neonaut.neocities.org/cyber/88x31 (many indieweb buttons)
https://www.cs.furyu.jp/beyblade2025/en/
https://zeroxm.github.io/pokemon-roulette/ (game!)
