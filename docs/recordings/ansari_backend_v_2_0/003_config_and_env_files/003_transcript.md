# Ansari Backend V2.0 - 003 Config and Env Files

## [00:00:00] Introduction and Setup

[00:00:00] Hello? Hello. Okay, this is a continuation of the recordings. I think I don't need to do this greeting each time because we are going to concatenate everything together. But bear with me. Um, Now we have okay, now. 


## [00:00:19] Exploring the Config File

[00:00:19] We will go to the config file and the n exemplifies. So let's go through this bit by [00:00:30] bit.

[00:00:30] We are using a library called FastAPI. Okay? REST framework, okay. web framework and to receive the requests from the front end ui. Okay? So, FastAPI has a lot of documentation and I suggest seeing the main the main the official docs for it. Official documentation for it. It's really it's what is this?

[00:00:54] Yeah, sorry. It's really clean and I liked it. And it's weird for someone to say that he [00:01:00] likes documentation and that he's having fun reading documentation. But really the, the team there did a fantastic job at documenting how it works. 


## [00:01:09] Understanding FastAPI Settings

[00:01:09] And one of its features is uh, settings and uh, settings here is is a class that is responsible for taking different values from different places.

[00:01:21] What do I mean by this? Let me explain with an example. We can run the server, the FastAPI server by running a command here and then passing [00:01:30] arguments, for example an argument called debug mode and give it values.

[00:01:33] Okay? Now. This is one place where we can get like you, you, you wanna say it constant? Okay. You can say environment variables. You can say like just configuration settings. Okay. Like configuration setting. This is one place to get them. Okay. From the command line. Terminal arguments. Okay. So this is this is what this means.

[00:01:54] Okay. 


## [00:01:55] Environment Variables and .env File

[00:01:57] And you can get it as well from, other places. Let me show [00:02:00] you an example that you're probably familiar with. The end file. I'm showing you an example of it. So you can here set the keys that you want to be read in the environment while the code is running. So again, you see the bug mode here.

[00:02:13] Okay? So this is another place. So there are multiple places. I'm not going to explain all of them. What we are interested in understanding is. That there, there is precedence. Precedence, meaning that if I set this here and then set this in the n exemp [00:02:30] file this will take precedence over the n for example, file.

[00:02:33] So meaning more priority, this will be prioritized. Okay? So this is another thing to take in mind. What you need to understand from, from all of these is that what we're currently using is the following. 


## [00:02:45] Loading and Using Configuration Values

[00:02:46] We are using .env file. .env file. So we're loading the values from here, from there into, into this class.

[00:02:53] So you're going to see here a lot of keys. Okay? These keys, most of them are loaded from the dot end, for example. So [00:03:00] here you'll see debug mode. Okay? So debug mode here. I, I got that from the digital example. Okay. It, this is done automatically. So when you just run the script in main, a P point and, and the, and the, and the Fast API server like runs in the background and it and it sees this base settings from the identical class.

[00:03:26] It runs that as well. You see that, we see that it [00:03:30] checks, it checks for these values. So it see that, okay, debug mode and sees based on the list above, where can I find this value. And it goes through this list and it finds it in .env file because it reads in the I think we, we passed it here.

[00:03:43] Yeah. The in file when we, we con fill it, settings, config, we, we specified that it is found in here. And this is respective to the root. So that's why we put the file in the root. The root file here will be in the root. Okay? So again, adult file is literally the same as this, but with the actual values, [00:04:00] secret values.

[00:04:01] So it'll be similar to this, but it'll not have this export. Okay. So what does this export do? Basically, there is another option. This is option info. You can you can run this as a script, okay. In the terminal. To, to take line by line as a command and run that. So this is a command in Bash saying, export this key.

[00:04:23] So it'll export this key to the environment variables of the environment, okay? That's currently running. [00:04:30] So if you decide to go with that path, then you will be abiding by this rule. Which one? This rule? The environment variables rule. Okay. So these are general environment variables that's available and how can you see them while the code is running?

[00:04:43] You can do something like this import os and then os environ. This will be a dictionary, I believe. Yes. Containing all of the environments currently based. So so, so, so. Suppo, assuming that you decide to go with that other path of [00:05:00] running this script, this best script, and running these commands one by one in the terminal.

[00:05:04] Then you should see when you, when you run this, when, when you print this, you should see normal environment variables that are always there when you run any Python script. And you should see as well the custom keys that you inserted here. Okay? So but we don't, we will not go through that with that path, and instead.

[00:05:23] Or I personally instead just take the stuff here and put it in a dotenv file. And when I do that, I remove the, the export [00:05:30] because in the dot file, you don't need the export prefix. So and I believe you can put some anything on the side here. So this, this is taken as well in the normal dotenv file when it's read.

[00:05:42] So it, it'll take this as a key and then what is after the equal will be taken. Okay. That's what I understand. I'm not sure if this is correct though or not because I, I, I think I faced this issue before. So you can put comments on the side like this here. In the actual end file you have to put it if you are going to put it, put it on top of it [00:06:00] or below it, don't put it to the side.

[00:06:02] Okay? And another thing, this is this string is optional. So for example, for example, when I say here two, I can also, I can also write it at, at like this, and it'll be read as a string as well. Okay. So, but we, we, we put it for clarity. Because everything here, I, if I remember correctly, is initially read as a string.

