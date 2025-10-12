# Ansari Backend V2.0 - 012 Resources and Utils Folders


## [00:00:00] Introduction to the Resources Folder

[00:00:00] Okay, so we're back again and in our agenda now is the resources folder. Okay. We're currently here, okay, let me zoom in a little bit more. So there are two sub folders here, prompts and templates in prompts. All of these are just things that we import in the code. 


## [00:00:23] VS Code Shortcuts and Tips

[00:00:23] But I will actually take this, chance to discuss some other VS. Code shortcuts and tips. I'm [00:00:30] explaining this file right here. And so we can go to zen mode and see, but in, in text files like these don't forget to, to talk with something called word wrap like this. Control shift P in vs code, and then toggle word wrap. This will make life easier by making the lines in the same line.

[00:00:47] Instead of me horizontally scroll here. The text will go here and then this will remain in line as you see. So this is line still. This this line. Okay? So this is something helpful. And so [00:01:00] whenever I zoom in, that now, so for example here, this will be line 14 only, and if I keep swimming in line 14 will have these three lines.

[00:01:07] Anyways, so this is a cool cool tip. 


## [00:01:09] Comparing Files in VS Code

[00:01:09] Another cool tip that I'll say in a. In a minute is regarding how to compare different files in VAs code. In a minute I'll explain the difference between a and we will see the difference between a and a layman. Okay? And but upon inspection you see them very similar.

[00:01:25] And so when you see any code or even text files like this, you can do [00:01:30] here, control shift p and then compare. Active file with. Okay. You say here this file that you want to compare the current file, I'm currently standing on system message A, so what I wanna compare with, I wanna compare with system message a layman.

[00:01:45] Okay? So I choose the second one and so it automatically got me here. Okay? And so this heat map is very useful because in this heat map at the right. That that all of this code is unchanged or text is unchanged, but the [00:02:00] part of the of change happens here. In that red part.

[00:02:03] So what's red and green here? I know I'm explaining this basic stuff here, but maybe it will help if you if you see the tabs here at the top, you will see a left and the right section. The left section is the file that I, let's say that it's is a file that I want to compare against.

[00:02:20] Okay. It's the initial file that I have. Okay. It is the old file if you say so, and the right side is the new file that I'm comparing against. Okay. And so the old file [00:02:30] system message area is the reference, it's the main reference here. And so we're saying the old file system message area initially contained this paragraph, the person reading your, Ansari, your answer is whatever.

[00:02:40] And then. This got removed. That's what the red here means. These lines 29 to 34 got removed and replaced with these three nine these lines. 29 31. Again, similar line numbers because in the old files system message I, they were on lines 30 to 32. And in the new file [00:03:00] system message, IL Aman the new content is also in lines 29 to 31.

[00:03:04] So that how you can read these line numbers here. Okay. The minus is what got removed from the old file. And the plus is what got added from the new file in, in this, in the right side. Okay. And if you see here, if we remove this and go back to system message A, you see indeed these lines here, the person reading with wherever in nine 30 and 72.

[00:03:24] And, but if you go to system message ayah layman, you'll see that in lines 20. Where is [00:03:30] 29 to 31. The lines changed. How did it change? Okay, so this is also a cool thing to see. Let me know that not to confuse you. Going back to IA first and then compare at the file with system message I you see here in the Red Port.

[00:03:48] In the red part if it's a, just a normal red, not a highlighted red, then this section generally got changed. How did it get changed exactly In the highlighted red. So you'll see here a [00:04:00] well-informed scholar, whatever this was in the old one. And in the new answer the green one, you'll see the person reading your answer is, this part is the same.

[00:04:07] That's why it's highlighted in in, in just normal, in darker green. Okay. So this is similar but who may or may not be a Muslim? Assume the reader is whatever. This is new. Okay. This is new. And so you tell me why did a general member of the public be in, in dark green? This is something with the diff algorithm.

[00:04:27] So you see here this part, the person reading your answer, [00:04:30] this is the same at the start of the old file, but a general member of the public. It is also in the old file, but at the end. A general member of the public. See, you see this part? This is at the end of sentence, and here, this is at the start of the sentence.

[00:04:42] So this is a I think is a cool thing that we don't wanna do. Exact diff differing, like differing between the files. No we want to know what knowledge changed. And so this is what the internal algorithm of doing this different mass matching is based off of. We want to know the [00:05:00] knowledge and the general content that got changed, not exactly the order.

[00:05:03] And so that's why a general member of the public remains in indoor green, even though in the old paragraph it's in the middle and in the new paragraph, it's in the start. Okay, so that's just something for you to, I think most of you know this, but, I thought it's cool to explain nonetheless.

[00:05:16] And so back to the actual purpose of these files. 


## [00:05:19] Understanding File Purposes in resources/

[00:05:20] And each one of the them instead of saying exactly what the purpose is, I will say how you can get to the purpose of the file if you need to do because not all of the files here you [00:05:30] need to understand when you start with the code base.

