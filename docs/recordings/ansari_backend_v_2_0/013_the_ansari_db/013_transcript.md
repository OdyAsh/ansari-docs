# Ansari Backend V2.0 - 013 The Ansari DB


## [00:00:00] Introduction and Overview

[00:00:00] Okay. Hello again. I gave some thought into this and I found that I really shouldn't explain Ansari DB that much because the database logic is in continuous change. So probably when this recording is out, most of what I'm saying here. got changed. Probably I'll give some some examples and how to trace things so that you can have the tool of how to navigate around the code base rather than actually getting attached into the syntax of this current implementation.


## [00:00:28] MessageLogger and Database Structure

[00:00:28] So let's start with the MessageLogger. [00:00:30] Okay. A simplified interface to ansari database so that we can log messages, IE save messages to the database without having to share details about the user ID and threat id. Let's just dive into the methods and see where they're called and hopefully you get the big picture.

[00:00:44] So you have here the in it function. Okay. We're passing to it, the user ID three id and WhatsApp. This is just a a ion to say, where we will store the info. Because here's the thing, let me get this out of the way before we start the session. [00:01:00] 


## [00:01:00] Handling Multiple Message Sources

[00:01:00] So currently we have multiple sources Okay.

[00:01:03] Of of messages. So we can get messages from the, ansari, the chat, the main web application that we have, Ansari the chat the website and. And that website the flow that it'll follow are these tables, the tables below, and the users' messages, feedback, and all of the, all of these tables.

[00:01:21] And then you have these three tables, users, WhatsApp Threads, WhatsApp and WhatsApp. And to be honest, this is basically just a duplicate of that main logic here the threads and [00:01:30] messages and users, but for WhatsApp just to distinguish the two users from each other. And so this isn't really the best way to do things. Because we, in the future, we may have more than like this already duplication, but in the future, we can have, maybe we decide to store the Discord users in a specific ING database. And and so that's an extra source And Et cetera, et cetera. So we, we'd rather have something like a flag in these tables called Source, for example.

[00:01:57] I call 'em called Source [00:02:00] which we can debate the implementation later, but for now, maybe it can take something like a string that says, ansari, the chat if it's from the web and can say WhatsApp, if it's from WhatsApp, et cetera. That I think would be better. So That in this column we can just filter by that column, that source column to get the data that we want.

[00:02:16] And that's the thing. So maybe probably when this recording is out is out we would've implemented that and then you'd see these tables, these WhatsApp tables not here anymore. So yeah, so for now, since this is the way that things are for now then [00:02:30] I I made here a boo and called to WhatsApp. That says, based on where this message, local clause is instantiated, this will be true or false. And if it's true if it's true we will we will use the appended message, WhatsApp function. If it's false, we'll append we'll use the normal appended message and again, very repetitive logic. Here you see in the code that we have in, Ansari, db, that if you see the outline here at the bottom left.

[00:02:54] That a lot of functions were written before, and then they have the equivalent WhatsApp version. So register, function [00:03:00] it, or method, it has a register. WhatsApp method account exists. Same for WhatsApp. WhatsApp retrieve user info and then WhatsApp. Create thread and therefore what, and so on.


## [00:03:09] Refactoring and Future Changes

[00:03:09] As you can see, it gets very repetitive and we need to refactor this. So that's why I decided not to go into the details of the database because probably a lot of these stuff will change later on. And so this is just a high level overview of the message local. Where is it used? Let's see, where is it called?

[00:03:27] You can see it's called for example, in, I, [00:03:30] ansari.py. We define an instance in, Ansari We passed away. One of the, one of its attributes is the, is an instance of MessageLogger. And it's later used. it's later used. This, I take this for example, except Mr. Logger in the set MessageLogger function. So yeah, so this is so I don't know, like there are two ways to to add a message broker to the Class E, either in the in it method above when initializing the instance or via this [00:04:00] method. So anyway, anyway, we'll work any of the two ways we work. And then what else do we have we use? Yeah, we, I think if you control F Yeah.

[00:04:12] I don't think you'll see. Yeah, you'll see it here. 


## [00:04:14] Message History and Retrieval

