# Ansari Backend V2.0 - 010 The Ansari LLM (Cont.)


## [00:00:00] Intro

[00:00:00] Okay. Hello everyone. In this session we're going to continue the, the process, the tool logic that I skimmed through when I explained it previously. I skim through a lot of parts, so hopefully in this one I will explain more in more detail how tool works. Okay. 


## [00:00:17] Deep Dive into Tool Logic

[00:00:23] So we were previously here in, in this function process, tool\_call, and we saw how it gets used here.

[00:00:24] We get. Strings again, messages. Okay. Or dictionaries of messages. And then [00:00:30] we log that into the database. And internally this will will add these messages to the self note message history, the message history that we have the current chat that we have with the user. Okay, so that's what we know, but what's happening here?

[00:00:42] What are these exact things and what does process, tool, code do internally? So let's go through that one by one. Okay. So let me open up Zen mode here. Okay, so you have let me go line by line here. Again, I said the supportive tool name is not in the list of two names that we defined [00:01:00] above.

[00:01:00] Above, in, in here, okay. In the good get tool name function. Then we return. 


## [00:01:05] Exploring the Search Quran Tool

[00:01:08] Okay, so let's, let me go take a drive deep into a deep dive, Ansari, into the, into this class the search Quran or clause. So search Quran. All of these are in folder, the called tools. We have a couple of files here.

[00:01:24] Okay. Search. These are all the tools that we have in the system right now. And they all have the [00:01:30] following structure. So I'm going to explain one of them and then you understand how the rest works. We take any, like global variables. Any keys here? For here, we're using, I'll explain that in a second.

[00:01:39] And then we have the tool name, we specify that globally as well. And then we define the class here. Okay. What does this class to? We take these keys. Okay. Right here as attributes, and then we get the tool description. What is the tool description? Okay. I'll tell you what is the description in a second.[00:02:00] 


## [00:02:00] Tool Description and Parameters

[00:02:00] Basically, we are trying to give a description to the LM, which is in our case GT or OpenAI model, and we're saying I want you to recognize that we have a tool, we have a function that we defined ourselves as developers and this function is called cro. Okay? That's, is its name. Now I want to tell you, Mr.

[00:02:25] Elem, that in order for you to deduce that the user [00:02:30] query could be answered by running this tool you can understand this description that I will give you. What is this description will be? Was saying search and retrieve a relevant as based on a specific topic, returns multiple as when applicable.

[00:02:43] Okay, so this is it, its description we're describing here. How do we and when do we expect this tool to run? Okay. And the other m understand this and so when applicable, and so when we, when the user asks a question related to specific as. And [00:03:00] it's normally related to the user wanting to know about certain is.

[00:03:04] Again, know about IA two colon two, or no is about patients or whatever. Then the LLM will see the descriptions of all of its available tools and then say, okay, based on this description, I see that the user is technically trying to search and t relevant A is based on. A specific topic, which is patients in this example.

[00:03:25] And so let me return to him multiple ayahs, okay. Using this function, okay? The [00:03:30] function called search core on search. Okay. And so that's what the LLM tells itself internally. We also tell the LLM the parameters that we expect this search core on to to have. We say that the the we have a type of object.

[00:03:44] This, I think this syntax is standardized. Okay. And then we say here, in this part, the parameters that we expect to be passed to the function. Okay? 


## [00:03:54] Handling Queries and Parameters

[00:03:57] Here's the tricky thing that I actually explained wrongly in the previously Yeah. Couple of [00:04:00] in the previous recording or a couple of minutes ago, is that remember when I told you.

[00:04:05] Let me get back to the query part. Query. Let me see, we'll see where it is. No network workflow steps. This is only, yeah, remember when I said that? Remember when I gave example that the tool orgs when the tool, when the LLM returns arguments, we say that it's returned like this.

[00:04:27] Okay? We say query. And then [00:04:30] the 2.2 and the example that I gave, remember that part? That's not completely, that's true in this case. That's what's happening here. But I said that I think I said that this is the standard syntax that we always get. The, no, this is not really the case. It depends on how not we say.

[00:04:45] To the, in the description of the tool that we're using. Okay. And since we're using multiple tools, we had to standardize. What do you, what do we have to standardize? We had to say, if I recall correctly, in each of these [00:05:00] return values, like in each of these descriptions of the Search Quran tool and of the search model tool and tool of the tools, we had to say that we expect a parameter called query.

