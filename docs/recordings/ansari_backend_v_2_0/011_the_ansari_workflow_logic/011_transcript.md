# Ansari Backend V2.0 - 011 The Ansari Workflow Logic


## [00:00:00] Introduction to Ansari Workflow

[00:00:00] here we're going to explain the Ansari workflow .py. And I thought I'd explain this a little bit different. I'll read this summary that I made when I skimmed through the code, but instead of over preparing for this part of the recording I'd rather actually explore the module and where it's called and everything with you so that you can see like a demonstration of how I navigate the code base and.

[00:00:23] Maybe you can follow something similar to what I'm doing here in the future. If you see any other code that I didn't mention in this [00:00:30] according. Let's read together. 


## [00:00:30] Overview of Ansari Workflow 3.0

[00:00:38] The file aims to redefine. Ansari for version 3.0. So this is a new version that we're aiming to, to deploy soon. I don't know if it will if it will be deployed when when this recording is out. And in that version, we hope that Anso workflow is the main driver behind our application. Instead of the Ansari file, I'm not sure yet if we're going to still use Ansari file or we'll migrate completely to Ansari workflow .py. So anyways, this is a new step that we're [00:01:00] trying to make.


## [00:01:00] Modular Workflow and Tool Usage

[00:01:00] And so we want to apply this workflow which is a modular workflow to process user queries. Okay? But since this is a workflow, the usage of tools, remember the recordings that I made about tools. Previously this logic now will not be determined via l LMS inference anymore. So if you remember, I said that the LLM is the one that decides whether the U user query requires a tool response or not. And so this determination won't be based on the LLM anymore, [00:01:30] at least in this part. Ansari .py. Instead, the workflow steps could be defined to include tool usage. For processing user queries. So based on the type of user queries which we can determine on our own, we will automatically insert a step for a tool usage within the pipeline, within the workflow that we have these workflow steps are defined via API endpoints in main\_api.

[00:01:52] We, we'll go to this part in a second. Note, when I say note like this it is probably a technical note. Okay. Or a note [00:02:00] regarding how to navigate things, how the code works, et cetera, more than the business flow or what we're trying to achieve in a general sense in the project itself. 


## [00:02:08] Navigating the Codebase

[00:02:08] In my opinion, a good way to navigate this file is to start from the execute workflow method as it's made by main\_api .py. Entry point to ansari workflow recursively, see which method scores, and then go back to this method. So this is what I'll try to apply with you right now. I actually don't remember what I'm going to see because this, that recording is a a few days later. So let's explore together. We'll start navigating from the [00:02:30] execute workflow, as I said.

[00:02:32] Again you have multiple functions. You multiple methods here. So that's let's just sort here execute workflow. 


## [00:02:38] Defining Workflow Steps

[00:02:44] This function handles the version three logic idea is to have Ansari, execute workflow. That can be a list of steps. Okay. So these are the allowed steps. And they're based in on different tools that we have. Steps, step name to function. This is a dictionary which maps. Each step name to the function, which will execute it. And I believe some of these functions include tool usage. I [00:03:00] think we'll go to them promptly enough. But but yeah, these are functions that we define here, methods that dictates how to answer based on the step name. Okay, let's just see an example of where this is mentioned. Maybe it'll clear things up a little bit. 


## [00:03:15] API Endpoints and Workflow Execution

[00:03:18] If you go to the main\_api .py, we see here that in an API endpoint called API version two A. Okay. I'm not sure if version two remain like this or B version three, I'm not sure yet. Let's just wait out and see.

[00:03:28] If a part of the [00:03:30] front end requires this API endpoint or calls this API endpoint we run this function, okay, which creates Ansari workflow instance with a specific system prompt. So this is a new system prompt, other than the one that I told you about, the, hello, Ansari, I'm an assistant to help you, et cetera, et cetera.

[00:03:47] It's similar to that, but tailored more to , requests regarding Ayahs. Okay. In Quran. We define the instance and the Ayah ID We have a way to calculate it here based on the surah on the. [00:04:00] And the I check if the answer is already stored in the database. Okay. All of this logic is the database, but here is the part that interest interests me, the workflow steps.

[00:04:10] So here, since I know I'm coming from the API endpoint here, and I know the question or the thing that I wanna answer is related to as then I know that I want the workflow to be as following, we have a third step. Okay. Like a list of topples and the topple here consists of the search step and what will pass to it.[00:04:30] 