[00:06:23] Okay? So if you just use the grow traditional method of of, from NV library, [00:06:30] import load nv, and then you load n you will see that and then you try to, to call, for example. And then you try to call is the get good get in the bug mode. It, this will return true string. Like even if you put this as a true without the, without the double strings.

[00:06:50] Okay? Even if you do it like this and you, and you print this, it'll still be decoded as a string. It'll still appear as a string because that's how it internalizes the, the, the, the [00:07:00] file, how this file gets read. So this is something for you to, to, to, so this is, it will be a string as well. This one will be a string.

[00:07:06] And then you, you can do, if you are going to get this here, for example, you won, you won't need that. But this just a for you to understand and you get that as a variable. Inval. This will actually not be an inval. This will be a, this will be a string. And you'll have to do something like this to convert it to a, an same thing with debug mode, [00:07:30] debug mode it'll return a string was true in it.

[00:07:35] And then I think, I think if you, if you, if you put this and, and here a string was true, it'll be a true value, but I'm not sure about this. I'm, yeah, I'm not sure. Yeah. No, it doesn't do that. So apologies for this. I thought it would apply the same logic, but apparently not. But you get the idea. Okay, so so this is something for you to be aware of.

[00:07:56] Of how to get environment variables at or configurations [00:08:00] into the environment. Okay. If you want a description of what the use of each configuration here is, then there are two approaches. First, approach growth, control, shift F global searching here. So for example, in here I can control shift F and I can see what it got mentioned.

[00:08:16] It got mentioned in, in all of these for example, let me see here, main, so if we're in debug mode right now. And this file is the main entry point. Then we will run the UV server, et cetera. So you can see the importance of each code, [00:08:30] but not all of the configurations here can be control shift.

[00:08:33] If, for example, if we see the open I key and we control shift, if that, you will see that it isn't written explicitly in any other file. Exclude over cd, GitHub action file. It's not written in other files. Okay? So this is a problem because it'll make it. Little bit more difficult to reduce its usage, but here we can actually rely on the comments in the example.

[00:08:55] Okay. I, I try to, to put the comments rating how it gets used. [00:09:00] Obviously open I is a clear example. Then, you know from the name that we are using an LLM provider, which relies on open AI model. So we use that key. So this makes sense. Okay. But other things that really don't, don't make that much sense.

[00:09:12] I I have comments like, for example, WhatsApp. Keys here. I have comments for that. Okay. And et cetera. And there is a tricky note regarding the OpenAI API key specifically. I will, I'll get back to this when I explain later files. So yeah, this is the part of [00:09:30] configuration. The, the remaining of the remainder of the code.

[00:09:32] Here is just the default values that we put. So if you remember here, there is a precedence on how we take each, value. Like if we have debug mode in here and in the .env, we will, we'll prioritize this one. So the last thing we'll prioritize. Prioritize is a default field value in the sittings model, which is something like that.


## [00:09:50] Debug Mode and Default Values

[00:09:50] If we go back to debug model, debug mode, I mean you will see the default value that means the following if we do not have this variable [00:10:00] called debug mode, all capital letters, if we don't have that passed in arguments over here. Or exported the via the export command From the example or in file or in, in the remaining of the above, like five settings.

[00:10:14] If you don't have all of that, then this will be set to as a default value over here. Okay. Which is false. Yeah. So I believe, if I remember in the live environment that we have in, in Heroku, we, we, we don't even specify that key. Like that [00:10:30] envi, that key in the environment over there, over hero. So since it doesn't exist there it'll default to false.

[00:10:36] Okay. And so we, we won't be in debug mode in life. And that makes sense. Okay. So this is something same same as logging level. Logging level deal. I believe in life we don't have this mentioned. I think so it defaults to info, which makes sense, not debugging. What else? I wanna say, I think this is everything related to to config feel very, this is when we, when we when we want to get the key [00:11:00] called origins specifically, which is this one which is this one this function.

[00:11:05] Make sure that we obtain it in a specific format, which is a, which is a list. Okay. So it's, it basically says the following, if we have origins. As a string, then convert list, but it's a list. Then leave it as is. For example, if you go back to end example here, you will see that origins is written as a string and between each link [00:11:30] and the other is a comma.

[00:11:32] You see a coma like this. Okay? So this is a string, so. This function basically tells us the following. When this script runs and we check for Origins and we check it in any place like the terminal or the en file or et cetera, we do this validation. Okay? And if it's so it's the thing, like the one that I just showed you, then you should strip by the this split by this this com.[00:12:00] 

[00:12:00] Okay, otherwise you leave it as is. There is all, I think it's pretty obvious this function is where we instantiate that sitting class sitting class that has all the keys above. And we call that function everywhere basically. So this function turns out instance of the savings clause, and we use that literally everywhere.

[00:12:18] Literally the sort of each file, for example, or not the sort of, yeah, when we initialize data, the database clause or the, an sorry agent itself, we pass it, pass it to the initials. So it takes the settings as an initial. [00:12:30] So we, we, we use it a lot. So just understanding this logic will help you out.

[00:12:34] So this was recording the config part and yes. 


## [00:12:40] Conclusion and Next Steps

[00:12:40] Regarding now what do we have here? Regarding, so yeah, this is a config by and and example.

[00:12:49] Okay, I'll, I'll just take a small break and continue the rest of the files. One second,

[00:12:57] what I wanna do, [00:13:00] 9 1 2.

[00:13:01] In the main presenter.

[00:13:03] 