[00:04:17] So in process, message history, if you remember that log the assistance response to the user scoring thread and database. So once the assistant finally. Returns the response, if you remember that logic that'll not go through again, where we do the four ch in each of the trunks of the response of [00:04:30] the LLM. And then we add each word to the final string of the the final response that the LLM returns after we stream all of its words. And so the final word, like it's the final paragraph, the final return, the value by the LLM, we will store that in the database. Okay? Just for you to imagine things. Visually this function, the dot log function says that I wanna store the content of the message, which is word in this case, and say the rule who wrote this message, which is in this case is assistant. [00:05:00] Okay? Because the LLM and so in the log here you will see that that the FLS that I just explained. And so I just want you to visualize this append message because append message here, it inserts into the table messages. The third id, user ID role, content, tool name, and two details. What we care about in this case is the role and content. Because if you remember the girl paint drawing that I made, the rectangles and all of that, we have the message structure the list of dictionaries, and each dictionary is a role. and the content. Okay. Role key and the content [00:05:30] key. That's the basic structure of the message that we have either a user message or an assistant message. And if you remember, we said that the tool message has an extra way of being written. We write a tool message , in two messages and internal message and a, and an actual tool message.

[00:05:44] So that's why we have here the tool details. Tool details. You will see that if you actually follow this along. Follow along. it here, then follow along in the tool details. In the log, you see where it's called, [00:06:00] called, multiple parts. So I'm interested in the one where it has tool. Okay? So you have here. Log the tools response to the user's current thread in database tool tool alpha string tool name tool details. So if you see tool details. here is the is the two dictionaries that I told you about. Remember in the recording when I told you about that the tool has two two dictionaries dictionary called internal message and the actual tool message.

[00:06:23] These are the ones, okay? So I store them like this. Okay. This is Dictionary and this is dictionary. And I store that, all of that in a bigger [00:06:30] dictionary. And I named this Internal Message Dictionary and I named that the Tool Message Dictionary. Okay, so how do I unwrap this? Okay, let me rephrase the question by giving an introduction first to what I'm trying to say.

[00:06:42] So we now know how this dictionary of the tool response gets stored in ansari database in the messages table. Okay, great. So here's the thing. Now if you, if we go back to the to the data model, we have the messages here. Okay. Here. It's like this. Okay. And now [00:07:00] you can imagine the the messages as rose.

[00:07:02] Okay. For, let's take a specific thread. Id for example, by the way, a thread id, again, if I didn't explain it before, is in the front end when the user opens a new chat, it's basically a chat container. That's what we call a thread here in the database. Okay. If the user opens a new chat and then he types a message and then, Ansari responds, and then he typed a message and then answer the response, et cetera.

[00:07:23] All of these messages. Or in a thread. Okay. Or in a chat container. That's what a thread. means in in, in the terminologies of this [00:07:30] code base. Let's assume the same thread idea here. You can visualize now the message history as a list of dictionaries, okay? And in here, in database, it'll be rules.

[00:07:38] A couple of rules, okay. Database rules. And each row has this info and we care about the info of the role and the content. And we care also about tool details at the end here, if we're going to get if we're going to add the messages from a tool. So you can imagine it like, so before I, I show you the function.

[00:07:53] You can imagine that the way we retrieve a thread history, we retrieve the chat the message history list of messages [00:08:00] is that we say, okay, select all the messages. Related to this thread ID and user id. Okay. Return these messages to me and and create dictionaries from that, that consist of a role.

[00:08:14] And each rule consists uh, each uh, dictionary consists of a role and a, and content keys. Okay? That's an structure that you know about. You can imagine that right now, and I'll show it to you in a second, but just imagine with me now, how will the code write? That I, if you encounter the role [00:08:30] tool, then take what's in tool details, because now the the type of message of the user and the assistant is flat, it's just a flat dictionary.

[00:08:39] It's just a dictionary of role and content keys. But the type of messages from tool is a, is like nested dictionaries. It says dictionary that has two dictionaries, and they need to unpack these two dictionaries into the message history. So how do we do that? If we go back here to answer your question, you, we need to go to which function?

[00:08:58] Let me see which function?

[00:08:59] [00:09:00] here in the answer database. I believe it's get all threads. Okay, so you'll see here get all threads or not gas. No. Get thread, lm, I think, yeah, because get all threads is it will just get all the possible chats that the user can open from. So if, remember in the front end you have the left like sidebar where you say you have a chat a date yesterday, and then another chat at whatever.

[00:09:26] So all of these are the entire thread that you have. So this function [00:09:30] will get you all the threads ready to you to to, this user. Okay? So that's the use of this function, but no, the function that I care about, I think is get thread. Lm Yeah, retrieve all the messages in the thread in a single thread, because all the messages, this is designed for feeding to an LM since it includes two return values.

