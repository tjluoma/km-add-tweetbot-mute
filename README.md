Quickly add new Tweetbot mute keyword(s) using Keyboard Maestro
====================

I love me some [Twitter], but I find that some days the Internet is talking about something I just don't care about. That's where 'mute filters' come in. Tweetbot lets you mute words or phrases and will hide subsequent 'tweets' that match your filter.

The problem is that adding a new "mute keyword" to [Tweetbot] requires *way* too many steps.

1. Switch to the "Mutes" tab
2. Click 'Edit'
3. Click '+'
4. Click "Mute Keyword"
5. Click inside the Keyword field because for some frustrating reason Tweetbot doesn't put the cursor there automatically. 
6. Click "Save"
7. Click "Done"
8. Go back to the main timeline

Eight is way more than enough, it's about seven too many. Here's what I want: *Press a key combination, type a word/phrase, press enter.* Boom. Done.

### Wait! Too many, annoying, repetitive steps!? Automate it!

As I've said repeatedly, once you get into the "automation mindset" you'll start to find uses for it all over the place. This is yet another example.

[Keyboard Maestro] is one of my favorite tools for this on the Mac, specifically because it can do so many of these things, and making a new macro is easy. However, since this does not need to be a "global" macro (that is, it doesn't need to work anywhere, anytime, it just needs to work when I'm using Tweetbot) my first step was to make a new 'group' in Keyboard Maestro by choosing the "File » New Macro Group" menu. I named it "Tweetbot" because I am wildly creative. Then I told Keyboard Maestro that any macros in this new group should only be available in one application.

The red arrows in the image below point to the Macro Group and the setting to show that it is only active in Tweetbot, and the yellow arrows point to the list of macros in that group. Right now there is only one, but if I ever want to make any more that are only for Tweetbot, I just have to drag them into that folder.

<p style="text-align:center"><img src="http://www.blogcdn.com//media/2013/08/keyboard-maestro-editor-tweetbot-1375343044.jpg" border="0" width="456" height="216" alt="[Screenshot of Keyboard Maestro Group]" /></p>

This is important because it allows me to define a keyboard shortcut in Keyboard Maestro which will only be used when I am in Tweetbot. Now I don't have to worry about it being accidentally triggered in other applications. I chose <kbd>⌘</kbd> + <kbd>=</kbd> because it seems like a good "Add" shortcut, and it was not already in use in Tweetbot.

### Now let's make the macro ###

Here are the steps the macro will take once I press <kbd>⌘</kbd> + <kbd>=</kbd>: 

1. Prompt user for word/phrase to add to Tweetbot mute filter. (See "Screenshot #1" below.)
2. Select the "Mutes" item from the "Window" menu
3. Click the 'Edit' button
4. Click the mouse on the "+" button (see the red arrow on "Screenshot #2" image below)
5. Press 'Enter' to select 'Mute Keyword (see the blue arrow on "Screenshot #2" image below)
6. Press <kbd>Tab</kbd>  twice to get into the proper field to add the keyword(s) to be filtered
7. Paste the text that the user entered (see Important Note below)
8. Click 'Save' button
9. Click 'Done' button
10. Pause for 1.5 seconds to that I can see the new filter has been created
11. Go back to my Timeline (which is probably where I was reading when I decided I needed to mute something

## Screenshots ##

Keyboard Maestro comes with an item to 'prompt user for input' and allows you to easily customize it. Here's what mine looks like:

<p style="text-align:center"><img src="http://www.blogcdn.com//media/2013/08/keyboard-maestro-user-input-for-tweetbot.jpg" border="1" width="456" height="139" alt="" /><br/>Screenshot #1</p>

Note that this is the very first step in the macro. I *could* have scripted this differently. For example, I could have created a macro that does the first six steps and then waited for me to enter the mute keyword(s) and then continued. I chose *not* to do that for several reasons:

1. By prompting the user for input immediately, we give the user a chance to cancel the macro, in case s/he triggered it accidentally or changed his/her mind about it.
2. The user will not have *any* delay between triggering the macro and being asked for input, so there's less of a chance for them to forget what it was they wanted to mute.
3. The user will still be looking at whatever screen they were at when they decided to add to the mute keyword(s) list.  This is particularly helpful if I need to verify the spelling of something.

The only 'tricky' part is this:

<p style="text-align:center"><img src="http://www.blogcdn.com//media/2013/08/tweetbot-mute-filters.jpg" border="1" width="456" height="267" alt="" /><br/>Screenshot #2</p>

The "Done" button on the top-right changed from 'Edit' after we clicked that button. I tried telling Keyboard Maestro to click the "+" button, but that did not seem to work reliably, so instead I told it to click at a certain number of pixels relative to the top-left corner if the front window. (You can calculate the pixel count using [xScope] or by trial-and-error.)

Once the "+" button has been clicked (red arrow) and then we need to select 'Mute Keyword" (blue arrow). The good news is that once we have done the mouse click on the "+" button, the  "Mute Keyword" entry will be highlighted, so all we need to do is simulate pressing the <kbd>Enter</kbd> key after the + button has been pressed.

## Important Note ##

When you mute a keyword, Tweetbot will let you 1) mute mentions, and 2) set how long you want the mute to be active (1 day, 1 week, 1 month, forever). I do not adjust these settings in this macro which (at least for me) appears to mean that mentions will not be muted and that the filter will be in place forever, which is what I want. I'm not sure if Tweetbot changes those settings based on your previous settings or not.

If you want something different, you can change those settings using Keyboard Maestro too. Doing so is left as an exercise to the reader.

## Why Tweetbot? ##

I've always been a big fan of [Twitterrific](http://iconfactory.com/software/twitterrific) but it doesn't have muting on the desktop *yet* so I'm using [Tweetbot], which is quite nice. You should be able to adapt this process to any Twitter client.

One thing I really like about Tweetbot is that these filters sync between the Mac and iOS client, so you don't have to maintain multiple filter lists.

## Download my macro ##

If you'd like to [download my Keyboard Maestro macro] you can find it on [Github].


[Github]: https://github.com/tjluoma/km-add-tweetbot-mute
 
[download my Keyboard Maestro macro]: https://raw.github.com/tjluoma/km-add-tweetbot-mute/master/KM-Tweetbot-Add-Mute-Keyword.kmmacros

[Keyboard Maestro]: http://www.keyboardmaestro.com/main/

[Tweetbot]: http://tapbots.com/software/tweetbot/

[Twitter]: http://twitter.com/tjluoma

[xScope]: http://xscopeapp.com

