
# Learn Lazy Loading Through a Simple Example

Let’s load that heavy second CSS file only after the user scrolls down

![](https://cdn-images-1.medium.com/max/2800/1*OIeSke0xle0FTZ4fy1l9qQ.png)

<iframe src="https://medium.com/media/318e69af0510df376a4046a728b781cf" frameborder=0></iframe>
> When it comes to optimizing websites for better performance, lazy loading is a concept we can’t ignore. But before starting, let’s go through some background of performance improvement.

## Three pillars of website optimization

Website optimization is a huge concept which includes optimizing the frontend, backend, and the network. Optimizing each of these 3 pillars is very essential, and each concept that we apply while optimizing them is very important to understand if we wish to actually make our website better in terms of performance.

![](https://cdn-images-1.medium.com/max/2000/1*H3KGy6PN4wmOqSk5s7XmOg.png)

The frontend performance can be improved by various techniques like optimizing the code, minimizing the files, minifying CSS, uglifying JS, shrinking the Images, lazy loading, caching, etc.

So you might have guessed, lazy loading is an important concept when it comes to optimizing the frontend for better performance.

## Psst… A secret between me and you

Ok, I am going to tell you a little secret, can I expect that you will keep it a secret, just between me and you?

<iframe src="https://medium.com/media/56e4358162ef2fea2c613086e6a678b9" frameborder=0></iframe>

Cool, I trust you! So I was not getting ideas for my new blog and yesterday one of my friends (who is working for a startup remotely) asked me
> # Hey Madhav, my boss wants me to apply lazy loading while fetching the data for their website, I googled the definition of lazy loading but did not understand shit, can you explain it to me in layman terms?

Lazy loading, as a concept, is very easy to understand but it can be implemented in various ways depending on your use case. So I explained the concept to him, and in between, I had an aha moment, I thought why not write a blog on it so that more people who are struggling with this concept can be helped?

Sorry for writing this story out of nowhere, but I hope you got what I am trying to say, did you?

What I am trying to convey here is that if you are not understanding a concept even after googling it, why not reach out? I might be able to explain it easier terms so that you can understand the concept, and I can get the idea for my new blog Haha!

So yeah, if you feel I can help you out, reach out, I would love to help (unless the answer can be found very easily on google, if that is the case, GOOGLE IT!)
> Ok Madhav, you bored me much, now get back to the topic!

Ahh, I am sorry man, here you go :)

## The concept of lazy loading

For a moment just forget about those big big definitions that you crammed in your college and try to understand the concept (Don’t worry we will get back to the definition as well)

Let’s take an example, suppose you are making a chat application (just like Whatsapp) and the idea is simple, a user can have any number of conversations (depending upon how many contacts he has).

So whenever he opens the app, his conversations gets loaded with the latest message in each conversation to display in the list.

![](https://cdn-images-1.medium.com/max/2000/1*JHY7Yr3mPwzDYnAKUg6H7Q.png)

Things are pretty easy, right? All we have to do is store the complete conversation list in the database, and as soon as the user opens the app, we fetch that conversation list.

Life is not that easy, is it? What if the user is a huge celebrity? What if he has thousands of contacts and he is in touch with all of them?

In this case, as soon as he opens the app, the whole conversation list is being fetched from the database, which is obviously pretty big and takes forever to load. Annoyed by this, the user uninstalls our app and uses a better application.

<iframe src="https://medium.com/media/d68a8a02d0363e9d3c8bbef5a482992c" frameborder=0></iframe>
> Oh crap, that is a pretty SERIOUS issue, what can we do!?

Good question, I expected that you will ask this, think a little bit, how can we solve this? (Obviously, the answer is “by using lazy loading”, but I need to think how are we going to apply it in this scenario)

Ok, I will give you 5 minutes to think about it and in the meantime, I’ll go grab a cup of tea (Yeah, I am not a big fan of coffee)

<iframe src="https://medium.com/media/403abce398a5a64ed11a8c4ec21f6e6d" frameborder=0></iframe>

Okay, your 5 minutes are over (kidding!), I hope you were able to figure out the answer.

The solution is very simple, since it took a lot of time to load the whole conversation list, ***we will not load the whole conversation list :)***

Yep, that’s it, that’s the whole concept behind the lazy loading. We will load only the things that we require as soon as the user opens our app. Nothing less, nothing more!

Therefore, in this case, we would load (say), 3 times the number of chat items that can be displayed on the user’s screen (depending on his screen size), and render that, and as soon as that is rendered, we will make another request to load more items, and once they are loaded, we will request more and so on, until all the items are loaded.

Now since we are not requesting all the conversations in one go, but only 10–12 items (example), the user will get the response very quickly and he can start interacting with the app. Now he won’t have to wait that much, correct?
> Woah Madhav, that was SUPER EASY!

I know man, I am a good teacher :)

Haha, just kidding. Now that we have understood the meaning, let’s have a look at the definition as well,
> # Lazy loading is a design pattern commonly used in computer programming to defer initialization of an object until the point at which it is needed.

I hope the definition also seems pretty easy now, since you know the concept. The definition basically says that we load the resources only when they are actually required.
> Wew Madhav, that was simple, but I want to see it in action practically, help me out bro