[00:09:45] So let's go by this function because it's an important one. We select the role and content, and two, details from messages so you remember the role and content is for the basics type of message. The message was a dictionary consisting of the two keys. Okay, so this is obvious, and we get the two tool [00:10:00] details.

[00:10:00] Let's see how we use this specific column. Okay. So we run the query, okay? And we also select from select the name from Threads or ID and user id. That's another command that that we run. Okay. To and so this command will run. and give us this result, and this second command will run and give us this result.

[00:10:18] Okay? We will say first if the if there's no thread if no thread return, then incorrect user ideal thread. To retrieve the chess history. Four. If not, we could we'll do the conversion and this is the part that I care [00:10:30] about. We get the third name. Okay. Which is, which appears in the front end and the left sidebar.

[00:10:34] Okay. So we have this convert message. And this is a function that somehow gives us the required dictionary or dictionaries and extends the messages list with them. Okay? So you can imagine the final outcome of this is a list of dictionaries, and that's what the model expects.

[00:10:51] That's the message history that I kept telling you about, consists of a list of dictionaries, is dictionary is a message. So this is what we want. Okay? What, what happens here? [00:11:00] Let's see. We say the following. If the message has a lens of three and message two exists at the third element is not known, so what do I mean by this?

[00:11:10] This part, if we go back here in the message itself. So the message itself is an integral either like a table, a top of whatever, because database rule returns topple offings. So if we go back here in database row, we're saying the database row in result, which comes from this part, which is from this select\_cmd, which is this.

[00:11:29] We're [00:11:30] saying if the lens of is three, like the lens of the current row is three, which should be the case because we're selecting three columns. Okay. And that's an important part, the me the message to the third element exists, is a, this means it's a non falsey value. Like it's not non, it's not false, it's not an empty string, whatever.

[00:11:48] And this third element is the tool details column. Okay. Because 1, 2, 3, this is a third element. Okay? If the two details exists, okay, if it's not, none. In the current row. Then we get it [00:12:00] here, and then we have the two dictionaries that we want. If you remember, I told you about the structure that we have in two details.

[00:12:07] When I stored it in the database, I stored it like this internal message and tool messages. So we are extracting them back from these same keys. Okay? So here we get the internal message, and here we get the two message, these two variables or these two variables, okay? And we now get these two messages. In a dictionary in dictionaries, and I put them in a list and I return that list. Okay? Okay. If not, like if [00:12:30] this is not the case, if there is no tool details in other words, if the message is from a user or an assistant, not from a tool, then we return the list, which consists of only one dictionary.

[00:12:38] One might ask, why do we return a list even though this is just a single dictionary? Because here, if you go back to the logic where is it? In extend, that this is an extent. What does an extend mean? Extend means that we take the list or Iterable here and we extend it. We take each of its elements and put it [00:13:00] in the original of object that we want to edit in.

[00:13:03] So let me let me tell you an example, a very quick example. 


## [00:13:06] Practical Python Tips

[00:13:06] For this, if you can't visualize this, it's also a cool thing to do, by the way, whenever you are confused about python, syntax or whatever, you can just run a python, and turn it and try it out together. Together just to see what works and what doesn't work. So if we say a is sorry. A is let me see. It's one and two, just a list of of lists of integrators and then three, four, okay. So this is a. [00:13:30] And then you have b Okay. Equal empty list. Now, if I say B dot extend a, okay. What do we get? Okay let's do actually the normal append that we are used to.

[00:13:46] What do I wanna say here? No, I wanna imitate the food loop above. So if I say for EL element in a, and then I say B append. [00:14:00] Okay. We get okay. We and I say B. We get one, two, and three, and four. So what happens here? The first element was this one and two. So we appended one and two to B, and then the second element was three and four.

[00:14:15] So we appended three and this list to B. So now B is similar to A. Okay? But what will happen if I do the same thing? If I do the same thing and I define being response, and I start the Adam and I say, here [00:14:30] extend. Okay, what will happen here? When I say B, sorry, say B is, see what happened here. Let me explain here. 1, 2, 3, 4. What happened is that in the first one we have el equal to the list of one, two. We extended, IE we extracted, like we unpacked The iterable that is in right now is a list. So this is an Iterable, it's an Iterable type, something that we can iterate on. So we extended that.

[00:14:59] To its [00:15:00] inner elements, and then we added each of these elements to B. So that's why in this four loop iteration we added one and two, and then in the next iteration we extended, we extract the three and four from here and added them individually into B. So we get this. Okay. So this is a summary of what's happening.

