# Ansari Backend V2.0 - 006 Dependency Injection in FastAPI

[00:00:00] Okay. Test, test, Test. Okay, we're good. 


## [00:00:03] Understanding Dependency Injection

[00:00:03] This is the final thing I think I've explained in this part in this file called dependency injection. And so I explained it in these notes at the very first time. We see depends mentioned. So what's dependency injection in fast pi? I've put some things here that will help you out, but, i've also added A-T-L-D-R version. If you just want a summary for it. What I'll read with you now is actually the TLDR of the TLDR is that when we put Depends like this, [00:00:30] sorry. As a parameter and a function, we basically, we can basically think that this function is saying the following, I depend on running this function, the function.

[00:00:39] So it depends, I depend on running this function first to proceed with my logic. 


## [00:00:44] Example: Register User Function

[00:00:45] So let's take this as an example. Register user when they, when the front end cause a request for the back end for this endpoint. We, sorry, we run this function, but before we run this function, we see if there's any dependencies.

[00:00:59] And there [00:01:00] is dependency on validate_cors function. So we first, first run validate_cors function, which I'll show to you in a second. And the return value of this function, we we put it in this boolean called cors_ok. Okay? Okay. So this is what depends mean. 


## [00:01:17] Validating CORS Function

[00:01:18] And let's see, what validate_cors to get a feel of what's happening.

[00:01:21] Basically it just checks that the origins from which the request comes from is within the Origins list. Remember the Origins [00:01:30] list? The one in end of example over here in here? This one? Yeah. So we check that from this function, which I showed you previously, and the rest of Origins that we have.


## [00:01:39] Handling Origins and Headers

[00:01:39] We check the incoming origin from the request parameter and see if the, like the header of origin or host in it, whichever header in it. If the values of this header is in the list of allowed origins. Okay. Then we're good to go. Okay. Then we're good to go. Otherwise we raise an exception.

[00:01:57] Okay. Of incoming origin host and we say, what? [00:02:00] The request isn't coming, is not in the origin list, the allowed origin list. One might ask why do we do as function specifically for this even though we have this code right here that I showed you, privacy, the middleware where we add list of allowed origins.

[00:02:12] You are right. We have that. But I think because I'm not the one who initially add this, I think the main reason for this is for any extra checks that we can do. 


## [00:02:22] Additional Logic and Custom Headers

[00:02:22] To bi maybe bypass this header thing. So for example, what we're, the logic we're doing here is that we're checking for another thing, like not [00:02:30] just the growth default origin or host headers.

[00:02:32] No, we're just checking for a custom header that we put and to see if it has certain values based on certain environment. Then we'll also allow it to return through. So if we are adding additional logic that we want to check and based on it, allow the function to run. We can call this function validate_cors.

[00:02:47] Okay? And we can use dependency injection like I showed you before. So that's the reason we use this. And we, you see this in everywhere basically. Like you see almost all the functions that we have at feedback. All of them, all of the endpoints we use [00:03:00] is logic. Okay? So that's something. And also, you might have noticed that this.


## [00:03:05] Request Object and Dependency Injection

[00:03:05] Has the request object passed to it? So this is passed implicitly. Okay. So in a function which is it depends function from a, from an end point function you have the normal register request. Okay? So this is the object that comes from the front end, which contains data with the same structure as this key value pairs.

[00:03:22] And. Implicitly, we also get a request object here. We don't need it, we just need this. So we just code this value [00:03:30] and that's it. But in here we need it. So in here we explicitly put it as a parameter so that when it's sent to us from the front end and when we run this we technically also receive that, the normal request info from the front end as well.

[00:03:43] Okay? So that's something to keep in mind. That's why this part works here. I think, I'm not sure about this. Technically, if I, if we put in this guest settings, if we put if we put also requests here, like rec call and requests, I think it'll work as well like we did here. But I'm not sure about this to be [00:04:00] honest.

[00:04:00] So yeah, but this is at least is a logic for this part. This is here and this is the logic of the, depends. You can see more info about it here. And and yeah, we use that logic everywhere. So for example in here, if it's not okay, we're not going to register the user. So if the request comes from any other host that's not related to us, then we will decline that request and we'll raise an a call is not permitted.

[00:04:21] Error. Okay. Yeah, I don't think I need to explain much else in the file. 


## [00:04:27] Endpoints: Briefly Explained

[00:04:27] The only thing remaining to explain is just the endpoints [00:04:30] themselves, just to explain what end point each endpoint does. And this you really can understand it just by reading the, any comments here or just the overall doc.

[00:04:38] Doc stringing is sufficient. For example, he get all threads, retrieve all threads from that. Again, I know I didn't explain what threads, what the thread means, but this part will come when they when I explain, I'm sorry. When the agent of, I'm sorry. The AI mode. But yeah, but overall the, these the code here is pretty self explainable and yeah, I think I think what I suggest is if you really confuse in [00:05:00] something try to search it here first and then search it in the ui in the front end repo and see what it's called.

[00:05:06] Maybe that will help you have a sense of of, okay, where does this lie in the grand scheme of things. Okay. So that's that's all regarding the main.py file. I don't think there is anything else I can add here. So yeah, next up will be will yeah, will probably be the probably be the WhatsApp files before the logic of Ansari itself.

[00:05:27] Itself. Yeah. And then we'll [00:05:30] we'll go to the AI model and then simultaneous fives, and we'll be done. Yay.

[00:05:37] 