[00:05:09] Okay, so I believe if we go here Hadiths. Okay. Why is the file not found? Okay, one second. Did we delete that? One sec? Where is the Explorer search? Hadiths? Yeah. Okay, sorry. And I wanna hide. Okay. Yeah, you'll see query here as well. [00:05:30] Okay. So that the structure is similar and we acquire a query. The query here means that when the LLM calls this, or when the LLM recognizes that we need this function, okay.

[00:05:40] And generate the generates parameters for it. The LLM must generate the parameter called query. That's what requires me. Okay? And so if there are parameters defined here but aren't mentioned required here, then the LLM can or cannot or may not generate them. Okay? So that's [00:06:00] another thing based on what it sees fit based on the user's description the user's.

[00:06:05] Okay so this part, the query here has to be mentioned. 


## [00:06:08] Tool Usage and Response Handling

[00:06:09] And when we say this part again, we are saying, okay, LLM when we, when you generate for us parameters or arguments, okay? Based on what you understand from these queries. Please mention the parameter's name as query. Okay.

[00:06:23] That's what this part says. And this query, when you generat it, we expect that to be a string. That's why you've seen the example that I [00:06:30] gave a query and its value is two column two. The A the the surah and diverse number. It'll be a string because we specified that you shall return to the string.

[00:06:39] Okay? Okay. So what if this was an integrator? Okay. And the search AI function just gets, use the surah not the verse. Then we would've returned something like this. It would've been query and then one, two for surah to back around, or one suta. Okay. And it'll be like that. It'll be like that.

[00:06:59] But this obviously is [00:07:00] in a string. And the value will be an integral if we specify the type to be an in. Okay. That's an example. Again you have to return to open ai documentation to see what it expects, like maybe tool calls in, in open ai. Expect. When we say an int, we say it an integral, not an int.

[00:07:16] So these are just terminologies based on the SDK that we're using the provider we're using. So you can return back to that for reference. And and the description for what this query for what this parameter represents, description, topic, or [00:07:30] subject matter to search for in haddi collection.

[00:07:31] But because this is Hadiths, so Ansari, I should have returned to our search for on example. Search Quran. You'll see it here. Topical subject matter to search for within the Holy Quran. Okay. This along with the general description of the function, the LLM understands internally and then sees any user query when they ask the front end of ansari and say, okay, based on what, from what I understand from the description here and the description of the parameters here, I think this function is a function [00:08:00] that that we want to use internally.

[00:08:01] Okay? So that's how it maps this logic. So this is a good tool description. Where do we use that? We use that. And again, all of that syntax, the way we write this syntax these specific key names, these are based on the documentation of open eye. Okay? Okay. So where do we use that? In here instead of the tools attribute?

[00:08:22] And Ansari. We we is a list of the two descriptions which is a list of strings. 'cause that's a return value of two description. [00:08:30] Okay? So these are are the descriptions for the tools. And so where do we use this? Use it here. Remember that part when I was discussing the unpacking thing with the parameters to be passed?

[00:08:41] We say to light lm. To pass these parameters to the model that we're currently using, which is open I, which GBT model. And we are passing this parameter as well. This is a parameter of tools. So if used tool is true, which is which we state here in the, on calling this function, then we we will unpack [00:09:00] this key value peers.

[00:09:01] So the tools is the thing that I was just saying. The model expects the light LLM expects in the parameters, a key core tools, and then the value will be a list of descriptions of the tools that you have. Okay? For example, the one that I just showed you here. Okay. And Ansari, this list did I say string?

[00:09:18] It's a dictionary. Dictionary. Okay. The descriptions are dictionaries. So if I, because I said a minute ago, I said oops. I said a minute ago that this was a list of string. [00:09:30] No, a list of dictionaries. Okay. Yeah. Hopefully you caught on that one when I made that mistake. And then the tool choice is auto, what does this mean?

[00:09:37] It means we okay, so basically we're saying. GPT or OpenAI, we instruct you to use this tool in what fashion? Either "auto" or, I can't remember. Its other options. You can offer the documentation of OpenAI. I think maybe always or like function which is like a, another value stating.

[00:09:55] We, you should always use tools no matter the query that the user gives you. You should always [00:10:00] use tools and so even if you think all the tools that we have. In the system, if we think all of them don't really match the description of the query that the user wants, you still have to use one of them.

