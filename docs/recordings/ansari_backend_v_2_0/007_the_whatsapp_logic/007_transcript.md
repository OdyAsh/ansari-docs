# Ansari Backend V2.0 - 007 The WhatsApp Logic


## [00:00:00] Introduction and Apologies :/

[00:00:00] Okay. Hello again. First of all, before anything, I apologize if you hear background noises. There's a lot of construction work behind me. We now shall proceed to the WhatsApp logic and it's really not com that complicated. And I'm not going to explain everything in it, but, let's see the main the main logical sequence of what's happening.

[00:00:25] We get the logger, we get the router that I talked to you about before, and we get the, [00:00:30] Ansari agent again. We go that far, soon enough. 


## [00:00:32] Understanding Meta's API and Initial Setup

[00:00:33] And now we initialize value, specific values related to making the the, like the connection between the server and. The meta meta's API tool called graph API to make it work.

[00:00:45] And so there is some info that we need. Chosen WhatsApp business number. 


## [00:00:49] Overview of WhatsApp Business Integration

[00:00:50] This is ba there is a lot of terminology here related to how to get WhatsApp activated like the API to WhatsApp to Graph API through metas [00:01:00] interface, like developer dot.facebook.com and all of that. And there's a lot of procedures and it's a lot of stuff to go through, but, to be honest, most of them were things that had to be done one time only, and I did that thankfully. We don't have to explain all the intricacies here of how I initially got this logic to work. Okay. In other words, the application is already set up in meta.

[00:01:21] . And uh, we have already a live version of the app and the test version, and we connected both of them with uh, was here. And so like the initial connections and [00:01:30] the initial roles and the. And configurations are set up. So I really don't think I need to get to go in depth in that part.

[00:01:36] Let me just see an overview of what I wrote here. 


## [00:01:39] Endpoints and Presenters Explained

[00:01:40] Aims to this file aims to extend many pi like I said, with fast P endpoints, which include which hand incoming handling coming WhatsApp webhook messages. And I think all of these are stuff that we know the credentials. I said I don't need to explain that much.

[00:01:53] And the presenter, again, the same tricky note here. The presenter isn't really presenting in our case because what's presenting [00:02:00] is technically the endpoints that we have here, that which get the request and then return back the response. And the presenters here have a different logic.

[00:02:08] You can imagine something like the API presenter that I showed you before, but actually a little bit more complicated than that. The API presenter just did the logic for completing, if you remember, the complete function. But you'll see for example for the endpoint in main API called register user, for example.

[00:02:24] The details of how this is done is is in the main. Is is in the main [00:02:30] API, not in the presenter. Okay. This is as well as the ad message. The ad message. We do the logic of adding or getting the thread history. And then all of that logic is is written directly here in the endpoint.

[00:02:41] But in main WhatsApp, however, I abstract the things a little bit. So the main purpose of like the only two end points that we have are a, is a verification webhook and a main webhook. Okay. 


## [00:02:52] Callback URL and Verification Webhook

[00:02:54] So the verification webhook is just a way to initially verify. That the server, which [00:03:00] calls the, like the meta graph, a p server is indeed the server that we set up from the meta interface itself.

[00:03:06] To explain this, you can imagine the UI of meta, okay? That side, and in the UI of meta, we want to say to state a callback URL. Okay? And the callback URL is for the the is basically like our code, like the endpoint of our code, which will. Be able to take requests from from meta.

[00:03:25] Okay. So if you, let me even, let me open up the trusty paint that [00:03:30] we have. So if you have so if you have the UI of, of meta, like developers do facebook.com here. And then you have multiple configurations for setting up the the like meta with the server. And that's already set up.

[00:03:41] We have now a place for a callback, URL. Okay. I don't know, it's route as code, which is a little bit confusing. Okay. I call back UL and here you put the A link. Okay. URL two the back end report that we have. Okay. And the link that we put is basically this one. Okay. But it is prefixed.

