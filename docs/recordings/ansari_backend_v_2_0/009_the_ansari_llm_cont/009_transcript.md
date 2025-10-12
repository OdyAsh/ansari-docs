# Ansari Backend V2.0 - 009 The Ansari LLM (Cont.)


## [00:00:00] Intro to process_one_round()

[00:00:00] Okay. Hello again. So last time I stopped at the process message history, and now we'll continue the logic into process one round the function or method. And um, this is basically where lite LLM's code. If I remember yeah. So you have something called common parameters. These are parameters that will be passed to lite LLM.

[00:00:22] I'll come back to this in a minute. But bear with me. We have failures here in response. Okay? These are variables that will be set below and [00:00:30] in our while loop, we are waiting for a response from the get completion. Okay? What is this? What's happening here? Okay? So get completion.

[00:00:37] It is just a wrapper. It's just an abstraction for the syntax of lite LLM, which is literally just litellm. 


## [00:00:44] Understanding Lite LLM

[00:00:44] And lite LLM, let me quickly explain what this is. Okay. And so let actually lite LLM is a Python library, which gives developers like a bedrock access. Okay, whatever. It's a gateway to provide model access, [00:01:00] logging and using track tracking across 100 LMS all in the open AI format.

[00:01:03] So from the, from what I've just read it connects multiple LLM provider. To have the same SDK the same syntax of writing the calls to these LLM providers in Python. For example you'll see here how to use lite LLM and this example is very cool. You'll see that. This completion is the same if I change the LLM providers, like these LLM providers.

[00:01:29] [00:01:30] Almost all of them get the same API. This was previously not the case. For example, you see that OpenAI and and Grok I believe and xAI, these will have similar co completion, like similar API, similar way of communicating. To the LLMs using the Python code. But other libraries have a little different syntax.

[00:01:47] So that LLM standardizes standardizes all of that into a specific format similar to the open eye format. And this is open eye format. I actually believe that what's written here, I think this is new. And [00:02:00] if I remember I searched the previous documentation for lite LLM and this was not present, if I remember correctly.

[00:02:05] This the streaming response format and the response format. Because what's written here? I'm just discovering this with you right now. What's here is basically what I attempted to do in the Jason files that I mentioned. The, not the Jason files. I'll tell you the the the notebook file, if you recall, that that file this documentation is very inferred from opening Eyes official documentation.

[00:02:26] And I try to do that and do an explanation of each key that we [00:02:30] have, that gets returned from that object. And so we have finished reasons and swimmings and whatever, and that's basically here. In streaming, you'll see the choices and finish reason. And then so that, so I think both of them are the same.

[00:02:43] Like what I, but here is like JSON format A here in the object oriented format. 'cause that's just what I have copy and pasted from the terminal when I printed the model response object. And so the middle response here is I believe the entire JSON here. Okay. So this is very cool actually.[00:03:00] 

[00:03:00] Since I just discovered this with you right now, I really suggest you read that, read this, and I think this doesn't really say details. It just tells you an an example of all of these values. But here you see me explaining for example, finish reason. Stop. What is that? You have to refer to the documentation of open eye.

[00:03:16] But here, I think I, I mentioned the reason models, the model stop generating tokens. This will be stopped if model hits a new an initial stop point or whatever. So I think mine is more verbose and you can literally apply that sentence to anything that I do. Like I'm always more [00:03:30] verbose and I, I write a lot and I talk a lot, but hopefully. That all of these writings will help you out. And it's cool. It's cool. It's a cool SDK and it's really easy to set up. 


## [00:03:40] Setting Up Lite LLM

[00:03:40] For example in here, if you wanna set up GPT 4o or any model from open ai, then we make sure that there's an environment variable called open ai, API key.

[00:03:50] Okay, and this is important. This, that's the cool part, is automatically used by, or automatically used by the lite LLM SDK. So if [00:04:00] we just set up an environment variable of this name, then we don't have to call it here when passing in the completion. No, it's just internally this function will we'll see if.

[00:04:10] Open ai, API key is mentioned in the current environment, variables. If it's there, we'll just use that and use it and continue. Okay? So that's the cool thing about it, and I think there's a way to, to pass it as well. If you want. If I go to completion, lite them

