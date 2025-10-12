# Ansari Backend V2.0 - 005 The main_api Python File


## [00:00:00] Introduction to the "main_api.py" Logic

[00:00:00] Okay. So now continuing with the logic of main_api this file has a lot of content let me just read with you the. The overview that I've written here, this file aims to provide a REST API server for the front end repo. Found out this. 


## [00:00:16] Understanding REST API Endpoints

[00:00:16] Again, as literally said we have a REST API server here using first API Python library.

[00:00:22] And it provides some endpoints, which we can see here, outline if we collapse this and see these functions. [00:00:30] All of these are endpoints. Endpoints and what basically an endpoint mean is that for the front frontend code, for this frontend repo, which displays the, I'm sorry, do chat website. If we go to the repo, which I actually have, here locally and then search for a specific endpoint. For example, I search for users register. I will get its location here and if we trace back this function, I think we can trace it back to the part of the page or the sign up page or the sign up button [00:01:00] and the, or register button.

[00:01:01] And pressing that button will run this logic. Which we'll call this endpoint. Okay, so this endpoint is basically this function called register user. Okay. With this URLI searched for this part specifically because the API version two is part of the base RL. So if we, if you, if we copy this and control shift if it here in the front end repo, you won't see anything.

[00:01:25] So that's part of the trick that you normally sometimes [00:01:30] substring, take substrings of the original string that you want to search for in the repo. So, um, Yeah so this is a file which talks to the front end, basically. And this is a high level of the steps that this function has, or not steps, but what this file does imports necessary modules obviously.


## [00:01:49] Initializing FastAPI Application

[00:01:49] Initialize FastAPI application and configure middleware. What does this part mean? It means this code right here. Okay. We initialize an app FastAPI instance in app, and [00:02:00] this app object, we bind to it certain decorators, which which like assign certain characteristics to this instance.

[00:02:07] Okay? So for example, exception handler here. 


## [00:02:10] Exception Handling and Middleware Configuration

[00:02:19] We say that for this application that we instantiated right now and that we're going to run in a few seconds, we want to make its exception handler like this. Okay? You, we, you can see this link for details, but essentially what this does is if there's an error that isn't caught below, like a try, except block if an error.

[00:02:27] Wasn't caught in, in this [00:02:30] blocks and got traced it to the main code here. Then we make sure to run this function initially, which basically does nothing. It literally just logs. It just logs the issue that that happened. But other than that, it just returns the Jason response that it would've returned otherwise anyways this is an example, another example of using app here is is setting up the middleware app, middleware saying the steering, the middleware features. Or parameters. So one thing to note here is that we are putting the list of origins, if you recall the origins. We got that from the [00:03:00] configured by which got that from the in example file, if you remember.

[00:03:05] Here, remember that? So we get that list and we say that if. The request that comes to you in the current endpoint that has been triggered. If that request has a host or origin in that list of origins, then allow it, otherwise don't allow it. And we extend actually these origins using this function or this function does, is is take the original origins again from the settings from the config po, but add to them some [00:03:30] couple of more links with URLs.

[00:03:31] That means based on certain. Conditions, if we're in the bug modes, and obviously you want to add this as well, et cetera. Okay, so what the, this is what this function does and yeah. This is regarding the middleware. Other logic for using the app variable. The fast p instance is the endpoint itself, so this is an endpoint, all of these functional endpoints, so an endpoint basically saying app dots because we want to assign this endpoint.

[00:03:57] Register it with this this app [00:04:00] specifically. Okay. This app instance. So if you control, click here, it'll return us back to this part. Okay? Okay. 


## [00:04:07] Running the FastAPI Application

[00:04:07] Now where do we actually run this? Like, where do we run this app? If you control F and then, and c the sub string of it you will see. You will see it, it run here.

[00:04:18] What is this? The main condition, let me explain it. Okay. So basically we're saying that literally I just wrote it in the comments programmatically start UV server while debugging for [00:04:30] easier control, accessibility. So if we are. Running the code locally. In other words like debugging and developing, then we can simply write Python main main do by here, main_api.py to run it and running it this way.

[00:04:46] Will will, will make us be able to run to run this condition because we, this will make the name equal mean and so we'll be able to run this block. Actually I should have, shouldn't have wrote this. I should have wrote it because the current directory is [00:05:00] here. So I have to navigate to source and then, I'm sorry.

[00:05:02] First, so I have to write source. And there's a tip for you if you're using partial, you can type SR. And then. Tab, auto complete and then tab, pressing tab again will auto complete with the folder that you want. So we have here on, sorry. And sorry, backend, whatever. That's useless folder.

[00:05:19] We continue to on, sorry. And then if you come back here and tab, we get a list of files. So that's pretty helpful. So if I write AP and it continuous. And then if I write main, [00:05:30] it continues with options, and then I run this file. So that's a very cool neat trick. Anyways. Yeah, so basically this is one way to run it.