[00:03:59] Okay. [00:04:00] But what do you prefix it with? The base. URL. Okay. The place where we host our application and here's the tricky part. And the production. And the production version. This will be, for example, Ansari to chat or Ansari, API to chat. So you'll have Ansari, API to chat and then slash and then WhatsApp, and then slash and then version one.

[00:04:19] Or something along that line. I can't remember the exact page. UL this is for the production and this is already set up and this is not gonna change. So you really, you do not know. You don't need to go to that page anymore. 


## [00:04:28] Testing Environment Setup

[00:04:28] But [00:04:30] what do we do for the for the for the callback UL of the testing environment?

[00:04:35] Because we don't we don't wanna, we, when we test, when we're testing here we want to adjust modifications in our local code and then test that through graph PI. Okay? In the production it was easy because in the production have the Heroku and we set up the RL and so API do whatever slash WhatsApp, and that's always live, that's always there in production.

[00:04:54] And so like verification, doing a verification check there into the live environment. Let me [00:05:00] imagine. Live as a cloud, like this terrible cloud. And and then that verification happens all like seamlessly because it's always up there, it's always activated. But for the local environment it's local.

[00:05:11] It's only within the scope of us. Like it's, its not on the internet. So how do we make this repo that we have locally right now? How do we make it on the internet as well? I don't know why I'm imagining the internet as a terrible cloud, but bear with me. So how do we do, we make that transition in order for us to get a base l from here.[00:05:30] 

[00:05:30] Okay? That base l with the with the WhatsApp version one route. Okay, how do we do that or endpoint? How do we do that? And finally get that link, that complete link and use that in the, in the callback, URL callback, URL in the testing app, because this was a prude app, production app.

[00:05:51] And we have, Ansari, also, but Ansari, dash test, which is the, which is testing environment. Okay. So we want to just link here. Okay. So link [00:06:00] here, it means like a URL that we that, that Graph API can see. 


## [00:06:03] Using Zrok for Local Testing

[00:06:04] Okay, there's a couple of methods to make this from offline to online. One of them is ngrok, I think it's known ngrok, if I remember his name correctly.

[00:06:12] Or nrok can't remember it exact name. It's well known. It is just a service that allows you to to, to basically open up a, like a public IP address and and report to, to, to the port that you map it with in the local pc. So it gets mapped from like locally to a public like URL accessible to anyone.

[00:06:29] So [00:06:30] that's the way, but when I read the I saw that meta considers this tool in service as as unsecured. So it doesn't allow it. So if you put a link here related to ngrok at the start, it'll not allow it. But it allows a tool similar to it called zrok. Okay. Called zrok. And so that's what we're using.

[00:06:51] I'm not really expert at the intricacies or what, like I can't give a proper definition of what it is exactly off the top of my head. So I did the [00:07:00] article about that, an article, and I can refer that article to you. I put its details, I believe in main, API here and the "if" main equal main name, equal main condition where is it in this part?

[00:07:13] Okay. In the note 2 here, you have to use Zrok to test WhatsApp web book locally. That's what I've been talking about in the awesome paintings that I've been doing. Check the resources at exemplify for more details because I did a lot of comments there that will go in in a minute, but too long didn't read.

[00:07:28] Version of it is that you should run [00:07:30] the below. Initially when you set up oc in in your computer you run this command. Okay. Okay. So you first get the Zrok exe file, which I have put here. Which I have put here. Okay. And that's why it's in the dot get ignore. If you see the do get, ignore, you'll find it here as well.

[00:07:48] Okay. And and so since we put it here, if now I type the zrok command it it can be red, it can be red from here because I'm in the country directory of this. And I have put it in the route as well. [00:08:00] So I, if doing this command and then dash h whatever this can work if I do it like that, okay, we can globally install it as well.

[00:08:06] But I put the instructions of how to do that in in the article that I refer to in a minute. And so after you, you do that and you install it here. You run this command here zrok Enable secret Token generated this I will explain this in a second. But you, but this is basically a secret token for your device.