[00:04:26] shared completions, I think you'll see in [00:04:30] s. I think you'll see the api, API key if I search for it, because I remember seeing that. Yeah. API key. You can put it, okay. You can put it, so if you put it that this, it'll be dynamic, but you really won't change it in a server or like in configuration.

[00:04:45] So you normally just. Put it in environment variables and it's read and it's read by all of these. So that's it. 


## [00:04:51] Handling API Keys

[00:04:54] It may help if you have multiple a p keys and you wanna set this completion to that API key and another completion to another API key, et cetera. But other than that it's good [00:05:00] and it automatically gets deduced.

[00:05:01] For example, let's say you have a system where you have a com a code here that says completion and it calls an open I model. Okay. And then another part of the code, for example, just this is a dummy example. You have grok here. Okay? So you have a completion, but now we are passing in a agro, a module for a model from Grok, okay?

[00:05:20] From XA ai. And so here, if we now in the environment variables set key called opening ai API key and set up another key called X ai, [00:05:30] X-I-A-P-I key. Then they will this, will get mapped to this to where the completion mentions XAI. And this key will get mapped to where we mention OPI key. So it's really just straightforward setup.

[00:05:41] Okay? And so this is what we're doing here. You'll see that we're doing here a completion. Let me get back to the code a completion here. And if we see the example, you will see open your eye key here. It gets read, okay, it gets read by this code. [00:06:00] So this is a good completion, we call it here.

[00:06:02] And we passed with the primes. What is primes consist of? Twoparts, common primes and specific primes. The common parameters are these, you can see the pages that I just opened up with you to see his details. Let me see if I can. Bring it up again. Did I just close it? Think I close it? Yes. This one.

[00:06:19] Input primes. Okay. So all of these, you can see an explanation of each one of them to read what it's all about. But yeah, it's basically the model which is GPT 4o [00:06:30] for now, the message history, the entire history of messages until the last. For example, user message that he that the user wants to answer wants I allow them to answer.

[00:06:38] And then the streaming mode, if streaming or not. For now, this is always true. Hopefully we're planning to make this dynamic. And then we have all these pamphlets you can eat about them in the. And the document and the documentation. So these are the common primes. And what are these are primes that could be true or false based on who called the function, called the process one round.

[00:06:59] So you have used [00:07:00] tool and you have stream. Okay. So we set stream in the common primes because we always just commonly use this, but the used tool one could change here. We're saying that if it's true. And if you stool is true, we will add this parameter. So this if you don't know this in text, it's called unpacking.

[00:07:18] This is dictionary. params is dictionary here. And so thispart. Is a dictionary itself. Okay, consisting of two, two keys. So we're saying we're going to create a dictionary of two keys and [00:07:30] then two key value piers. And then we will unpack these two key value piers into the remaining key value piers of common primes.

[00:07:37] So again, common primes is dictionary. We take the dictionary, unpack it here. So when we say double asterisk here we, you can imagine all of these key value periods getting spread. Into this. So you can just imagine with me this dynamically gets replaced. Oh sorry. Oops. This dynamic gets replaced with all of that.

[00:07:58] It's as if we are [00:08:00] putting all of this right here. Okay. And then we continue. So you can imagine it like that. Here we're unpacking all these key values. Here we are unpacking these two key value pairs and these two, two key value pairs until we have all the key value pairs of parameter prime dictionary.

[00:08:14] Okay? And this is also the case if just format I believe, do we set this? No, we don't set this to to true. So what is the Jason format? Jason format is basically saying when the LLM provider replies back to the user. How do we want it to [00:08:30] respond? Do we want to respond in, in free form text and to just write, okay, ansari, et cetera, et cetera, et cetera.

[00:08:36] Or do we want to standardize Jason structure that the LLM provider always abides by and follows? So we can say if we do this, then I think there's a we can still specify for example how we want Jesse is Jason to be returned to us. So the alien provider can give us, for example how do I say it?

[00:08:56] I wanna, I want a clear example. You can say [00:09:00] okay. Suppose we are always using ansari to just get relevant is based on the user query. We want to always standardize how, ansari, responds by having a Jason where the key with the first key is called. Relevant A one. And then the value is the AI itself.

[00:09:14] And then relevant A two, that's another key. And then the value. So this a structure, this is a structural response. This is what will happen if we make this true, if we put these key value pair. And if we don't put them, if we don't put the type as Jason object it'll be freeform text.