[00:10:11] So you use the most one you think is possible, even if all of them are really not likely to be what the user wants. This is another value, but we don't do that. We make it auto. If you think all of the tools that we have don't really don't really have a high probability that they will give the answer that the user wants then then don't use tools.

[00:10:29] Just use a [00:10:30] response with normal words as a LLM always does. Okay, so this is another thing. Hopefully this is explained and the response format, I explained that before. 


## [00:10:41] API Integration

[00:10:44] Returning back to the tool of search core on this is a tool description. The tool name is just a wrapper. It's just an section to get the tool name that we defined above, which is, in our case in this fight, is Search Quran.

[00:10:52] And the run function is, I believe what we call. Can you please help me out [00:11:00] in, yeah. Okay. It's in okay. So this is like an internal function here. It should be prefixed with an underscore, but, okay. Anyways let me actually skip that and go to the. So the functions that we care for here run as this a thing.

[00:11:12] These are the ones that we call actually in ansari, we call here in the part that I explained before quickly is that we get the results, we get the final values returned from the function that we have, the tool that we have. We get the values from them from this function. Okay? And again, if you recall in the context of search core on these will be a list of [00:11:30] ayahs.

[00:11:30] So if the user a asks, okay, tell me about the, is the two two, two and two three and two four, for example. Then this test will be that. So that's that's the thing as well that will give you the most relevant tools from the user query. Relevant is from the user query. Okay?

[00:11:47] And it'll be a list of strings. Of a in here. Okay, so what does this run assist do? Let us go and see what it does. Session Core on four, the query here. So for example, two, column two, [00:12:00] and the default number of results that we return. 10. Okay, so we try the 10 most probable results.

[00:12:06] Obviously in our case, if it's just a two column two query, then then only the first result will matter for us, but we return the others nonetheless. And then we run this function, which will return us this these ayahs. And for these ayahs we format them in this function takes the Ayah number from so this is a dictionary, okay?

[00:12:26] The results is, are list of dictionaries. So all here is dictionary. And we [00:12:30] take that all and pass it to this function, or here is called a, I dunno why it's called a R for, okay. And then we take the from each dictionary, we get the id. Sorry. We get the id, we get the text, if any which is in Arabic, and we get the text in English, if any.

[00:12:46] Okay. And then we, it like, so a then I number and then the Arabic text for this a and then we see it in Arabic and then we see it in English. So that's a string within the string here. So this result will be a string. And we do that in a [00:13:00] loop, so we have. A list of strings. E string is an Ayah number and it's Arabic and it's English.

[00:13:05] Okay? This is what run as this does as a string is basically the same thing, but this will not be a list. It'll be a string. So that's why we say a string. Okay? And we separate it with a new line. This is the thing. And so what does run do? But this is the core logic, this is actually where the function is happening is in dot run.

[00:13:23] so.run here. It is just an API code. We say the headers that we have, we serve API key, which we define above, in [00:13:30] which is this one, API key met, and this which is in the environment variables in the in, for example, environment variables you, you should define in here. Where is it? In here, token. And then you have.

[00:13:49] Oops. You have payload query which is a query 2.2, column two, whatever number of results, which is stand by default, or did we? Okay. We left it here as five, [00:14:00] but I think we pass it here. Yeah, we pass it to 10 because here the full is 10 anyways, anyways. And then the the get text one is the Quran.

[00:14:08] Okay. There's a type of the return that we want. So one, because it's all hard to code because we always want the Quran in this case. So the final question is what is this? What are we sending here? What is this base l what is this API actually, if we go together and see it. In here. Let me up.

[00:14:26] Design mode and, um, [00:14:30] get up here. Mm-hmm. Okay. What was it? Uh, 'cause that's actually API, um, I want uh, a second. Will this give me. The search kalimat. Okay, so kalimat dev, the API is obviously it won't have a ui, so apologies for that dumb search. Yeah, so this is just a service that allows us to, to get AI powered searching for yeah, excuse.

[00:14:56] Ansari. This was needed before. Nice. 


## [00:14:59] Exploring the API Results

[00:15:03] I'm glad they added that. Anyways uh, and then you can you can see an example here into something from the Holy Quran. So if I say. 2.2 we get the Quran and sun and then the Quran, we get the ba and it's English equivalent is this. And so that's, if you can imagine now the API from the API will get that.

[00:15:20] We get the first couple of results. 


## [00:15:21] Handling Multiple Results and Parameters