[00:05:37] This will run this which will run this script UIC, to run the file name without extension, which is main_api. The point is the file. That we're currently in. Okay. So it'll get just this part and the colon app. Colon app means what's the name of the instance that you're doing and we named it app Above.

[00:05:53] So it's app and the info that you want to run in. And that's it. That's it. It'll just run it here in the [00:06:00] server. That's one way to do it. Another way to do it is just to, to use that command directly. Okay. In in here, in the terminal. Okay. That's another way to do that. But I don't know.

[00:06:09] I just prefer the Python method. So I just wrote that if name equal main part. Okay. This is regarding this logic. Here, these notes are regarding the WhatsApp logic that I will come to that later, come back to this part later. And I think this is the main points the custom exception handler.


## [00:06:26] Database Connection and Usage

[00:06:26] I explained that database connection. Yeah. This is [00:06:30] quite clear. We just have, the database instance and an sorry instance, which is model the agent and the database connection to postgre SQ database. And then we use that across the file. If you see here, we use it multiple times to register, to check if account exists, et cetera.

[00:06:44] The same thing with the agent, with the Ansari agent. We use it in multiple part. Where do we use it? Where do we use? Okay. Actually we don't use it. Yeah, we use it in the API presenter. Yeah. Okay. 


## [00:06:55] "api_presenter.py" vs Other Presenters

[00:06:55] What does the API presenter do? Here its logic is a little bit different [00:07:00] than than the other presenters.

[00:07:02] A presenter logic is just to interface with the user as intake input from him and then return back output. But here presenting actually doesn't do that. Why did we call it presenting then? Just to remain with a, the convention. But honestly, it should be named that for this specific case okay.

[00:07:19] Then what does it do? Literally nothing. If you code the present here it's nothing we, it doesn't present. Why does doesn it present? Because technically, if you think about it, the end points over here are the ones that present. [00:07:30] Because basically these are the things that are the functions which interact with the front end re.

[00:07:34] So when we get a request and it gets through one of these functions, these are the functions which reads this request, and these are the functions which reply back to the request. So basically this is the interfacing layer with the user. I mean in terms of backend at least. So this is technically, all of this is technically the.

[00:07:52] The present is how we are presenting to the user. We're taking the input and presenting. Okay, then what does the presenter do in this case? Weirdly [00:08:00] enough, I don't know why that choice was made, but basically it just provides a complete function. And what is the complete, what's the word?

[00:08:05] Complete? Imagine you have a chat with with an, sorry, and you say, who are you? And it says, I'm sorry, et cetera. And then you. You have now a history of messages, okay? Between you and, I'm sorry. And now this is called a history list of messages. 


## [00:08:17] Handling User Messages and Streaming Responses

[00:08:17] And now you send a new message and you say, okay, tell me the pillars of a Islam, for example, and then you want the agent to complete that chat and answer back.

[00:08:26] So that's why we called it complete. So what it does is take [00:08:30] the messages and which is which is actually a dictionary. Which, which have two pieces of info, I believe, if I recall correctly, the thread something related to the thread name itself and the the messages. What does the thread mean?

[00:08:41] I'll come to back come to that later. But uh, basically what we care about here is the messages value, which is a list. Okay? So this value here, this here will be a list. Even if you look at the replacement history, you'll see that it's typing. Here is a list of dictionaries. Okay. How is this structured or how is the user [00:09:00] message structure will come to that later?

[00:09:01] Okay yeah, so it basically we take the history, okay, that's currently appearing to the user in the ui. And then we say, okay I want to, to stream the response. Okay? Why stream it? Why stream it? Because if you remember, we want to return the words chunk by chunk. If you remember the yielding logic.

[00:09:19] The generator function that we said. Even here, if you look at this, you'll see that it returns the generator, if you remember. We want to return that one by one as well. The way to do it in Python here in the code is [00:09:30] yield. The way to do it through the server, through a FastAPI to the front end repo is by writing, is by returning a streaming response object.

[00:09:37] Streaming response is from the FastAPI library. Okay? This is, this automatically says to fast ai. Okay, wait. I'm going to return a response to the ui, but we're not done yet. I will keep streaming the response until there's nothing else to respond from my part as a backend code. So this is what this part means.

[00:09:55] And so where do we call this? We call this in the main a p, obviously. Okay. In a [00:10:00] couple of functions here the main one of them is ad message, we call it. And what does ad message do basically? It runs when we make a post request to this part. So if you see in the, an sorry website, you will see if you open up a chat.

[00:10:12] You will see the chat and everything, and at the top you'll see a URL, and at the end of the UL you'll see a long hash. That hash is the thread id. Okay, so basically when you type a message on, sorry, and you press enter in the front end code implicitly or behind the scenes, we run code in the front end, which calls [00:10:30] this endpoint with the thrill id, similar to the ID that you see at the top of the URL.