[00:08:22] Whenever you when you make an account and when you connect, the, all of that steps will be shown in the article that are referred to. But when you do that and [00:08:30] connect to the zrok with your with your pc. The X ui will tell you, okay, this is a secret token for you and for this device.

[00:08:37] You will take that to and put it in the NV file. And you can see an example of it here in the example, or like the portal. I put that key Zrok shared token. Okay. Here I just put it in a very long way just to make it clear. Actually no, I did not put it here. The Zrok secret to, I didn't put it in the end for example.

[00:08:59] Why? Because we don't [00:09:00] need that in the environment anymore. Like we run this command only when we just set up Zrok, like only when we download it and set it up for the first time. But in any other run that we do in, in, in your pc, you won't do this two commands anymore. So that's why I didn't put it permanently in the dot exemplify, but we'll get to back to this in a second. And then you run this Command, zrok Reserve Public, local host the port that you want to connect to. So if we so if we do the application here if we run the server on Local 8,000, and this is a default one, like you'll see [00:09:30] here that I think I like 8,000 is, I believe is a default for Fast Pi.

[00:09:33] So when you run this and you don't specify the host or when you run this file itself. Like this, and you don't specify the host. First P automatically makes the the host and the port local host and the 8,000. So that's why I make like this, I run this command. And so this command like connects this server at this location, the local host, 8,000 to publicly like to reserve the public with a name shared token.

[00:09:56] What does that mean? I'll come back to this in a second. So these two commands, you [00:10:00] run initially on the initial setup and then when you start when starting any new terminal session, like for example, when you're done with this and then you want to like for any later run, you open a VS code and then you open up the terminal again, and then you're going to work on WhatsApp.

[00:10:13] Then you run this command, only the rock share reserved this command basically say, okay. Now let's share the server that I've connected to here. Okay. Let's share it and and to prove that I will share it in a consistent URL. I will pass you the secret token of that URL. [00:10:30] Okay. Or like the shared token of it.

[00:10:31] I know these details are vague, but they'll become clear when you, let me tell with you the notes here, because there are a lot of notes. So I don't know if I'm going to explain all of that or not. But basically you can read these sources to understand the part that I explained in paint, the part of the callback URL and verification web book and here and I even added timestamps for you.

[00:10:52] Hopefully like these these links are sufficient. Even the first one specifically are sufficient for you to understand the code behind the, the code that I [00:11:00] wrote in verification webhook and where I got that from and and now how I connected that logic of the code back.

[00:11:05] Your l You see straight up examples in these videos. And here, if you want to test WhatsApp webhook, look, you can use zoc on a reserve your l with a zero shared token. That's what I've been saying contained by contacting a control holder. Obtained by contact control. Yeah. So currently I'm the only one who, who knows this actually I think I shared it with others anyways, I'm the one who created this share token. And so if you try to use that share token in in your pc, you'll probably get an error because it can only be held in one account. And that's [00:11:30] a a limitation of X. Let me illustrate it with a, with an example, like with a poor diagram, if we, can I wait, I, why can't I delete this? Can you please get the, okay, you know what, let me open up paint again. Paint, okay. And if we have this is zero. I love doing horrible rectangles. And you create a secret token here. Okay? A secret token called the shared token then, and this is my account, or [00:12:00] this is my account.

[00:12:01] Then I'm the only one who can use this token right now. Okay. And and then this token I fixed that key like the, this this this private string. I fixed that in the, callback, URL Meta, if you remember the meta ui. And we have the production page. Okay. Which has its own callback.

[00:12:22] And then you have the testing page. So the testing for the callback airport. Okay. I I put a link like the htt, PS whatever, [00:12:30] and then the secret token, the shared token that I have, and then dot and then Zrok, and then share like the u rl format of zrok. Okay. To make it public. And so this shared token is fixated here.

[00:12:41] It's okay. I fixated it in this page of meta, and that's it. Okay. So now you need to to get this token for me. And then I need to deactivate the token from my end so that you can enable it in your environment. This is the zrok of your environment, okay? And and in order to use that same secret token, you have to contact me and I have to let it, [00:13:00] putting conditions, let it go or un reserve it, and then you observe it from your end so that you can use that same token to connect here.