[00:09:29] [00:09:30] So in that same dummy example, we'll be returning okay. Here is a relevant area as you asked, and then colon and then the area, and then here is another relevant area, and then the area. And so that's freeform text isn't structured. So that's the difference between JSON object and a normal freeform response by the LLM provider.

[00:09:47] And these are all the parameters that we care for. And we don't really we rarely adjust these parameters. Since the beginning of the project, but that might change if we try to see other m providers like anthropic or or grow or [00:10:00] XAI or whatever. But for now, we're sticking with t for now.

[00:10:04] Okay. And, exceptions here is the failures that you saw above the failure. We keep counting up the failures and seeing the maximum failures. I think this is repetitive with the like this exception and failures block is similar to the one above it, like the one in the function that are previously explained.

[00:10:19] Here, because here we in the process history, we also doing a failure here. So I think this is redundant code, I think we don't need to do. The exception here Anyways, we have it [00:10:30] and then we are printing the, logging, the trace back and all of that. All of that is great. Wait, I'm where am I?

[00:10:37] Where am I? Yeah I'm back in process in here. I think we do similar exception. Yeah. Literally similar, accepting, we, I think it's got copy and pasted personal around. We do all of these exception as well. And so this is exception part. This is I believe this easily understood. And so now comes up, I think the most tricky part of the, of of the code here.


## [00:10:57] Processing and Yielding Response Chunks

[00:10:57] How we get each chunk [00:11:00] and yield it. And so here's what happens. lite them returns a response. Okay. Response option. And this response is what? It's a, is a, it's a model response or a custom stream wrapper. So let's get back to the to the stream here. If we see example stream if said true, it sends partial message, deltas tokens will be sent as they become available with a stream terminated by a done message.

[00:11:21] Okay? And so this means that this will be streamed, okay? That's why this is also a possibility, custom stream wrapper. And since we're [00:11:30] always true, then for now, this will always be the case. So as you can see, the code isn't really written in a way that accommodates for non streaming code.

[00:11:37] It only takes care of streaming scenario. So this is actually a thing that we might change in the future. And four chunk in response. Okay, so response again is streamed. So each word for example, comes in a chunk in a in this variable. So we take each chunk in the response, and we do this for Loop In it.

[00:11:55] We we all of what you're going to see now is just a syntax. We're saying that there [00:12:00] from strong, there's something called Choices and there's something called Delta. What the heck is that? If we go here into the the main page of la. You will see in the streaming part, you'll see its response format.

[00:12:11] Again, this is very important. That's why I'm I said that. And it's similar to the open eye format. Okay. We have something called Choices. Okay? So again, supposing this is a model response, a stream response object which is chunk, so we can from chunk, as you can see here, you can see that from chunk we get choices, which is this one.[00:12:30] 

[00:12:30] Okay. And this is a list because you see this value here is a list. And so we get the zero element, which is the first element here. And I always saw that, like I always, see that choices here is just a list of one element. Like I never encountered the case where it doesn't contain more than one element here.

[00:12:47] And this element is dictionary as you can. It always like each chunk object always has one dictionary object here. So we always get zero and we always choose zero here. Okay. So that's why what I [00:13:00] noticed. And so it makes sense because it's a chunk, and in that chunk there is dictionary saying the only chunk of the entire message, which is, hello here.

[00:13:07] For example. And then another chunk will come with the same structure, with the same everything almost. But but here the content will be world, so hello world, for example. And this is how you can imagine the flow going. We're taking chunk choices, we're taking zero element. This, which is this dictionary.

[00:13:24] And from this dictionary we're accessing Delta, which is this one, Delta, okay? And we get back this dictionary. [00:13:30] And now if Delta content is not known. And this is self-explanatory. So this is not none. This part is not none. We will add it. We will from the list of words and the words that we have, we will will add to it the content.

[00:13:44] Notice how we don't say space. We don't do that because it actually the space is, and all of that and the dot and whatever, and it's, it can be in the trunk. So you can see this as hello space or hello, and then the next chunk is space, world, and et cetera. This we added to the [00:14:00] list of words and then we return the delta content.

[00:14:01] We yield it, we yield the current world that we have, the current chunk that we have. And you remember the logic of yielding? I'll explain it again. Okay. And we say that the response mode is words. Okay? And this will come later. This, if the delta content is not non, okay? If it's non.

