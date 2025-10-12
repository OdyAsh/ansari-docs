# Ansari Backend V2.0 - 002 Pip-Versioining, CI-CD, Logging (SquadCast Session 2 Take 3)


## [00:00:00] Version Pinning in Production

[00:00:00] I just wanna point out some stuff here in the previous recording that I said in the requirements that the text file I mentioned that we didn't pin the versions. This is not correct.

[00:00:11] This is, should not be the case when we are productionalizing things. But we should pin down versions. When you see this later on, you'll see the official, like the main branch having a pin down versions. I'm still we're still going to commit and make a PR on this.

[00:00:25] Until we do. Expect that this will be found in their [00:00:30] comments file. We just put versions right here. Okay? How do we get these versions? You get them by the following. You see any libraries that you installed, for example, the show, pendas or maybe light.

[00:00:44] Let's example. Here you can see that van, that's the version environment we created and requires, it means the Python libraries that light L needs to function. I didn't write all of these in this file. I just wrote light LLM, and when I PIP installed light LLM, it [00:01:00] implicitly installed all these libraries as well required byAnsari backend.

[00:01:04] This means that Ansari backend here. I guess it means that the users themselves, we ourselves installed this library by writing Pip installed light lm. You can get the version, that's what I wanna talk about here. You can get the version from this part and then you can write equal, and in this version, okay?

[00:01:20] But now when you go back to this file you'll see me pinning down on everything I'm just saying. Just for you to know that's the way that you get them or when you install anything for example [00:01:30] any library like this. 


## [00:01:31] Dry Run and Dependency Management

[00:01:31] But let's make it a dry run. A dry run means that it wouldn't actually install, it'll just give the log.

[00:01:36] That it'll give, assuming that it installed. It'll run, it'll give us this, and then it'll say, would installed, not installed, no would installed because we are running dry run. Argument. So it would install this library because this library is a dependent of the environment name depends on this.

[00:01:53] And then to install var name and this, we can take this version and put equal, and then paste here. That's the way we can pin down versions. [00:02:00] This is something for you to know. And you can see that we changed the file to be requirements.in instead of text. You can see this link to know why.

[00:02:08] But the summary of the situation is that whenever you add libraries, you add it here sorted. If something for example, library called data. It'll be B between B and D. So you add here and then you add its pin from the commands that I showed you in terminal.


## [00:02:22] Compiling Requirements File

[00:02:22] And then you run this command pip compile requirements.in in output file requirements with text. What does this command do? It [00:02:30] basically compiles the content of this file Okay. Into the requirements.txt file. How does it compile it? So the requirements.txt file, you see it got changed majorly So it, it now not only contains the libraries that I installed here directly, it contains the implicit libraries that these libraries installed as well. 


## [00:02:50] Understanding Direct and Implicit Dependencies

[00:02:59] Let me explain again in the requirements within the file these libraries are called direct dependencies. A direct dependency is. Something that we pip installed directly as I've [00:03:00] wrote, I've written here.

[00:03:01] Okay. But second degree or more than that libraries. These are implicit libraries installed by these. Again, another example is pendas. If you see pandas, you will see it requires MPA and all of that. But MPA isn't shown here because I didn't install MPA myself. But if I go back, the requirements, the text here, you can see MPA written here, okay, via appendices.

[00:03:26] So this is automatically created by the command pip compiles that I shown you [00:03:30] above. Okay, this so you do this step each time. Even if you decide to later remove this library, after you remove this, you'll save this file and then you run this command, which will alter this file, the text file, and then the server will hopefully read from this text file.

[00:03:45] And this pin down version will be more since it's more explicit, it'll lessen the possibility of weird surprises coming up. When setting up the environment in the live version. This is the part that I wanted to discuss about the year comes with text flight. This is the third time I'm discussing this.[00:04:00] 

[00:04:00] Hopefully the recording doesn't break on me. Now I wanna show what, one second warning it was in 1150, I think. There is another thing I wanna talk about over here. That is the, one second.


## [00:04:24] GitHub Actions Overview

[00:04:24] The Python app, a m file, the up actions that I talked about. It isn't actually a [00:04:30] CI/CD. It's it's, there's no D part. It doesn't deploy. Okay. So it, what it does, it just install python dependencies, run tests and lint was Ruff, if you remember that. And so if you see here, the last step is this run test using pi test.

[00:04:43] I explained the test files before. So that's it basically. It doesn't cover the part where this code deploys to Heroku server. Okay? So this is something that you just need to keep in mind. And another thing that's also cool is that if you see here any commits in GitHub, [00:05:00] let's take a false commit initially.

[00:05:03] The internet here is amazing. For example, this commit that I tried to make and it failed spectacularly, you'll see all of these For anyone who doesn't know GitHub actions these are based on what we initialized here. We say here the jobs each job that we say here will be, will be written there. In the steps part of the job. If we have a checkout step, checkout the post [00:05:30] report, then you'll see it over here. This will translate to what's being done here. Install uv run these commands to install them, which is just this command.

[00:05:39] And you'll see it's output here. Install uv. Okay. Pip in run. Pip install UV. So this is the command. And it even captured the comment that we wrote here. It's giving us what's happening this is cool for logging. This is done for the rest of, until, until you have uh, uh, linted with Ruff.

