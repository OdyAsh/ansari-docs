# Ansari Backend V2.0 - 004 Main and Presenter Files

[00:00:00] Okay. Here we go again. 


## [00:00:03] Understanding the "main_*" Logic

[00:00:07] So, uh, Now what's remaining is is the main logic, the main, the core of the project. I will briefly explain the purpose of main file versus presenter files right now. Okay. 


## [00:00:21] "main" Stdio File

[00:00:28] So let's start with the easiest one of them for the main stdio file. This file aims to process inputs from [00:00:30] standard, input from input, which is a terminal. Over here engineer answers using a specayah_fileed EL model, which is Ansari agent. Okay. There is literally nothing to explain here. Just imports and then the logger that I previously explained. And then we get an instance of the class of Ansari, the agent, which uses the open AI model, which I'll explain this file a little bit later.

[00:00:50] And, and passes this agent to the presenter clause, which will present this present here means that, okay, so the main difference is this the [00:01:00] main logic is the entry point. Is the entry point file. So when we want to run this project, where do we go? What do we run? We run these main files.

[00:01:08] So we want to run the main file where the output channel, where the output channel is. The S-D-D-I-O is the terminal. Then we run the script. Okay? We say in the terminal Python space, main, stdio pi. Okay? And we run it. 


## [00:01:22] Presenting with the Presenter Class

[00:01:22] And then this class is responsible for presenting. For for presenting the the way that [00:01:30] it'll run in here.

[00:01:31] Okay, so let's see that. If you go here you'll see this function is a function responsible for presenting. It has a following itself. That agent to greet is just a agreed greeting message. I think actually you can see it's blinded with greeting here. Which I believe is a file that we have. If we see here reading the text, it'll say this, Sam, my name is Anari, I can help you with, et cetera, et cetera, et cetera.

[00:01:56] So it just paints that in the terminal. And then [00:02:00] this bigger than indicating that the user can type here, the prompt that he wants to type. 


## [00:02:05] Processing User Input

[00:02:06] And then, it's an input variable. Let's say the user asks in the terminal, who are you? Then this will be stored in this variable. And while this variable is true because it'll when the model finishes answering you, we can take the input again.

[00:02:20] So it'll, the, it'll, we will stop here and then when we enter, okay, I understand. Hope you have a great day. Then this will be a new line and [00:02:30] it'll contain the white loop. This is understandable, but this part, the four loop part, I can explain this a little bit and I actually can make this its own chapter.

[00:02:39] Okay. Two, two. 2 46. 2 4 6. Yeah. Okay, so this part basically says the following.[00:03:00] 

[00:03:00] We say the following here. Let's suppose that the AI model answers with I am Ansari. Wait, because this actually here, this here. Okay. He'll say, I am Ansari. I do 1, 2, 3, 4. Okay. That's actually a bad example because he already says that in the greeting okay. Let's give another example. What is your purpose?

[00:03:18] They asks, what is your purpose? And then they answer, my purpose is to blah, blah, blah. Okay? So in that string won't be obtained here in a single call, but rather in multiple [00:03:30] calls in streamed in a streamed way. So we will first get when calling this function the word. I am And then the world, Ansari.

[00:03:43] And then the world responsible, and then the world four, and then et cetera. So how is this done? 


## [00:03:48] Understanding Generators in Python

[00:03:53] It's done because this process, input function or method is actually a generator. Okay. It it heals as a generator, so a generator python, basically. Yeah. I'm not sure if this is exact or [00:04:00] not, but basically it's like a function that when you call in a certain way, you will get the next instance of its response value, of its return value.

[00:04:09] So since we normally in any Python function, you have given a function and given some inputs, you get an output, like a return value. Here, it's not exactly this it's basically you give it an input and then it exhaustive the returns values. So it returns the initial value, and then when you call it again, it returns another value.

[00:04:27] And then when you call it, again, it returns another value until it, [00:04:30] it, its list, its inner list or whatever gets exhausted and now we can call. We can say that it generated all of its possible return values. And so that's why we name it, it yields instead of returns yield. So we say here, yield as in Y-I-E-L-D yield.

[00:04:46] Okay. So I will go through the code of this, only this because it is worth going through. Okay bear with me. Let's go to this function and see what it does. It returns on the [00:05:00] function. Great. Let's see this returned function. Okay. You'll see that this also returns the generator, so it just returns the generator, which is returned from here.

[00:05:09] And now I expect here to see a yield statement here says, so basically in this try catch while something is being. While whilst whatever is being set true we will yield these values. Okay, sorry. We'll yield these values. This also returns yielded values process. One round. You will see here if [00:05:30] you go below in this part, we yield delta content.

[00:05:34] So basically what this says is when we get the response. Okay. The response then from here, when we get the response from the AI model, from LM model, from open AI or whatever it is not received as a single string. It's received in, in, in streams because you see his stream equal True. 