[00:10:35] Sorry, chat. Okay. And so when we call it, we pass to it. The details that you see in the ui. So currently in the ui, you have who are you and, sorry, replies and whatever. And so all of that, when you press enter to enter a new message to submit a new message to the backend, what gets sent is not only this message, it's this message no, sorry.

[00:10:55] It's only this message. Yeah. We the previous message that UI don't get sent again, only [00:11:00] this message gets sent. Okay. And you can see it here in the Quest because it's an ad message request object. So if you see that object. You'll see that just have role and control will be always be user because the person who sends the request is a user.

[00:11:12] So it's always called user. Even if you call to the front end code, I think you'll see user. Yeah, I think user. Maybe if I put a single string. Yeah. Here. Okay. Where is it? Return. User core types. User role. [00:11:30] Yeah, user role. So these are possible user rules. And so we sent the user, but I just wanna see where is this used?

[00:11:37] Username? Yes. Here it is. Here it is. Okay. So we create the the thing that we're going to send to I'm sorry to the backend repo. And then we, that message we specify so we specified the rule with the user rule, which is just a user swing as you saw, and the content, which is the message that you just typed in the website and hit enter that message.

[00:11:59] Okay? That's the content. [00:12:00] Okay. So that's what's written here, has to be, this has to abide with what's written here. Okay? Okay. This is something as well. Now, after we get this last message, we, internally in the code here, if you read the messages one by one. You would, you'll understand what's happening.

[00:12:15] We get the thread history, IE we get the previous messages, which appear in neuro I, we get it from database from our side. And so now we have the complete history of messages. Okay. And now we add the last message that you just sent. When you press enter, we add that to the thread history, [00:12:30] and then we get all that history and then send it to the complete presenter over here just for the LLM to compete it.

[00:12:36] And give us the response and the response, the streaming response will return it here. That's it. Obviously this is misleading because technically this really isn't a presenter anymore. It technically presents the complete answer of, I'm sorry, back to the ui. Anyways so this is initially the logic and for the main endpoints that we have here, for the main ones, for the core.

[00:12:56] Functionalities that we have, you'll see me adding, detailed [00:13:00] the comments, explaining what each part of the code does. So I won't go into details here to be honest. But hopefully you get just a glance and a, an overall idea of what's happening here in this file. I think I'm done with it. The tricky note is recording the word presenting, and its different meaning here.

[00:13:14] I already explained that FanoutCache, to be honest, is not expert in caching. So I'm gonna explain that. 'cause I really don't know it. I don't know how exactly it, it optimizes our memory usage additional routers. Yeah. This part is actually, this part is important. [00:13:30] Okay. 


## [00:13:30] Integrating WhatsApp Endpoints

[00:13:36] So in summary, we have these endpoints over here and we have endpoints related to WhatsApp in the a file called Main WhatsApp.

[00:13:39] Okay. You will see them here get, or whatever. So these are endpoints as well. Okay? But. In the server, we always run the script of main_api de deploy. Okay, so now the question becomes, I want to run the endpoints here and I want to run the endpoints in main WhatsApp Deploy. How do I do that? Do I run two instances, two server instances?

[00:13:58] I, that's not [00:14:00] really a good option. So what we do instead is in this server that we're running at now in this app variable that we defined above that we defined above here, we want to somehow. Toy or bind the endpoints of WhatsApp's endpoints. We want to bind that with the endpoints of the instance that we have currently running here.

[00:14:22] Sorry for my English. So how do we do that? How do we do, we make this binding process by using, include [00:14:30] router, include the WhatsApp router. So if we control, click here, you'll see the router that we define in main WhatsApp by. And so this router, which I define here, when I, whenever I create an end point, I now add that endpoint to the router object I created, which is here, and now I call this, okay, in, in this file, in WhatsApp, the router object.

[00:14:47] And now I include it here as well. So how, where does this appear? It appears here. I import it from another file from the main WhatsApp file that I just showed you. I import outr and name it as WhatsApp router. So that's it. That's the whole [00:15:00] thing. And now the API endpoints over there will be visible, will be in that same FSBI instance that we have running in the live environment.

[00:15:09] That's why if you want to test WhatsApp, you test it by actually running the the this script, the main_api script by running Python main_api. So you run this to test either the main_api or the WhatsApp API. Okay. 


## [00:15:23] Outro

[00:15:30] So this is also something for you to understand and hopefully it's not really hard to grasp handle CORS validation.

[00:15:33] Yeah. Okay. I think I might leave that part. To another. Yeah. I've leave that part later. That's the last thing remaining in this file. The defining various API endpoints, I don't think that's really necessary um, used to the comments that I wrote. So yeah. I'll start next time from the CORS validation logic. 