[00:05:32] A quick way again, is a good old cont control shift, f. This file is called greeting. And so I will type here greeting. You will see here it's mentioned in Ansari.py the greeting. Okay self bind greeting. So here we're assigning the greeting message. So I know that this is a message, this is, I know that this is a prompt and even it's type, this prompt.

[00:05:50] So I know that this basically somehow maybe wrapped in a class or whatever, eventually contains the string that is in the greeting to text. So if I just see where this is used, it's [00:06:00] used in greet function, which is used in here. So for example, main is DIO. We print the greeting, so we understand that this is the initial greeting message when we see the application in the when we see, Ansari, in the S-D-D-I-O in the terminal.

[00:06:13] Okay? So this is the way that you can understand where these files are used. Let me see with you other examples. 


## [00:06:21] Checking Out "news.txt"

[00:06:21] News. News is a tricky one. News comes up in the front end whenever something, like major happens. For example, currently we're working on releasing Claude instead [00:06:30] of OpenAI.

[00:06:31] Is it pronounced Claude? Claude anyways instead of OpenAI. And and so when that happens, we'll probably write a, like a news headline and this eventually get. Sent to the front end, I believe I myself don't know the logic. Let us check together. We'll do it live. If I search for news here, let me see what I can get.

[00:06:51] Okay. I get nothing. I get nothing in this file. Interesting. To be honest, I think I called the team leads in the project and they told me that, [00:07:00] they told me that it's planned to be used, but it's currently not used. I think like whenever there's a new change we write it here and then we read the code so that it updates.

[00:07:09] And goes to the front end and says and then we don't use it back. So that's why the last edit was 19 months ago. So maybe I chose the wrong example here. Let me try with another one. 


## [00:07:19] System Messages and Prompt Engineering

[00:07:19] The system message I and layman, if we at least do the search here. System message I, you saw you see it here in the configuration.

[00:07:29] The [00:07:30] two the I related variables here, point file name. And main file pi, mini pi will see where it's used as a parameter in Ansari workflow. Which makes sense because this actually, if you remember in the, when I was recording the answer workflow we wanted this to be specific to I, and that's why we have a file describing the system in terms of I explanations.

[00:07:52] Again, how did we or the authors or whatever did used how to write this, like why do we write it in this way? This is called prompt engineering. [00:08:00] Okay. So there are quick crash courses you can see on prompt engineering. But but yeah, just stating like what your role is, like who you are initially, what your role is, what your expertise are, and again, we're stating that explicitly here.

[00:08:14] And obviously we can change, like we don't have to write, here's how you work. Like we can say, here's how you operate, for example. This isn't something strict. We can go, we can be flexible here, but essentially. The gist of each part of the paragraph has to be there. So there should be a [00:08:30] part explain how you work.

[00:08:30] You have to, you can phrase it differently, but this part should be there. Okay. And you should say any constraints. For example, and the audience that you're giving to. So here we're saying who the, your audience is, and this is technically the difference between the AI and the AI layman, is that here we're assuming the audience are informed scholars, and so we're giving concise responses.

[00:08:51] In the layman version, we're also giving concise responses, but it doesn't have to be like in depth and and pre assumes knowledge. From the reader side of the [00:09:00] Quran, et cetera? No, that's why we're saying the general member of the public. Okay. Who may not even be a Muslim. Okay.

[00:09:05] So that's the audience part. So the prompt should contain these this general how do I say it? Guidelines, like this should be a part for the audience who are, who is your audience? It should be a part of who you are, your character, your functionalities, your capabilities, your expertise, all of that.

[00:09:20] How do you know which guidelines? You should just make sure they are in the prompt. You can say a crash course about the prompt engineering in that regard. So same [00:09:30] thing with the Claude or what we're experimenting with right now. Message tools. And so these are the prompts. Okay. Passed through to the LLM to properly define it.

[00:09:40] To, Ansari, LLM. In the templates, I think I explained that before the templates, when I was explaining the testing part, we said that this is Jinja and we have here this is j temping. So when we are getting from the CSVs, we can fill. The question and the options based on these dynamic parameters.

[00:09:57] Okay. And the Passeng said this is also [00:10:00] something that we, for some reason we sent the TML back to the front end, but I don't know why this specific port we did in the back end. To be honest, I'm not exactly sure. So this is for the resources part? Okay. And I can as well do utilizations. Since this part isn't really that big. So tools I explained before, resources I explained right now and now with util. 


## [00:10:24] General Utilities in the Codebase (utils/)

[00:10:26] So these are general utilities that or just code that we can use across multiple Python files. So we [00:10:30] decided to put them here.

[00:10:31] For example, the get ex extended origins if we have, I decided to define it here just to abstract a little bit of the logic of, of which origins that we want to get. Okay. So for example, when testing locally I think I change this by the way, in the middle of the recording. So part of the recording, you see this called debug mode, but now I change it in a commit that I just made to testing locally because that's more transparent and clear.

[00:10:53] So when we were testing locally, we have the local origin and there the rock origin and all of that. So I wanted to make that logic a little bit [00:11:00] abstract away from Maine because just saying what's in GitHub actions, what's not, and how to add origins, that's not really related to the job of Maine API.