[00:14:17] So if this is non. Then probably, or possibly there could be a Delta tool calls attribute. So in here, Delta in here, this can be not known. So if this is none, [00:14:30] if content is none, then probably tool calls is not known or maybe two calls is not known. So we're checking for that. 


## [00:14:36] Understanding tool_calls and Response Modes

[00:14:36] And so if tool_calls is not none, then we will say the response mode is tools.

[00:14:40] Okay. It's a tool. And then we get the the tool called chunk list. This is what TC stands for. Tool called chunk list. And then we get the tool calls here and then we see in in the, in, in each tool chunk. In the tool chunk list. We do that logic. I wanna see if there's an example of of two calls here, because I don't think, yeah, it here it stays as none. [00:15:00] 


## [00:15:00] Example of tool_calls in Action

[00:15:03] So I don't know if I put a, maybe here, I put an example in my notebook file to, to make you oh, not this one, to make you visualize tool call tool called okay. You will see here two calls. Two calls. Value will be an empty list if the model deduce that no tools are needed, two calls are needed. So that's also, I think. If no two code are needed, then obviously this would be none. Okay. As mentioned here. So that makes sense. 


## [00:15:28] Tool Call Syntax and Structure

[00:15:28] And now the two code here, I give [00:15:30] an example.

[00:15:30] So yay I'm glad I did that. You would have an object like this, or or you can imagine here if this will is in the official documentation. This would be a dictionary which have the keys ID and type and function. And and this function, they have the keys of name and arguments. Okay? And so this is the syntex.

[00:15:45] And so you can you can get back, you can get back to this later and check it out to see the details of each explanation here. Actually, I'm glad I'm, I did that through explanation for it. This will help you out, hopefully. And based on this syntax, okay, you can see that I said here [00:16:00] in the, in each chunk in that list.

[00:16:01] And again, it's normally just a single element that I see because we're doing chunking. So that's probably to correlate to that. To that party or no? Wait, because if it's a tool, then we just get. It's the response. Okay. Or the function code. We don't chunk that. I think that's why it's just one element here.


## [00:16:19] Handling Tool Calls in Loops

[00:16:19] Anyways, anyways I think this for Loop will only be done one time because I think TC chunk list is always will always have one element. Okay. If any. And so we're saying [00:16:30] if lens of tool calls is less or equal to the three chunk index. Okay. I think this is just a. Check 'cause index here will have an index here, index of two, calling the response if there's a multiple once, but I think this will always be one.

[00:16:42] I'm not sure though. This is what always just happened with me. We will append to the two calls variable above the MT variables this dictionary. Okay. ID and type and functions. Okay. And we will say the following, we are assigning the [00:17:00] let me remember. Yeah, we are saying since we append it here we are we are giving a shorthand for this, which is the two cause that we just appended with the index that we just checked here.

[00:17:10] Okay. We are putting that as TC and with now this should now be this, if I recall correctly. Okay. Dictionary. And yeah, this dictionary we're saying that the ID part, which is this, we want to to add to it the TC chunk ID and the function name we add to that here as well and the arguments.

[00:17:28] Yeah. Again, [00:17:30] I think the plus equal here is redundant because I think it's always just a one call, like it's just a one index. So this will always be plus equal to one time only because the four loop point repeat again. So this will literally just assign it. And that's that. So I think this is useless, but I kept that syntaxing nonetheless.

[00:17:47] Okay. Like we could have just made this not a full loop and and and just made that tool call added to the TC variable id. And for name without the plus here, I think because again, one last time I [00:18:00] do not recall I ever saw this length or like of this list exceeding one element.

[00:18:05] Yeah, but I guess I made this like that just to to be aware or to make this cool comparable with any feature updates in, for example, if they decide to make this model in one element, and this is the part of tools. Now, if the, now all of that was in the four loop, so now we change, we finished the four loop for in response.

[00:18:23] Okay. 


## [00:18:24] Appending tool_calls to message_history

[00:18:24] And so if we are done with this, we say response mode, words. Okay. And we check [00:18:30] the response model that we assigned here, okay. In the for loop. And so if it's words, then we append. Okay. We append to the message history related to this and, ansari, instance. Okay. We append to it. The message, the final response from the assistant, from the LLM provider.