[00:15:16] Sorry, I I took so much time to explain this, but hopefully you can visualize it now. And I wanted to do this explicitly because it, this way of thinking will help you out of just opening up the terminal, trying something real quick to validate your thinking. A way of thinking. Another easy way is [00:15:30] to just create a Python file.

[00:15:31] I dot IP, I and B file. And and try what I what? I didn't determine it here. And actually, ansari I, know I know that I'm going off topic a lot here, but because these are useful tips in my opinion I believe in Python in Visual Studio Code if you do something like this, okay? This will behave like a cell, like a Jupyter Notebook. So if we said here what we want the same example that I wrote in the terminal. But let me write a simpler one. Just hello. Okay. Without even the word. [00:16:00] And then we run it. See what happens. It already tries to run Python in this part only. I don't, yeah, it needs but it needs to install an IPI kernel. So this is this is the only restraint here. I can say select another a Python environment, which has this kernel, okay, so I just, in here I may select maybe mini, the normal mini conda. I think this has a notebook installed, like a kernel installed, so I can maybe use that to run.

[00:16:24] No, I, it doesn't have it this well. Okay. So this will, to be honest, this tip is very useful if you have [00:16:30] in the current environment IY kernel icon installed. I'm not I'm not gonna install it for the sake of time and because the internet here is awesome. Yeah, but if you have it, then it'll help you out.

[00:16:39] You can simulate what you're doing internally here as well, and you can change these as notebook sales instead of creating an do IPI and B file. So hopefully this tip is useful for you. I just wish I could have actually. Made this example to the end, not going to install Apple. Hopefully you understand now how we get the messages back from database as a [00:17:00] message history and then we feed it back to the LLM. Okay? And again, for you to visualize this, when I said the get thread get thread l and m, this one, where do we call this? We call this here in the ad messaging.

[00:17:13] The main API, we say that this is a history. With that gets read them. So this returns a list of opportunities. Okay? And this is the history itself. Okay. It returns. Okay, wait, in order for me to be concise. It returns. It returns a dictionary [00:17:30] of thread name, just the thread name that appears on the front end.

[00:17:32] And the messages. And this messages is a list of dictionaries. This is the actual history. Okay this is just me being very concise. So here in history, we use the messages here. This one, if you see this, we append to it the user message, the final user message. And so the history is now complete with the latest message that the user just asked before in the front end.

[00:17:52] And we. Pass that entire history to the presenter complete. The presenter complete. If you remember instantiates the, ansari Agent and the, Ansari [00:18:00] Agent now has the entire message history, so that's why it replaces its old message history with a new one. And we set up here the message log, which I explained is responsible to store the remaining messages that, ansari, sends.

[00:18:12] Back to the database. So hopefully you can see the entire loop like coming together. Now if something doesn't add up, you can trace the code again yourself, but it's not really that, okay, it's complicated, but it's not that complicated. Okay this was the main thing that I wanted to explain was, ansari database, because I think this logic will not [00:18:30] change. That much. I hope other parts here that will come and go. Okay. Like the way we write these queries or the what we're using maybe even the, database, the post sql, maybe that will change as well. I'm not sure yet. So yeah, this is what's happening here. I think that's all for on, Ansari database that I will explain. And and yeah, when you see this again, you'll probably not see the, to WhatsApp. You'll probably see like here maybe like source or something. And that will be a string instead of a bullion. And based on that string, we will we will [00:19:00] run specific queries for specific tables or the specific table, but on the source column and we will change.

[00:19:05] That's why I didn't explain in depth what the queries itself does. Okay. I just give an example of the guest thread element for you to visualize how we turn the message history. One final thing I wanted to discuss about actually. Let me just write something real, real quick. Okay. Okay. Is is okay. Something completely unrelated. ansari now, but it'll really help you out. 


## [00:19:26] GitHub Student Developer Pack

[00:19:26] So I thought I'd tell you about this nonetheless, is GitHub student [00:19:30] developer pack. So if you're a student then you really benefit from this. I, and this. is not, advertising is not anything, this is just literally something that benefited me so much that I thought that I'll tell you about this.

[00:19:39] In here all whenever I need something, I just go to the chat here and ask questions. Okay. And so this is very helpful and I can change the model that I want to use here from a list of models that's available to you. All of these are available to, to use as long as and as much as you want.