[00:04:30] Okay? Query the query, which is a question coming from the user, from the front end and the tool name. So if you see here, we sp specifically specify the tool name to, to. Okay. We didn't leave the logic to the LLM to infer anymore. No. We know here that we're coming from the front end from a part of the interface where the user wants questions related to is, and so we know that we'll use that tool.

[00:04:52] Okay. The tool of for example, search of series, a new tool we're working on. And so yeah we'll send that to him here because now we know. What the type [00:05:00] of question is. And then the metadata filter. Okay. All of that will be required by the Ansari workflow agent. This is a step of searching and then the to generate query, we take that input again from the user. And these parameters are other parameters that the that the equivalent functions that I'll show you in second need. Okay. After we do these workflow steps, we execute what have we define them?

[00:05:24] We execute them here. Okay? 


## [00:05:25] Tool Responsibility on User Instead of Model (Unlike ansari.py)

[00:05:26] So again the main thing that I want you to take from this, because I'm not going into [00:05:30] details with each line of code here, is that we migrated the logic, the responsibility of deciding the tool to be used from the LLM. To infer it we migrated that responsibility to us.

[00:05:42] Okay? To the developers who put in the who know that here we come from an endpoint that wants something related to ai. So I know that the, that I wanna use a tool related to ai. So the responsibility is now ours to choose a tool based on where we're coming from the front end. Okay? This is another way to approach things.

[00:05:59] And you [00:06:00] can see here that these steps, workflow steps here is best here. Okay? List of top of the one that I showed you in a minute. And it's used here. We take the step name and step parameter and we pass that to the output dictionary. Okay. And okay. One second. The outputs here takes, yeah, it calls it, this is a call.

[00:06:24] And we take the step name to function. Which is a dictionary we passed with the step name. [00:06:30] Okay. Which is passed here in the main P. So if you remember here, for example, search, we said that search here is a key, first key. So in the first four loop iteration, we pass in search. Okay so now this part that I'm highlighting, we'll give us back the this function. Okay? So this is now a function, okay? Is now this, and then. Since we have a function, we will call it by doing this parenthesis right here and say and test it. Step pars and outputs, which are from the workflow steps [00:07:00] here. Okay, so step primes here is the, what I'm getting here from the main\_api code.

[00:07:06] Okay? And the outputs we're passing it because within that function. We are we are using the current outputs. So for example, the first time outputs would be zero, because that's the first step. So this function, which is this function, will give us a result. This result will be appended to outputs.

[00:07:23] And then in the next situation, we'll use the outputs , which has the results of the first step. We'll use it back as an input in the second [00:07:30] step. Okay. So can you see the loop that's happening here? Hopefully you can follow along. And this for loop will execute each of these functions based on the parameters paused in the dictionary in here, in this part.

[00:07:41] Okay? And all of the outputs. Of these steps will be returned to us. Okay. And then this output will be used, will be processed and used. So taking the outputs we use, we're using only the last one here as the, Ansari. Answer the final answer. And then returning that to the user. So this is the main logic.

[00:07:59] Of or the [00:08:00] main idea of using the workflow agent. The, is the specificities of each step here. I'll leave that to you to search in. And to be honest, the documentation on the prompting here makes, it, makes this semi English like enough for you to understand once you read through them.

[00:08:15] And so I'll leave that to you. 


## [00:08:16] Conclusion and Further Reading

[00:08:22] This part was related to the Ansari workflow agent. I don't think I need to explain it further. Again, the most important lesson that you can take out from this part is that the tool responsibility is now we specify that explicitly instead of [00:08:30] letting the LLM say it itself. Okay. Or at least let me search with you just to make sure in the tool here Yeah. We literally running it. We're running the tool. See, run. Remember this function? If you recall what I explained in the tools, if I get, go back, for example, in search core on. Where is it? Search Core on? Okay. We have run as list and run a string. I explained Run as list before. That's what we used in ansari.py. So apparently, because I'm seeing this with you right now, we are using run [00:09:00] as string in Ansari workflow here. Okay. So you'll follow along, you'll just read it one bit by bit.

[00:09:06] And the intricacies of of this class, you'll understand it once you read the Code base. Okay. So that was regarding the. Ansari, workflow version 3.0.

