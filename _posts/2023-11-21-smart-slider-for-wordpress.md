---
layout: post
title:  "Smart Slider for WordPress!"
date:   2023-11-21 17:10
categories: wordpress
---

Smart Slider for WordPress is a WordPress plugin that allows you to create slides of different types on your WordPress site. I have tried MetaSlider before for creating slides on WordPress, and I have been happy with it until recently. After moving a local WordPress instance to a VPS, I updated the plugins and then found out that the slides didn't show correctly anymore. The photos of the slide would show up below each other. I tried fiddling around with the settings, but it sometimes showed errors while saving some settings, and with other settings that saved successfully, the display was not fixed. 
Finally, I decided to try a new plugin. There was this Smart Slider that had a good rating on WordPress market. So, I installed and enabled it. Although it was not as easy to use as MetaSlider, it did the job, and with some custom CSS I was able to position the caption I wanted to show on it. It also supported specifying link on each slide, which allowed users to click each slide and read the related post. 
Here is the custom CSS I used for the slide:

{% highlight css %}

//To size it around 60% of the total screen width
.n2-ss-slider-wrapper-inside{
	width:60%;
	padding-top:50px;
}

// To position slide caption at the bottom side of the slide
div#n2-ss-2 [class^="n2-font"]{
	margin-top:20rem;
	font-family:Vazirmatn;
	background-color:rgba(227, 52, 108, 0.5);
}

{% endhighlight %}