[00:13:05] That's one way to do it. Another way is to create your own token, and when you create your own token, you go to this page. And then you modify this this token yourself, and when you're done, you return the token to the original one. Or you don't have to return it, but just notify the rest of the team that you change the token so that if I go back and test WhatsApp I need to go back here and change the token, okay.

[00:13:24] Et cetera. This is one way to do it. Another way to do it is that for me, whenever I finish testing WhatsApp [00:13:30] I release the token. Like I, I don't create a link with this shared token. And so that it's free now and anyone can use it. But the disadvantage of this is that if a user, even authorized user somehow guessed that shared token, because it can be like I can't remember its maximum amount of letters.

[00:13:44] It's a lot to correct through, but and there are new miracles allowed, so it's difficult to crack through. But still if that happens, then then they'll be the one who's, who are able to to use that share token and and access the the the callback QRL in our part, which is not really good.

[00:13:59] [00:14:00] Okay. If they have the ripple locally on their end. So to mitigate the security risk. I do not, I never unle this, okay. I don't rerelease this ever. And whenever someone requests it, I unle it and then they. Use that share token. Okay. If this is not really clear, just read the comments here.

[00:14:16] These are sources that, that's the link that, that I talked about. Quickly share your app with zrok. I, here explain the basic terminologies. And please ignore the cringy gifts, gift or gifs, whatever [00:14:30] that I that I made here. But basically I did all the steps of of content, of just how. To use zrok.

[00:14:35] And and you have a link at the end, like this. Where is it? Yeah, like this, can I zoom? Yeah. Like this, your unique instance name to shadow zrok. Here, the shared token that I created is called Your unique instance name. Okay. So that's very unique, but but yeah, but so you have a share talking like this and so this.

[00:14:55] Your unique instance name right now, if I have this, if I have this and [00:15:00] I'm reserving this right now, I can't remember if I read it or not, then no one can use this token in any zrok instance that they make it. So that's why it's a unique it's completely unique. Okay, so that's the thing. And so again, if you're confused, just read this, read through this, and read the sources here.

[00:15:18] I, I also have timestamps that that help you, that will help you out. And and yeah, and I, here I see the options. And here I say that even that you should contact me to get the X cash share token or alternatively you can go [00:15:30] to this link here in develop with facebook.com and change the callback URL.

[00:15:34] Okay. Because, so I said here that if you go to that link, you cu currently you'll see something like this in the call back, your l form. You'll see that I put a link like this with here the unique sheet token that we have. So you can just replace this part with your token and then when you're done, you return it to something.

[00:15:49] Okay? This is all of, again, all of this is done so that I may allow this this, like this locally testing and connecting this local environment with the internet so [00:16:00] that meta can see it. And I can get replies from Graph Api. To test the WhatsApp logic that I meet. Okay, so I actually spent a long time explaining Zrok, but hopefully it's clear now.

[00:16:11] You can read that in your own time. And these keys, to be honest, these keys will be obvious when you read these descriptions. So I won't go I won't go into details in them. And not all of them are used. If I remember correctly WhatsApp participant, I, I ended up not using this.

[00:16:25] Yeah, only config is not really used somewhere else, I don't think that's important. But most of them are [00:16:30] used. But man, yeah, this is basically how I got WhatsApp to work. Again, the verification logic, that in the video that I, mentioned. In the comments. 


## [00:16:39] Handling Incoming WhatsApp Messages

[00:16:39] And then the main web hook hand, the incoming WhatsApp web hook message.

[00:16:42] This is a part where just here in WhatsApp code, I'm the one who mostly did everything related to it. So now you see a lot of comments everywhere, just staring what each part of the code does. So I will not go into depth in in explaining this. And it's pretty clear from the comments like, coming web book message is empty, invalid, [00:17:00] or message that this update. So I'm only expecting a specific type of messages from WhatsApp. Why? Because stating a callback your error or a webhook means is that whenever a new event happens from the user side, then we will receive a notification of that message.

