

Whenever I tell people I "do software" they lean in and put up walls. It's a somewhat contradictory reaction, but an understandable one. Outside of tech, software development is looked upon as a kind of magic. It's both attractive and intimidating. Attractive because you can seemingly make anything with this magic and intimidating because the making of such things is unintelligible to outsiders.

In a way, the intimidation is warranted. #Software  _is_ a lot like magic: developers speak arcane languages and write spells we call #Code. [Even new developers see it as magical.](https://spin.atomicobject.com/2017/08/29/strategies-new-developer/) I remember the first time I started coding, I felt as if I'd walked into the wardrobe and found Narnia. It was a new world, scary and dangerous. I broke the first terminal I touched, blowing up my Raspberry Pi so badly I still haven't fixed it, 5 years later. I floundered around a cloud based development environment, mixing up files and generally writing terrible code. It was a profoundly confusing experience.

I'm not sure it had to be. A few summers after my first troubled attempts at software, I worked at a Cybersecurity Company. At the end of the summer, I had a breakthrough insight: software is more like construction than magic.

Once I began to conceptualize software as a sort of digital construction, it became less scary. While there is a lot to construction, it's not seen with the weird mix of confusion and admiration as software. The reason? Construction is accessible. While we may not know building codes, we know how nails and hammers and wood work. We understand the tools of the trade and it's easy to see how they result in a finished product: a home.

With this analogy in mind, I'm going to use this post to introduce you to the tools of a software developer. My hope is that by knowing the tools of the trade, you will find it a little less intimidating wizardry and a little more accessible construction. Who knows, after this you might even want pick up a hammer yourself!

You can get complicated when it comes to Software just as you can get complicated when it comes to building homes. But, there are 3 basic tools as I see it:

1.  The Text Editor (The Hammer & Nails)
2.  The #Terminal (The Workers)
3.  The #Language (The Building Code)

_Bonus_: The #Cloud (Subcontractors)

## The Text Editor (The Hammer & Nails)

We've all used a text editor of some sort. Word, Google Docs, Notion, and even Slack can be used as text editors. Text editors do exactly what they say: they allow you to edit text. The text editor is the hammer and nails, the bread and butter, of a software developer. A good text editor makes your job easy, just as a good solid hammer makes quick work of nails.

The main difference between the text editors normal people use and the one's that developers use is that they have the rules of the building codes (the language) built in. Plus, they have fancy features like [multicursor magic](https://spin.atomicobject.com/2019/04/04/vscode-multiple-cursors/), which is real wizardry.

On top of all these fancy features, there are text editors that include access to the terminal (the workers) as well. These beefed up versions of text editors do it all and are called an [integrated development environment](https://www.codecademy.com/articles/what-is-an-ide). In construction terms, an IDE is like a workshop, where all the tools you could imagine needing are right there on hand.

So, like you've used a hammer and nails, so you've used a text editor. The difference between a developer's text editor and yours is like the difference between a nail gun and a hammer. One is fancier and easier to break, but makes the job faster if you know how to use it. 

Examples for the Curious: 

- The Fancy IDE I Use: https://code.visualstudio.com/
- The One Lots of Other People Use: https://atom.io/
- A True "Text Editor": https://notepad-plus-plus.org/

## The Terminal (The Workers)
If the text editor is the hammer & nails, the terminal is what puts everything together. On a build site, if you have no workers, all you've got is a bunch of wood and metal. On a computer, without your terminal, all your code is nothing but a glorified word document. 

The terminal is what "executes" your code. Only heaven knows why we chose the word "execute," but unlike in the "real" world, "execute" means to run in the computer science world. When you click on the Netflix app on your TV, the computer in there "executes" or "runs" the Netflix program and viola, you have movies. 

Just as workers in construction, the terminal does dangerous work. Your terminal is connected to the "foundation" of your computer and can topple it if you aren't careful (I destroyed my Raspberry Pi all those years ago from the terminal). That said, with great responsibility comes great power. You can do [unbelievable things from the terminal](https://chrishannah.me/cool-things-to-do-in-terminal/). 

The terminal is like the "magic" in your computer and it's one of the secret weapons of the software developer. An understanding of the terminal and the commands it can run is part of what helps us do what appears to be magic. 

Back in the day, the terminal was all anyone had. As recently as the early 2000s, I remember watching my dad zoom around his laptop terminal as he checked out the charts for his job at the radio station. Over time, the terminal has been hidden by convenient programs like Word and Chrome that have Graphical User Interfaces (GUIs). Behind the scenes though, the terminal still runs the show. 

One last metaphor. The terminal is like the Wizard of Oz. It seems magical and shows off using fun apps with GUIs that we love, but behind the scenes, he's just the same old terminal. He's still got power, but it's much less flashy. 

## The Language (The Building Codes)
Just as construction is limited by building codes, software developers are limited by the language they write in. Each programming language comes with its pros and cons. 

Some languages, like C, let you have fine grained control over every little detail at the cost of dealing with all said details. Others, like Python, let you get off the ground quickly but offer little fine grained control. If you're curious to learn more about these pros and cons, check out this [article](https://www.coderkids.com/blog/beginners-guide-to-programming-languages).

Part of the pros and cons of a language are the community surrounding it. Just like building codes, programming languages are created by communities and are "living" - they change over time. New features are added and bugs are worked out. The more active the community, the more help available and the better the language will be in the future. 

Unlike building codes, programming languages can give you automatic updates about your compliance. This is one of the advantages of an IDE over a text editor. IDE's often check to see if your code follows the "building code" of your language. A normal text editor, like Word, lacks this key feature and thus leads to buggy code (which is why we don't use it). 

The final point about languages is that all their "rules" are listed online in a place called, "the docs". The docs are like a programming spell book. They tell you what the language can do - a great starting place for any new project. For the curious, check out the [Typescript docs](https://www.typescriptlang.org/docs/) here!

## Wrap Up
Software development is not online wizardry (as much as we'd like you to think it is), it is digital construction. We use many of the same tools you do every day, just like you use many of the same tools a construction worker does. We use souped up text editors to write our code, terminal workers to make it run, and languages to tell us what is and isn't ok to build. 

### Bonus for the Curious
#### The Cloud (Subcontractors)
One of the most confusing concepts out there in the computer science world is the Cloud. From the outside, the cloud seems like the height of wizardry. You can cast spells from anywhere! What magic!

Yet like all our previous examples, the Cloud is not as fancy as it appears. If we take the Cloud out from behind the shiny curtain, we find subcontractors. 

The cloud takes work your terminal would normal do itself and has other terminals do it instead. When you upload your Word document to the Cloud in Google Drive, you're computer sends it to Google, who puts it on their computers instead. When you come back later to grab that same Word document from your phone, it asks the Google computers for the doc and it's terminal sends it over to you. 

The magic of the Cloud is that you get access to terminals anywhere in the world. It's basically like having hundreds of subcontractors on demand everywhere you go. You could build whatever you want wherever you are! 

The same applies here. With the Cloud, you can build just about anything you can imagine because you suddenly have access to nearly unlimited terminals via the internet. The Cloud is what makes something as big a Netflix or Google possible. Without it, you'd have to have massive data centers all in one place. With it, you can have your work done anywhere, anytime. 

#Spin