[00:18:47] Okay. So the words here would be the whole list of chunks. All of them con coordinated together all of the final response of the l of the AI model. ansari. And then we will log, IE will save that to the database. Okay, so the [00:19:00] log save the assistant response to the user's current thread in the database.

[00:19:03] Okay, this is what this does. Again, I'll explain that part ansari, DB later. And this is a trickypart. If we call the else if we are using a tool, not words. 


## [00:19:15] Processing Tool Calls and Logging

[00:19:15] So if the response in the chunks above were was a tool related, a tool, not the normal response of the LLM model then.

[00:19:22] We will this we will do the following logic. We'll have here a succeeded bull and we will do a for loop for all the tool code. Again, I [00:19:30] think this will only run onetime because again, I think we only have one element here in tc. But anyways, and we will say we'll get the tool name and tool orgs and two ID from the tool called dictionary, the defined above.

[00:19:41] And we will pa pass all of that to self process tool call function. Okay. Again, this is I toggled word wrapping, so that's why this is the same line. Okay. Anyways, and so we we call this method and we pass these details and we get the output from the tool. Okay? From the function. We get the output, it's output, and [00:20:00] we get an internal message.

[00:20:01] We explain that later and we get a tool message. What the heck is that? Let me, okay, let me continue with this function and then I'll get back to this one. Okay? We log the tools response to the user current threatened database. We say that if it was successful, so no exception occurred, and a self message log is none.

[00:20:18] And this is this is the message log which actually saves stuff to the database. So if it's actually defined, if we define that, if we define to save things in database, then we want to save it. How do we save that? We add a tool [00:20:30] details dictionary here. Okay, and I'll explain that, and then we log that as well.

[00:20:34] Okay. We log the tool details and then we log the output of the tool, and then we log the tool name that we used. Okay? We log all of that to the database and that's it. Now comes the final question. What the heck is this? 


## [00:20:46] Defining and Using Tools

[00:20:48] What is process tool called as from its name we process. The the LLM the tool that the LLM wants to call.

[00:20:55] Okay. What is that? We passing the following the two name and arguments and ID [00:21:00] because we have multiple tools and ansari we wanna know what the tool name is. So let me first go through that logic. If two name is not from the list of two names that we define in, ansari. Then we say that this is an unknown tool name.

[00:21:11] This should never happen. This should never happen. Okay. Because we tell, ansari, we tell the LLM provider the tools that we have and we tell them their exact names. The LLM should never mistake their names. So I don't think we ever got that. Okay. I don't think so. But this is here. And then we say if this is okay, we try to [00:21:30] load to do loading into a into a dictionary.

[00:21:34] The tool_args string. And so what the heck is that? Okay. What is two orgs? Let me give you an example to to imagine the situation. 


## [00:21:41] Formatting Tool Arguments

[00:21:43] Let's say the user says tell me Aya two. Two, okay. And so ansari decides that this is a tool called we can get, we can use a tool we have called Search Quran.

[00:21:53] I'll explain that in a bit. Okay? And we can pass through that because we can pass through that. The I number. I number, okay. [00:22:00] I number, which is a string. Okay? And we define somewhere, I'll show you that later. That search Quran expects a parameter called a number, which is formatted like this.

[00:22:10] Okay? So basically what will happen is if the user asks something like this, okay? The LLM will infer that okay. The from my code base that the developer has written, I am aware that we have a function called Search Coon. And I'm aware that this function needs an I number and I'm, and I deduced that the user query has an I number here.[00:22:30] 

[00:22:30] So let me pass that. Let me pass that into here. Okay. So now this will be converted to a tool arguments Okay. To tool arguments. And so how does the LLM write the format of the tool argument? It, write it like so it write it as a dictionary. Okay. And I just wanna remember how it actually gets written to s arguments to s I think I, yeah, if I remember correctly, it, write it based on on how we define the functions.

[00:22:59] So [00:23:00] we define it with anum, so we'll probably see the model returning some dictionary. Which like, which is like a and m. Okay. And then it's value to two. Okay. This will be returned. So actually two orgs is a string that looks like this. So this is quotable. Like we can code this into Jason, like in, we can Jason load this?