Yeah Yeah, calm down man, we will get to it, but first let’s quickly have a look at why do we need lazy loading

### Why Lazy Loading?

Let’s suppose that you are loading stuff that is not currently visible to user, and the user might never even see it, you are at loss,

1. You are wasting the precious time that could be used to render only the data that is currently being displayed to the user. He might get annoyed by the slow loading and even leave the website/uninstall the app

1. You are wasting the precious data. I agree that many people have unlimited data these days, but the app has to be optimized for all users and let’s say a particular user group is using a limited data plan, loading things that they might never see would be a waste of their money

1. Waste of processing power, agree that it might be comparitively very small, but still why waste it?

1. In cases of websites/webapps, CSS is render blocking, until CSSOM is created fully, render tree will not be created, so load only whatever is really required.

Now I guess you really understand the importance, so let’s move to the final and most interesting section of this blog :)

## Time to code

Now since we have theoretically understood the concept of lazy loading, let’s try to implement it to see it actually in action.

Yayy, I am super excited, we are finally going to code after that huge theory :D

So to see how things work, we are going to create a very simple website, which would have two sections, one primary section (height: 110vh) which would be visible to the user as soon as the website loads, and other secondary section (height:110vh) which would be visible only if the user scrolls down.

In this example, we would have two separate stylesheets for both of them and will load the second style sheet only after the user begins to scroll down.

Please note that this is just an example, in the real-world scenario we would not have 2 separate style sheets for the content which has to appear just as soon as the user scrolls, why? because if somehow there is some network connection error, the user won’t get the second stylesheet and the content in the second section would appear in a very bad way.

But we can use the same principle to lazy load the images, or lazy load the data with which user is not directly interacting as soon as the page loads and has to be fetched from the server (like the list of conversations in the example of the chat app we took in the beginning)

### Part 1: Coding our HTML

As we discussed, we would add 2 sections, one with class primary and the other with class secondary, and we just need to add the link to the first stylesheet. Here’s the code:

<iframe src="https://medium.com/media/7afac8cd5bd374c477379bb9c2556367" frameborder=0></iframe>

As you can see, we have 2 sections here, each section will have a height of 100vh, and inside each section there is an inner div whose content will be centered.

Also, in the <head>, you might have noticed that we have included only the style1.css file. We would be fetching style2.css dynamically when the user scrolls down.

### Part 2: Let’s add the first stylesheet

This style sheet will make the height of primary section 110vh and the background-color ff80ab

Also, we have to center the inner div both vertically and horizontally.

<iframe src="https://medium.com/media/718f21ffa5e1554d19d30781322fef22" frameborder=0></iframe>

### Part 3: Adding the second stylesheet

This will be similar to the style1.css but with background-color d1c4e9.

<iframe src="https://medium.com/media/a2f8f955f4d13b291c3b24872e3a794e" frameborder=0></iframe>

Ok, now I know all of you are going to ask me why did I not give the inner div of the secondary section the same class, primary-inner even though they have the same style. It is just because I wanted to illustrate two different stylesheets completely for both the examples, of course in the real-world scenario we would try to re-use the code as much as possible.

Alright, now it’s showtime, we are finally going to add the JS which will be responsible for loading the second stylesheet dynamically.

### Part 4: Adding the script

So here’s the main part, the idea was to load the “non-initially-visible” contents lazily, here we go :)

<iframe src="https://medium.com/media/63451ba54332f9da8575c463dcf5ae10" frameborder=0></iframe>

So if we go through the code, it is easily understood that we are basically adding the new stylesheet dynamically after the user scrolls down.

To detect scroll down, we are using window.onscroll event, and to make sure that the call goes only once, we are maintaining a flag variable, scrollFlag that is set when the onscroll is called for the first time.

And to load the stylesheet, we have created a function in which we are checking if the direct document.createStylesheet method is supported, if yes, then we use that, otherwise, we create the link tag and append it in the <head> tag

## That’s it let’s see it in action!

So we are done with the code, now to see it in action, open the index.html in your web browser, inspect element and go to the networks tab,

In here, you will notice that only style1 stylesheet has been called, and once you scroll down, style2 stylesheet will also get called.

Here you go —

![Notice how “style2.css” gets loaded after we scroll](https://cdn-images-1.medium.com/max/2712/1*OjqAM4RdGlztPuGBd69RMg.gif)*Notice how “style2.css” gets loaded after we scroll*

So that was pretty much it! Hope this blog helped you :)

> # *“Always aim for the moon. If you miss you’ll land among the stars.”*

![](https://cdn-images-1.medium.com/max/2000/0*7RLU2PeptbVcKRZg.png)

Feel free to reach out to me anytime if you want to discuss something :D

I would be more than happy if you send your feedback, suggestions or ask queries. Moreover, I love to make new friends and we can be friends, just drop me a mail.
> *Thanks a lot for reading till end. You can contact me in case if you need any assistance:
Email: madhavbahl10@gmail.com
Web: [http://madhavbahl.tech/](http://madhavbahl.tech/)
Github: [https://github.com/MadhavBahlMD](https://github.com/MadhavBahlMD)
LinkedIn: [https://www.linkedin.com/in/madhavbahl/](https://www.linkedin.com/in/madhavbahl/)*