[00:19:55] If you are in the student GitHub student pack, okay? And and it's very [00:20:00] great to be honest. You can select here stuff and it'll appear. What the context you want is you can write here like symbols specifying the exact file. So if I say ansari, db. It'll use, or here, Ansari DB class. It'll use, the entire class as reference before answering my question is very great and there is a lot of documentation for it in Visual Studio Code itself. I I love this, to be honest. Extension, it helped me out so much and it continues writing for me. For example, if I and sometimes it deduces what I wanna do and do a similar. Okay, let me [00:20:30] give you an example. If I see a WhatsApp function here, if I remember correctly, if I remember correctly, when I finished when I saw register here and I just did a diff and register register WhatsApp it auto completed. With the implementation based on what, what was above. Okay. But I'm not sure if it'll work.

[00:20:52] Yeah. I'm not sure if it'll work now or not, because again, the internet is not the best. And so it just continues implementations for me. And so that's very that's very [00:21:00] useful as you see the autocomplete that I just made. And it does more than that but yeah. See, like here, it just, it, it implicitly took what was said before and, provided me a function similar to that, but for storing in WhatsApp, obviously it can have here, so you have to double check it, but it's very useful. The inline chat is useful. The chat at the left here is useful. I love this. You should try, if you can sign up in the student pack, if you still in university or school the TA wave verification and in email related to it or whatever, you can sign up here.

[00:21:26] It offers a lot of a lot of tools in all offers [00:21:30] here. One of the most important is a GitHub pilot that I just showed you, but there are other important stuff as well. You can get a free domain for a year. You get stuff on Microsoft Azure. It's like a hundred dollars credit. It's amazing, to be honest.

[00:21:42] A lot of services that become free or free for a certain time for you, and it is very great. So that's one last thing I wanted to talk about. And one of them, one of them, one of the great features. 


## [00:21:54] GitLens and Commit Messages

[00:21:54] Is Git lens. Git lens here. If you know this is a very great extension to see details [00:22:00] about the GitHub and the commit graph and all of that.

[00:22:02] What I love about it the most. It is an experimental or, or was an experimental feature is now, I think, became a stable feature for it stating what you can write in the commit message that you do before pushing into GitHub. So here, for example I made this change to do now as I remove this to do and this import was added at the top. So if I go here and then, actually, let me show you something first. If I go to settings. If I go settings and I type [00:22:30] Git lens. AI commit message, for example, commit message. I see here generic commit messages enabled. This is a preview, so this is not established yet completely stably, but I have this enabled.

[00:22:43] And then we see, we say here the custom instruction. So I say use a conventional commit guideline as in here to format the com to format your response. And in the details section, try to be more verbose. On what has been changed. So this is a custom message that I wrote, and the link that I provided is a list, is a link on how [00:23:00] to properly like write commit messages. Okay. With examples. And I can I think it's better because I don't think it accesses the web. So I think it's better for me to take these as an examples and pull it here. Anyways, when I set these two stuff up in the settings and I come back here, okay, I remove this. Okay. And I go here. So this is the current change that happened. Okay? These two changes only. So if I were to commit this, and I go here and say, control shift P and I say gitlin generate, commit message. Okay. It'll give you a prompt to [00:23:30] do it via GT or whatever you say, accepting trust it and whatever. And it gives you this removes on news to do comment and adds test and printed statements.

[00:23:37] Remove and updated. Do code from the file. Edit this to print statement at the end of the file for debugging purposes. I'm actually not sure if I did this or not. Let me see. No. I only did the to do. And the UID, there is No. other changes that was made here. So actually this was hallucinated.

[00:23:53] Okay. But this was not it's useful for you to just do, but it actually, the first time that hallucinated with me, like normally when I do a couple of stuff, [00:24:00] it adds them all here together in bullet points. This is the first time it did. But as in any LM you have to double check. It doesn't hallucinate.

[00:24:08] And it's very just a quick way to write, commit messages instead of seeing the changes one by one. So I recommend this as well. 


## [00:24:13] Conclusion and Final Thoughts

[00:24:13] Um, that was all, That was all, sorry, I got sidetracked here from talking about, ansari, but this stuff all helped me out so much and I thought it was worth your time. Uh, Hopefully you gained something useful from all of these uh, like, uh, [00:24:30] all this time that I've been recording. And uh, And if you have any doubts or questions uh, you know, you know the, the maintainers uh, of this repo So ask away and I'll see you soon In sha' Allah. Bye bye.