[00:11:10] Okay. So that's why I extracted that away in this general helpless utility Python file and called that in main API, okay, in the app. Add app middleware here. This is an example. Another example is divided course, divided cores, because we call it in more than one file. I decided to add that [00:11:30] logic away to move that logic away into the i utility that can be used by multiple files.

[00:11:34] I many PI file and the WhatsApp file. Again, defined in a separate file to avoid circular inputs between main python and files. If I think if I define it in for example, if I define it in main a p po and I define this function, I require this function in the main WhatsApp file. If you see here, main WhatsApp, I believe.

[00:11:56] Yes, I require the divided course. So to get the divided course, [00:12:00] if I had to defined it in main API, I would've in the main WhatsApp file, needed to call, needed to import the main API file. But the main API file requires the WhatsApp file in order to include the, if you remember that logic. So the WhatsApp file will call the main file to get the validated course, and the main file will call the WhatsApp file to get the, router. Okay. But then when it so when we are importing that the main API will try to import [00:12:30] WhatsApp. And so when WhatsApp is being imported, it'll try to import main, and that's a circular importing. Okay. So that's why I moved away the validate logic. To be in here the divided course.

[00:12:39] Ansari, I did course to be in the general helpers Python file. So this is another example of a utility that should be placed in here. Check if mostly English. Yeah, so again functions that I even if it's used in only one place for now. Functions that I think, or that you think [00:13:00] will be placed later in multiple places, or that they are general enough that they can be reused in multiple parts of the code.

[00:13:06] You can put him, put them here as a utility. Okay. So here, check mostly English. This is just for me to determine a texting coming from the user or whatever is mostly in English language or not. And based on that, I can decide the language to answer in. But I think I didn't fully implement this logic yet but this is just an example.

[00:13:23] And so this function is general enough that maybe we can need it in other flows as well. Main API or Discord or [00:13:30] whatever, WhatsApp or whatever. So I put it in the general head, proceed. Okay, so that's another example. And get language from text. Same thing. Get language action from text. These are related to WhatsApp for now while I'm recording.

[00:13:43] And they're not completely used till now because I think this was for me let me remember where I used that. Message direction is to get the message. Yeah. Yeah. These were related to to, to formatting the WhatsApp markdown because I okay. I'm going into extra details here because [00:14:00] when the LLM returns the result, it's sometimes in markdown language.

[00:14:03] So in markdown you have, for example how do I say it? The the bold is in double E and double. So you can say a word, a specific word is in bold. If it has a double asterisk sign in the left and the right, but in WhatsApp, I believe it trans, it translates a word to be bold If you have only one asterisk.

[00:14:22] Okay. And the WhatsApp messaging doesn't really support the exact syntax of the normal markdown syntax. So we have to convert. Okay, [00:14:30] convert conventional markdown, syntex to WhatsApp, markdown, syntex. So these are very specific logics for now these functions. And so again, my advice when reading code is that before you just dive deep into everything, understand everything in the code base, don't really aim to understand everything.

[00:14:43] See where the code is used. So here you, you saw that and you control click and you saw that it's only used in this part in the WhatsApp Magnum file. Maybe you're currently working on something related to discord or whatever. You don't need this. You don't need to understand this. Okay? So that's a, just a tip for you.

[00:14:59] [00:15:00] Don't understand everything in the code to do a task. Okay? That was for the general helpers and why it's used. Again, this why let me, instead of horizontally scrolling, let me talk on the word wrap, this why aims to provide general miscellaneous functions that can be used across the code base.

[00:15:15] Okay? 


## [00:15:15] Prompt Manager Overview

[00:15:15] The prompt manager, I think I explained it before, I think. It yeah, file aims to provide one second prompt related functions that can be used across the code base. Again, similar to the general helpers, but for prompting it specifically it load prompt for me versus, as [00:15:30] I mentioned before, and manages them for the Ansari agent.

[00:15:32] That's a prompt class and it it defines the render. Method and all of that. And the prompt manager, all of these are just wraps for us instead of to the, instead of us saying in the Ansari, code itself. Hey, just with open statement, open this text file and read the content and let's go.

[00:15:48] No. Instead of doing it like that, we wrap, we wraps around these clause just to see if you wanna do Excel logic and there is open. You can see it here. Okay. So it is basically just swiping and so that in that wiping, we can [00:16:00] add any additional logic that we want. Okay? So you can see it you can see for example, prompt or prompt measure.

[00:16:05] It's called in the Ansari related files. So for example, here, the prompt measure, pm it's just a wrapper again to get the system profile name in the system message that will be inserted at the top of the message history, if you remember that logic. Okay. In, in, in. Where is it? Yeah, in this part.

[00:16:22] Okay. So yeah, you can just trace the code and figure it out where each prompt is exactly used. 


## [00:16:28] Conclusion and Next Steps

[00:16:29] And yeah, [00:16:30] that was the logic of the utilities. Utilities consists only of these two files for now, so we're good to go. I believe what is remaining for me is the Ansari, database and yeah, so you'll see you then.