[00:05:55] That here as well. And then test with pie. Test the last one. It'll be here as well. Okay. The rest [00:06:00] are regarding the other logs regarding GitHub. 


## [00:06:02] Handling GitHub Actions Errors

[00:06:02] One thing just to take care of in case it you run with this issue again, is that in this file, in this step, if it's called done at the end or if you refresh the page, you'll be redirected to this part.

[00:06:13] If you push any commits here and you see it failed on these parts, then that's okay. 'Cause normally these failed because of a connection error between open AI and the server of GitHub actions. If I core correctly, that's why we have a assert here was 500 instead of 200.

[00:06:29] [00:06:30] Okay. And stuff related to the commands that are related to the, ansari agent, which uses open AI models. Okay? So if you see issues like this, then this is expected, but if you see any other types of issues here, then no. Then you need to fix that yourself. Okay? And if you remember when I said Ruff, enforces guidelines like the maximum character length in a line. If you exceed that. You'll see this issue. So if we push the code while it's like this, you'll see an error occurring. An error occurring where [00:07:00] occurring here "lint with Ruff" part.

[00:07:04] In this part this didn't do anything because we, it runs the check command correctly. But normally you see an issue here stating where the issue is. Okay? It'll say it something like this. It'll say that line too long and it'll give you the position where the issue happens. So it'll tell you 19 it tell you the fine name, and then it'll tell you 19.

[00:07:22] And then it'll tell you the part where it, where the problem occurred, which was. Column 128. So you'll see something like 19 [00:07:30] column and then 128. This is how you can read the errors if they come up. Okay. That is something for you as well.

[00:07:38] One second. Okay in this spot? I think, yeah, I think that's that's all you'll see also here as well. Colors, beautiful colors where okay, these are beautiful errors. We don't want that. These are done using the logging modules that we have. I'll explain that later.

[00:07:55] But essentially GitHub actions has specific variables, environment variables related to it. [00:08:00] That that we could use for our advantage. So for example, when I'm here defining my logger, in the logger file, you'll see that I'm adding configurations for it. And one of them is this environment.

[00:08:11] And this is the function to get the environment variables. I'm saying if there is an environ variable called GitHub, actions then make a rise. True. Okay. This is the thing. Here and only when it's running here, there will be a GitHub. There will be an environment variable called GitHub actions, and this will turn true.

[00:08:27] So it'll be colorized. So it'll colorize over here. [00:08:30] So this is something that you can use to advantage. Another thing related to GitHub actions is the uh, the "testserver". So if I control shift F on the server over here, you'll see that, that I added in one of the origins that is allowed to buy to, to go through.

[00:08:47] Our code is testserver, okay? Because this is when this is done, when we are deploying to GitHub, so to, to make sure the CICD of GitHub actions is allowed, which is, again, not A-C-I-C-D, but you get the point. So these [00:09:00] things you can keep in consideration if you wish to adjust stuff. That relates to GitHub actions. Yeah. And now I'm finished with this part. I'm sorry if I'm talking a little bit too fast. It's because it's like, um, can't remember this, the too many takes for this part. So I just wanna get it over with before I go to the main logic that we have overview of those.

[00:09:22] Yeah. I think now we can go to the source files, which is the main logic. That we have [00:09:30] one second. Okay, let me go to, ansari. Log file first, I'm sorry. 


## [00:09:39] Logger Configuration and Usage

[00:09:43] If you're seeing me look away, like when I'm looking at this direction is I'm just looking at the second monitor that I have to make sure I'm tracing what I'm doing in the video.

[00:09:49] For later editing. Let us go to logger. ansari logger. So I was just in this file a few seconds ago. This does [00:10:00] nothing special. It just uses loguru library instead of instead of the standard logging. And you can see why I made this decision here. In this thing. Okay. And this is for documentation.

[00:10:09] And it's pretty simple syntax. I don't need to explain it. You can read the parameters and the usage here. There are coloring colorings available. So the coloring you just saw in grab actions, you can also see that in the terminal as well if you run if you run the the server here Okay.

[00:10:22] In the logs. So that's something that is useful. Another thing that I just thought of right now. 


## [00:10:29] Logging Exceptions

[00:10:29] [00:10:30] That I didn't plan to say that. I think this present in, but not in the standard logging that you can log exception. Like not just an error. Like normally when you have a try accept, you have a try accept here Uhhuh except exception as.

[00:10:46] Exception as e you will have you will normally log error and you say your details and then you put the error or or the function that gets the trace back of the error. And then you print that here. But there is a [00:11:00] cool way to do this is that you can just if you use exception, then you can, you don't have to say the, see the trace back.

[00:11:06] You can just say the final string of the final error that you caught. Okay. And if you pass this instead, in an exception, then this will this will automatically, after this string, it'll print a new line and then print out this, the trace back of how this error. Was caught like the, all of the touchback of the functions, which led to this issue.

[00:11:28] And it stores extra metadata [00:11:30] that helps in debugging. It's really cool. So that's also something that you could use. 


## [00:11:33] Conclusion and Final Thoughts

[00:11:34] We didn't use that yet in the code, but something that I just remembered related to the library of logo route that I really so this is all with the OO library and now with the config logic the config logic will take a bit of time.

[00:11:49] So I think I will take a small break first.