[00:15:26] I'm actually glad that now this returns only the first result. This is amazing because if I now search for two, two and get the first 10, you remember that parameter? 10, 10 [00:15:30] values. It actually will just get, give us one because the API itself will return the nearest.

[00:15:35] Um, Which is the first ayah. So even if we set it to 10, in this specific case, we only get one. But if I actually write patients, okay, we get something like this. All of them are related to patients and perseverance from different messenger, from a couple of examples here. And so this is we can get all of this, we can get the first 10.

[00:15:57] And we get, it's English and it's Arabic versions, and then [00:16:00] we send that. So we have that for the, for here. And then we have all of that is for koan, which is one get text one, and then for the Asana. And we have them as well in here in English and Arabic. Amazing website to be honest. So that's a tool that we have.

[00:16:12] Okay. 


## [00:16:13] Understanding Tool Functions and Code

[00:16:21] So again, why are we using this tool just to reduce the possibility of ansari, hallucinating as, and we don't wanna do that, so we try to get them from here. Okay. So this one is for the Quran. You see the similar one for the Hadith, but to be honest, the rest of the files structure in a similar way.

[00:16:28] So I will not go through them, but if you [00:16:30] understood this logic, then we're good to go. Okay, so now you understand. And another thing that you might have noticed is that I kept seeing tool to, we have this tool, we have this function, we have this function. We define the function in the code, there is a function.

[00:16:42] You'll see that actually the tool or the function code, search core on. Search qu. This is technically, there is no actual function in the system that we have is called Search qu. Like we didn't say def search qu and then all of the No, but you can imagine we did something like that. [00:17:00] And then we say that this accepts a query and this is a string.

[00:17:03] Okay. And in here we put the dog string of of this part. The assert and achieve is based on whatever. And that's, that description is what we put in doxing here. And then in here we call the API of the just show. You can imagine that. Okay. Or that's at least what the LLM imagines.

[00:17:20] So when I say to the LM, Hey, we have in our system a function called search on which is this subscription and expect this parameters, the LLM will say, okay, and that's all that it knows. Okay? [00:17:30] It doesn't know the doesn't know that we actually have this as a clause and this clause has, these methods and that we use the run as list method first, which runs the run and PPA methods and then all of that.

[00:17:41] We don't the LLM doesn't know that. It just knows this description based on what we gave it. And so what we care about only from the LLM is that from the user query, which is free form text. We just get the keywords that the user wants to search for. So for example, patience and then perseverance, and then we get these.

[00:17:57] Keywords. And then we [00:18:00] the LLM the AI is is responsible for that for just summarizing and extracting relevant if from the user, getting these keywords and then passing that as a as a as a value to the parameter that we told that its name is we. Okay? So just have this visualization in your head.

[00:18:16] Okay? 'cause that's the most important thing about tools. Basically one last time when we say we applied tool functionalities in LLM, what we're saying is we tell it, please, from the user query, see [00:18:30] if it it can be solved. The user question can be solved by one of the descriptions that I gave you in these tools here.

[00:18:36] And if you think these descriptions match the user's query, then please extract the relevant info from the user's query and send it as a parameter. To me. Okay, I'll handle it. When I get that parameters, I'll handle it. How did I handle it? In here and run as list. I handle it here by, by by yeah. I ended by getting the query.

[00:18:55] This is a query that I got from the ai. Okay. And then I handle it by doing this [00:19:00] function process tool called, which will use that AI obtained query from the user, and then run it. In this run, this which I meet Okay. In the code. Just hopefully this logic is now clear to you. And this was a logic of tooling.

[00:19:13] The only thing that remains is the structure of the messages re related to tools. 


## [00:19:18] Message Structure and History

[00:19:23] So once we got the query, once we got, Ansari, the results, which is again, you can visualize now just a list of strings, list of the ayahs I number English and Arabic, this list of strings. What do we [00:19:30] do now?

[00:19:30] Okay, we need to define two messages. Okay, two dictionaries and add them both to the message history. How do we make this definition or what told you that this is what we needed to do? This link can visit it. I said here we have to first add this message before any two response as mentioned in this source.

[00:19:47] You can read about that to computational of opening eye. So basically this is what we're doing. We are adding some, an internal message. There's a message in the history that we internally add ourselves with a role, the role [00:20:00] of assistant. We must do it like that. Read the documentation. We must. This is, we have to hardcode this like that with the content as an empty thing.

[00:20:07] We also have to hardcode this and with tool call, with a tool called a key, which expects a list of dictionaries. Okay. And which will be a single dictionary with the type and ID and function keys. All of this is hard. We have to resist this structure. See here, to understand, I just took it from the documentation.