[00:17:13] How is this notification received? Based on the type of message the user sent. So for example, if they just sent a message, then we will receive something like this. Method with PI. Tructure of a user incoming message. So this is the structure if they sent a message, okay. And you can and this the structure that you see [00:17:30] me formulate the code that I've written based off of, I dunno if that's proper English or not, but, okay.

[00:17:36] And everything here is clear. I tried to put that all in here because I didn't really find the proper sources for meta to, to see this in a clear way. Probably they have, and I just didn't find it. Yeah. But there are other ways of notifications. So for example, if a user just reads a message that you sent, like if we, if the agent.

[00:17:53] Ansari, agent deploys in a message and the user has closed WhatsApp the message will be delivered. Okay? So you [00:18:00] get a notification, they, it got delivered, and then when he reads it, you'll get a notification, like a message like this. Notification means a message ization like this, okay? You receive a Jason like this, that states that the user just read your message.

[00:18:11] Okay? I'm not interested in all of that. I'm just interested in the message that the user sends me. Okay? And now the message that the user sent you can be multiple things. Can be the type, type can be audio, or it can be an image, or it can be a sticker, or it can be a video and all that. And I've wrote all of these possibilities here in order for you to adjust your code accordingly if you need them.

[00:18:29] In my [00:18:30] end, in my currently in the code. I don't recall doing any logic for this stuff except the the what is it? The text. The text. If it just sends a normal message, then it'll be text and it'll be body. And then this is the message that the user send. That's it. I didn't do the logic for anything else, I think, except the location, because if we plan to do like a a prayer time thing we probably need the location from them.

[00:18:51] But, other than that, we, I didn't use anything of these. I think so yeah. Again, here's a, here's an example of the meta API structure of a [00:19:00] reply messages. This is the reply message I said that I was talking about, that this can be either, where is it delivered? Delivered? Yeah. So here, for example, statuses, the status key that we receive, it can be one of the following, can be sent or delivered or read.

[00:19:14] And I've put details here if you want to read them, if you want to use that info for whatever reason. Okay? We get that, we get a, and if it is a string like we, we do problem checks, like if it's a location, then we handle handle location means handle how we reply to allocation type message.

[00:19:29] Okay? [00:19:30] And if it's not a text and we say that it's unsupported and if it's a text, then we then we handle the text message. Okay? The run this handle text message, you'll see that all of these are functions in the presenter. So that's what I was talking about. The presenter here has a different logic.

[00:19:43] The presenter here is basically just the behind the scene logic or like us, like abstracting the logic in the main WhatsApp to profile. And we abstract it into and put the main code actually, or the main logic or the detailed of the of how we do things. We do that in the presenter clause.

[00:19:59] [00:20:00] Okay, so that's why presenter means different things in, when you're talking about WhatsApp and Main API, but presenter in the stdio and the files and all of that is, is what we talked about is actual meaning presenting. And so this presenter class has a couple of of functions with which helps us, which helps the two endpoints in the main WhatsApp profile. And so if you see here, these are all the functions that help us check relevant WhatsApp message details, check and register user. And then all of them are apparently from the name. And if you can't understand them from the name, you understand them from the long docstrings that I [00:20:30] write.

[00:20:30] And if you don't understand them from the long docstrings that I write, you understand them from the long comments that I write at each step. So I really won't explain this because because they are, like the, like I'm basically writing English, like the code here is like basically English.

[00:20:43] It makes, it made the code long, but to be honest it should be understandable. The most important part was the zrok and all of that. And I hopefully explained that well. And if I didn't, the comments will hopefully help you out. So that was related to WhatsApp.


## [00:20:57] Conclusion and Next Steps

[00:20:57] I think I'm I'm done now with the WhatsApp [00:21:00] logic. And now remains the, Ansari. agents, the actual LLM part, the actual uh, good stuff and a couple of more miscellaneous files and Ansari database and we will be done hopefully.

[00:21:15] 