## [00:05:51] Implementing the Typewriter Effect

[00:05:54] Okay. So what that mean is we, when we receive the response, we can.

[00:05:58] We can, yeah, see custom [00:06:00] stream wrapper. Okay, so we can iterate on that. That's the meaning of streaming. So when we iterate on that, you'll see that chunk here could refer to a word, for example. So if. The model returns something like I am, Ansari. How can I help? Initially it returns.

[00:06:17] It returns I, and then, for example, m and nor is here. The space. The space over here. Okay. So this is and all of this is returned. One by one by by the [00:06:30] model. That's why you'll see later that we just con to concatenate these strings without adding a space or anything in that. Okay. And then you can see species like these.

[00:06:39] Okay? And maybe a question mark or maybe a step in the end. Anyways, so these, each of one of these are is a chunk, okay? And then from a chunk, it has multiple attributes. And then we get the content attribute from it, and then we yield that. So yield here means the following means that when I reach this point right here this function [00:07:00] returns this value.

[00:07:01] For now. For now. Okay. And this part which called Pro one Round Returns. For now I am okay. The word I am this trunk. And then this process, message history. Function that you see here returns in this part. I am. Which process? Inputs. Returns in here I am. And that's the word that we use over here.

[00:07:26] If it's not, none because I think, I'm not sure, I think sometimes that the [00:07:30] return chunks are none or have a non-value depending on the type of chunk return. But I think this is an extra check. This should not be never true. Is that, how do I say it? This shouldn't be false ever.

[00:07:42] I think Okay. But we just do it as a validation check. So if the word has anything in it like I am, or whatever, it's not none it's a string. Then we write it out, okay? And then we flush the term. Flush doesn't mean we clear it out. It's just something internal in the memory anyways.

[00:07:59] So this [00:08:00] gives a typewriter effect. So when we ask in determine, for example, who are you? Okay? And then you'll see that the answer. Instead of just a bulk of message coming up in a in one second. No, it'll be I am and then Ansari. And then I intend to whatever, and it'll have milliseconds of gap.

[00:08:16] Difference. That's a streaming effect. The typewriter effect. That's because it's internally here, just going through each word one by one. Okay. So yeah. This is a logic of this. Hopefully now understand that just how words are processed and are sent this [00:08:30] logic will continue with us.

[00:08:31] So hopefully you understood that. Where am I? Okay, I finished this now.

[00:08:38] Back to yeah, presenting rest of the presenting projects. Okay.


## [00:08:47] File and API Presenters

[00:08:47] So for other presenter classes like file, sorry. You also have a way to present. So if you look at its main file, you will see okay. I will explain [00:09:00] that in a minute. But basically this is the entry point for the main file in which we want to output stuff or input stuff from and to files instead of the terminal. Okay? So there we also present. How do we present, ie. How do we write to these files using the file presenter? Okay, so it opens here and then read lines.

[00:09:19] This is the input. And then send each line to agent and exit result. Read line for me. Literally the comments says it all. So presenting here doesn't necessarily mean just presenting as an output. It means output and input. Just [00:09:30] presenting like how are we presented? To the user who wants to activate this functionality.

[00:09:36] Okay. So we say to him, give us input in this way. And we tell him that we will give you the output in that way. That's why instead S-D-D-I-O presenter we also take input. Like we don't just present the output. We take input as well. Okay. Okay. So this also is pretty straightforward and don't need to go through it.

[00:09:53] The only remark here is that, is that this part is similar to the one before, but you see here a comprehensive list instead of a for loop, [00:10:00] like in the previous one. A full on for loop. The reason for this is because we don't need to do any processing in the middle. Like here we want to write this in the middle.

[00:10:08] We want to write this command in the middle, but here. We are going to paste into a file. Why do I want to have a typewriter effect when I'm just pasting into a file? So I just iterate to get all of the words in a list as strings, and then join all of these strings together without any space.

[00:10:23] Because remember, the open I model returns the space in the text itself. And then you have a single string [00:10:30] representing the answer of the model. And then that answer, you just put it in the output file. That's it. Okay. That logic is consistent, like that logic will return to us in Discord and in WhatsApp.

[00:10:41] Okay. This is also something to be aware of. I think none here. I was mistaken when I said that this will never apply because apparently because I'm not the one who initially put this logic I believe that occasionally it does actually send a nun to, to its answer instead of, instead of a string. That's just a validation check [00:11:00] for here. So interesting. Anyways, that's regarding this presenter and for other presenters the API and the WhatsApp. I'll leave that for later. The a FI presenters, we also didn't work on that I'm not exactly sure how it goes.

[00:11:16] Neither did I work on most of what I explained here, but at least I interacted with that code. But this code, to be honest, I didn't really. See it in depth. But if we actually see our trusted friend outline Mr. Outline over here [00:11:30] and we see the present function, we'll see that it basically outputs to a c to, to a file as well, or to a CSV action.