[00:20:26] We have to make it like that after we do that. We [00:20:30] say that the type of what you're about to get is a function with the idea of the tool id. The tool ID was achieved earlier in the code. You can trace it yourself. It's easy to be traced, to be honest. And then the function from the tool definition.

[00:20:42] Okay. This definition is another definition I quickly made here with name and arguments. The name is a tool name, which is search for on our case and arguments is the two orgs, which is the which is. The string itself. So this expects a string. So this should be a string like this, like query.[00:21:00] 

[00:21:00] Okay. And then 2.2. Okay. Two. Two dot two. Column two. We have to pass it as a string. This is a string. This is a string. Okay. And then we pass that here. Okay. And you'll see, because the two, two, this is a thing that's actually generated by the tool. Okay. Yeah. So we put that here. All of this, we have to do it like that.

[00:21:23] Okay. Based on the link here. So once we set up this internal message, using this structure, we add it to the message history. [00:21:30] Okay? Again, let me make you understand why we are doing what we're doing right now. Okay. Just to, so we are on the same page. You have the message yesterday. Okay.

[00:21:40] Sorry, my amazing drawings, which is just a list of dictionaries, first dictionary, second dictionary, and all of that. First dictionary has a user, or actually the first dictionary is a system message. You remember system when we said that this is, hello, ansari, et cetera. This is a personality of, Ansari, this is always has to be the first message.

[00:21:56] And then we have what do we have? We have a user message [00:22:00] with a message with a role user. It says, who are you, for example? And then we have a message saying from assistant saying, Ansari, and it's response. Okay. And then we have this chat like that. Okay. This is a history.

[00:22:14] So now we have, now we want to add, a new entity to our conversation. So we have the system, which is just a single message, and then we have two entities, the user and the assistant. 


## [00:22:24] Integrating Tool Responses

[00:22:28] We want to add a third entity right now called the tool. Okay, so wanted to get the tool's, opinion, the tools talk [00:22:30] to us.

[00:22:30] Okay. And we add that talking to the history that we have connected, the chat that we currently have, add tool to the chat. And to add it, the tool talks in a certain way, like the tool has to be written in this message history in a certain way. Or, let me rephrase this sentence, the message history.

[00:22:47] Okay. Or the LLM understands this message history and understands that the way that the tool talks, if it talks in the format that I'm explaining right now, what is the format? The format [00:23:00] is the following. The tool has to first put an internal message, okay. With the role of assistant.

[00:23:06] Okay. And an empty string. Okay. This is what I explained right now. Okay. This is this part. Okay. So the, any tool that responds to us, any tool that responds to us has to respond to us, has to add a message in this format. Okay. This internal message. And then it has to append the actual, like the actual tool response, which is a role tool.

[00:23:29] Okay. [00:23:30] I'll show that in a second. And the actual arguments that, that it said, okay the query to column two. So if we see that horrible drawing here, you will see this part of the horrible drawing as the internal messages I explained. Okay, this part, and you will see the other thing that we appended message needed from dual, which is this horrible part.

[00:23:52] Horribly drawing part. Okay, so what is this message needed from tool? It has a following format, it role, tool, [00:24:00] sorry. And then the content. And here we put in the content something we put the results string, which is the results of the function, the results of the actual tool that we. We called in the backend.

[00:24:10] Okay. Which is the list of ayahs. Okay. Sorry. The list of ayahs that we have that I just show you a number and there's English and Arabic list of ayahs. List of strings. Okay. And then the two call ID that we put here, we put this here as well. So again, in the internal message, what do you have from the ai?

[00:24:28] From the tool, we have its [00:24:30] arguments. The arguments that has query. And two column two. Okay. And from this portfolio we have our backend codes response. Okay. We have that here, which is the list of i one as a string. I had two and all of that. Okay, so I actually made a mistake when I said a couple of sentences ago that this has to call into the, it doesn't have it has this formatting.

[00:24:56] Okay? So when a tool adds a message to the [00:25:00] conversation, it has to add it in this format, in this walkie and weird format, okay? This two messages like this with the keys that I just showed you, okay? But when an assistant, just a normal assistant, a normal lm. Return words in a, in just a free talk.

[00:25:13] It just adds a message like that the assistant rule and saying, hello, Ansari, I can help you with with et cetera. And then when a user talks to the chat history, they can just add a user rule with this message. Like this is simple and this is simple, but the tool is complicated. I don't know why.