[00:23:22] From a string like that to a dictionary, dictionary will have a key value. And I'm mistaken here. It's section, not item. It's query. It's query. So it's written here, [00:23:30] query. And so from query if I load that, we get the dictionary, which is like this, and using the query key, we get the value like this.

[00:23:37] And so this value will be here, will be in query. Okay? And now we can use query here in thispart so we can say. We get, we can get the tool instance, which is either surgical on hadis or can be other search tools. I want to update this actually. And this tool instance will be the the function tool that we get from here.

[00:23:54] Okay? What is here? This is this part. 


## [00:23:57] Mapping Tool Names to Instances

[00:23:57] When we define Ansari, we say that we have a two name, two instance dictionary, which maps two. Name two is instance, so we have two name. This is a function that we define in other files like search qu on, and I'll explain that later when I get to the tool section.

[00:24:10] And it mentions its two name, which is search qu on. Okay. This is the example that I've been given and we say that this search qu on key is value, is this search qu on instance, which what we defined here above in the initiative in the net as well. Okay, so we just map the keys, which is the two names to the values, which is the class instances, search core.

[00:24:29] These are the [00:24:30] tools that the class of search core on. Okay. Which contains the function that I need, which is search core on function. Okay? And we get that to nim. Okay, so for example, for, in our example is croon, and then from this croon class, we run the function run as list. Okay.

[00:24:47] This is a method inside croon. Okay? Which, for example, is here. It takes a query and then we process it. Using the run function which, and the run here just calls an API to, to [00:25:00] an online service, which returns from us the most relevant AI based on the AI that we sent here in the query. Again, I'll explain that later.

[00:25:06] So yeah, this is this is the part of the tool. And so what will we turn? Okay, hopefully I have time to explain this. It'll return the following. Results. I wanna see what its structure is like results is based on the results of this. This is just an implementation. 


## [00:25:23] Finalizing Tool Call Processing

[00:25:24] So this result is now based on like here, okay, let me again, my thoughts.

[00:25:28] The part of the Virginia I is done. [00:25:30] Okay. What was the part of Virginia I is that it tells me how we can convert the user query and such that we get the argument that we want and we permit it properly. This is what where the Gen AI part ends. Okay? And so once we got that two column two in a proper format like that, we exactly it here, we're done.

[00:25:47] The AI part is done. All of that. These are code, these are code that we have written ourselves, and these are functions we have written ourselves that returns a list of values a list of strings that we implemented ourselves. This will be the list of relevant areas, [00:26:00] I believe. Okay.

[00:26:01] And these are the results here. And all of that is code that we write ourselves. And so tool definition here all of that, okay the remaining code here is part of how we make ansari, realize that this part of the message history is related to a tool not related to the user, or not related to an assistant.

[00:26:19] Just leads to the tool. Writing messages with the tool generated by tools has has a different format than the normal rule and content dictionary format that we talked about. [00:26:30] So we previous said that if you want to say we have a message from user, we just say rule, and then we say user, and then we say content, sorry.

[00:26:40] And then we say hello. Okay. The same thing for for for the l. ansari, but we say here Assistant. Okay. Assistant. So can't remember it's written like that anyway. But if is the rule is tool. Okay. The structure differs a little. The content here will be empty, if I remember. And and we add another parameters that I'll [00:27:00] talk about in a bit.

[00:27:01] Okay. And we add a message before that even, and after there are some changes okay. That we do. So I'll get to that in a minute. But that's the initial logic of the process tool calls. We format the the structure of the message, return from a tool in a way that I'll explain a bit.

[00:27:16] Okay? That's what's happening here. And then we put all that in the message history, okay? In the message, internal message, and the actual format of the final tool call. All that we appended to the master history. And then we return. These are related to [00:27:30] the tool formats of the message that I'll explain a bit.

[00:27:33] Like this part, okay? This part and the internal message that we would explain below. All of that is returned here. Okay? And that's what's logged what? Get logged get logged in here, in in this part. Okay? So this is actually the final part of post one round. 


## [00:27:49] Conclusion and Next Steps

[00:27:49] And with that, I think we're done with the, with ansari.

[00:27:51] What I still didn't explain is the details of the tool. As you saw, I already skipped this through that part, so I'll return back to this in a bit. Okay. The how the [00:28:00] tools are formatted. And after we finish the tool logic, we'll be finished with Ansari 2.0, and then we'll go to, ansari, workflow 3.0. 