[00:11:37] So you see here, there is a CSV, and so at least we know that whatever this file does. It's way of presenting is using CSVs. Okay. Yeah, until it yeah, until it it it tries the road and con Yeah. Continues until finally writes the CS V. And I don't know if this actually points to something that we set or not.

[00:11:57] Put file. Yeah, we said that in the [00:12:00] okay. In the term. Okay, great. I'll explain that in a second. But yeah, basically ayah_file presenter is is just a way to also present to a file. Okay. Like it presents to a file, but with extra parameters. Okay. So now we have two, two logics. Okay. The logic of just a file presenter.

[00:12:16] Just regular. This is the equivalent of the stdio presenter, but just for file instead of terminal. And then ayah_file presenter, which is also presenting to files like or to CSV rather. But with a ca with a catch, like with certain settings [00:12:30] changed. So how do we adjust for this? Or when do we run this or when do we run run that?

[00:12:35] I believe both of them is based on main file. So we run either file presenter or a FI presenter from the main file. Okay. So I'm now finished with presenter explanations graduate as a presenter. We don't use that anymore actually. So this we abandoned that logic because it's it it takes up a lot of big size when we try to run the pipeline of GI actions.

[00:12:55] So we neglected, we just abandoned implementing UI for, [00:13:00] we don't need just that on that. Anyways, so that code is actually. Yeah, I think we could de delete that code now. And discord presenter, the same thing. But if you know the API of Discord, then you understand this. Like I don't need to explain what is message author or what is message content or mentions like this.

[00:13:18] If you look at the API on the website of Discord, do you understand it? So I don't think there is anything that needs to be explicitly said here. It can be understood from the code. [00:13:30] Yeah the WhatsApp presenter and the API, I'll leave at the end. So I will now, I'm now finished with presenters regarding the main file that I was talking about.

[00:13:38] I just wanna mean just wanna state that I'm done with presenters and go ahead. Where's the main files? 


## [00:13:51] Using the Typer Library

[00:13:54] Okay, so for here, how do we run either ayah_file presenter or file presenter [00:14:00] using a class called Typer? It's a cool it's cool. Library. Sorry. Library called Typer. Yeah, typer. Build great CLIs. Easy to code based on Python typings. So as it says, instead of using the boilerplate python code, which I can't remember the syntax, like just can't remember exactly long lines of saying, yeah, we want to read an argument x from user where it's help string is, et cetera. And it's default value is whatever.

[00:14:22] Instead of all that syntax. Its syntax now is similar to Python, where we just define a function. We called it mean here. We say it's parameters. [00:14:30] We type hint each parameter. Like we say that this, we expect it to be a string, et cetera. And we potentially add as a default value this typer object called button, okay.

[00:14:41] Or function actually, which basically says. What we were supposed to say in the boiler code below. For example, if we now run this script from the command line and we don't pass any arguments, then you assume that this argument called a mode is said to its default value, which is false.

[00:14:59] Okay. [00:15:00] Okay. But how do I call this argument By using this AI mode written like that. And what is its shortcut? Is this, I think you understand now. And what if you write dash itch to get help for this file? You will get this explanation for this parameter. So it's a very clean way to write this interfacing.

[00:15:16] And you can see more about the details here. And I explained the overall logic from this, the aims to process input, file engineer eight answers. It's, this part and specifically this part can help you out with that link and understanding the syntax of this [00:15:30] library. Okay? So don't get confused about all this is literally just parameters.

[00:15:34] Like literally if you press this button here to just collapse the option definitions, you'll see that literally these are just parameters to the main function. It's just there's nothing else. Okay? And so this gives us a bit of flexibility. To change certain parameters when running the script.

[00:15:50] Unlike what we're doing in the normal present present a clause and . What we're doing normally in the main stdio just run the script and then we have the anari element ready for us, and then we [00:16:00] ask, and then it answers. That's it. But here we can set arguments that will help us out.

[00:16:06] You can search for these arguments and this usage. Most of them go to the to the I Mode presenter. So if we set the I mode argument true, right? I think to true, yeah. To to true because it's a boolean, then we will run this. Okay? We run this ayah_file presenter class elsewhere. We run the normal file presenter.

[00:16:25] So I think it's very straightforward what's happening here regarding what ayah_file does. [00:16:30] I think it runs logic related to the Ansari workflow, which I'll explain later. So it's for testing specific things in in Ansari. But if you don't want to test that pipeline, you can just run the normal like default mode, make ayah mode equal false when running in the terminal.


## [00:16:46] Outro

[00:16:46] Okay, so this is regarding the main file. Main stdio already explained it. Main Discord is literally the same as main stdio. We just get the agent of Ansari. And then present that obviously with any [00:17:00] credentials related to discord, like the Discord token, et cetera. But nothing special. It's just the same logic. 