[00:25:27] The tool has to write in this [00:25:30] format in a message history. So this is a message history. The tool has to write in it in this way. Okay. It's just two dictionaries. So all again, all of that's being done. Just to make the assistant in the future. So now this is it, this is the response, but that response, that list of, is we don't just wanna show the user a list of ayahs like that.

[00:25:51] We want to to make the model understand this list of a, as a, like a background for it, as like the context for it. And then. Paraphrase what [00:26:00] it understands from these is, and and like these is names and et cetera, and mention them to the user while adding the, its AI touch not destination, but explanation for it.

[00:26:09] If we, if the user wants to know is about patience and perseverance. We don't wanna output to the user. I two, colon two I two, colon five. We don't wanna do that. We wanna say, okay here there are a couple of ayahs about patients. One of them is I two, colon two, which is, and then says it.

[00:26:25] And then another ayah is two point two column four, for example, and [00:26:30] then states. That's the ai like flavor flair, not, I'm not talking about hallucination, is just paraphrasing. Just rewording. What's being said? Okay. So we wanna make the assistant understand this tool's response and to make the assistant like to make the assistant later here to make us be able to create a message.

[00:26:49] His here with the role of assistant. And it's final paraphrased response to the user. If in order for us to do that, in order for LLM to under to do [00:27:00] this we have to pass this message history and this message history will now include the tool response. And so for the, in order for the LLM to understand this response from the tool, it has to be for formatted in this way.

[00:27:10] Okay? So this is a summary of why we are doing it like that in the first place in order for this to understand that, okay? I would like to understand that. Okay. In order from the assistant to understand the tool has to communicate with it like that. Okay, this is a summary of everything.

[00:27:27] Hopefully I explained it relatively [00:27:30] well, except that for the drawing part. Sorry about that. And yeah, this is why we're doing this in the first place. So we appended the message native from tool. We appended the internal message. And so we returned them. So we returned that message native from tool, and we return the internal message and we return the actual the actual content.

[00:27:46] The string here, the content is the resource string and this is the, list of ayahs. Okay. List of strings of ayahs, but but made as a string. We just joined the results and we say an A two or column two, and then we say another relevant citation. [00:28:00] And then a to convert whatever all that is just a single string.

[00:28:03] We put that single string in ing and pass it here. And all of that's now added as a context to the LLM when it answers the user question. And so how does it do that? When does it do that? 


## [00:28:13] Finalizing the Process

[00:28:15] Does that in the following, after process, two calls finish. We now have set the, its responses in the message history, the message history attribute of, Ansari.

[00:28:22] And and so we continue here. It's logged in database, and then this function ends. When this function ends, when this function ends, we go back where [00:28:30] we go back here, and then we go back here in the Postma history. We finish this loop, okay? Or we finish this part of the loop and then we come back to the wild while the role is not assistant.

[00:28:41] All the two call ID is not in the last message. This is the case. This is actually the case because the last message that's currently sent here at this point is this one. Is this one, okay. This is the last message that's currently in the history and so this is not an assistant message. So we enter here one last time.

[00:28:59] If I recall correctly, [00:29:00] we enter here one less time and we say, okay, please take the message history. Internally, it'll take it in here and use it one last time to process the to process it, to generate an answer. So now it'll take all of this part okay. In the message history. And the model will now idu when we are calling the l lighter lamb completion this call, it'll now because we passed in auto, it was in auto here, so now it'll automatically choose that, okay, based on this context.

[00:29:29] Now, I don't [00:29:30] need to answer with the tool again, I'll answer with the. With the model itself. And so I will not use the tool and just use words. And so it'll use words to need this answer here based on this context here. And then that answer will make the last message in the history assistant. And so when we return back to that loop it'll have the final rule assistance.

[00:29:48] So this will be false like all these will be false, and the one will exit, and that will be the message returned to the user. And that is it. That is literally the, the what's happening here, [00:30:00] and again, it'll be technically returned to the user using the yield because we're leading. So when we're leading this yield will temporary hold the function here in order to return bit by bit in the replace message history here, which is mentioned in the complete in many API, which I explained before.

[00:30:17] I think that was the most complicated part of the entire code base. But, hopefully you explained it now. This is a, this was a tricky part. Anything else should be easier and hopefully now we have a, you have a understanding of, of what's [00:30:30] happening.

