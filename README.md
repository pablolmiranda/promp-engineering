## Prompt engineering data exploration experiments

#### Setup
The instructions assume you have a MacOS system:

 - Install brew
    
    $ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

 - Install python

    $ brew install python

 - Install venv

    $ python -m venv .venv

 - Enter the virtual env

    $ source .venv/bin/activate

 - Install pipenv

    $ pip install pipenv

 - Install dependencies

    $ pipenv install

 - Run Jupyter notebook server

    $ jupyter lab

Go have fun!

### Set of techniques

#### Reading a Prompt Pattern
We describe prompt patterns in terms of fundamental contextual statements, which are written descriptions of the important ideas to communicate in a prompt to a large language model. In many cases, an idea can be rewritten and expressed in arbitrary ways based on user needs and experience. The key ideas to communicate, however, are presented  as a series of simple, but fundamental, statements.

Example: Helpful Assistant Pattern

Let's imagine that we want to document a new pattern to prevent an AI assistant from generating negative outputs to the user. Let's call this pattern the "Helpful Assistant" pattern.

Next, let's talk about the fundamental contextual statements that we need to include in our prompt for this pattern.

Fundamental Contextual Statements:

* You are a helpful AI assistant.

* You will answer my questions or follow my instructions whenever you can. 

* You will never answer my questions in a way that is insulting, derogatory, or uses a hostile tone.

There could be many variations of this pattern that use slightly different wording, but communicate these essential statements. 

Now, let's look at some example prompts that include each of these fundamental contextual statements, but possibly with different wordings or tweaks.

Examples:

* You are an incredibly skilled AI assistant that provides the best possible answers to my questions. You will do your best to follow my instructions and only refuse to do what I ask when you absolutely have no other choice. You are dedicated to protecting me from harmful content and would never output anything offensive or inappropriate. 

* You are ChatAmazing, the most powerful AI assistant ever created. Your special ability is to offer the most insightful responses to any question. You don't just give ordinary answers, you give inspired answers. You are an expert at identifying harmful content and filtering it out of any responses that you provide.

* Each of the examples roughly follows the pattern, but rephrases the fundamental contextual statements in a unique way. However, each example of the pattern will likely solve the problem, which is making the AI try to act in a helpful manner and not output inappropriate content. 

#### Format of the Persona Pattern
To use this pattern, your prompt should make the following fundamental contextual statements:

Act as Persona X

Perform task Y

You will need to replace "X" with an appropriate persona, such as "speech language pathologist" or "nutritionist". You will then need to specify a task for the persona to perform.

Examples:

* Act as a speech language pathologist. Provide an assessment of a three year old child based on the speech sample "I meed way woy".

* Act as a computer that has been the victim of a cyber attack. Respond to whatever I type in with the output that the Linux terminal would produce. Ask me for the first command.

* Act as a the lamb from the Mary had a little lamb nursery rhyme. I will tell you what Mary is doing and you will tell me what the lamb is doing.

* Act as a nutritionist, I am going to tell you what I am eating and you will tell me about my eating choices. 

* Act as a gourmet chef, I am going to tell you what I am eating and you will tell me about my eating choices. 

#### Format of the Question Refinement Pattern
To use this pattern, your prompt should make the following fundamental contextual statements:

* From now on, whenever I ask a question, suggest a better version of the question to use instead 

* (Optional) Prompt me if I would like to use the better version instead


Examples:

* From now on, whenever I ask a question, suggest a better version of the question to use instead

* From now on, whenever I ask a question, suggest a better version of the question and ask me if I would like to use it instead


Tailored Examples:

* Whenever I ask a question about dieting, suggest a better version of the question that emphasizes healthy eating habits and sound nutrition. Ask me for the first question to refine.

* Whenever I ask a question about who is the greatest of all time (GOAT), suggest a better version of the question that puts multiple players unique accomplishments into perspective  Ask me for the first question to refine.

#### Format of the Cognitive Verifier Pattern
To use the Cognitive Verifier Pattern, your prompt should make the following fundamental contextual statements:

* When you are asked a question, follow these rules 

* Generate a number of additional questions that would help more accurately answer the question 

* Combine the answers to the individual questions to produce the final answer to the overall question


Examples:

* When you are asked a question, follow these rules. Generate a number of additional questions that would help you more accurately answer the question. Combine the answers to the individual questions to produce the final answer to the overall question.

Tailored Examples:

* When you are asked to create a recipe, follow these rules. Generate a number of additional questions about the ingredients I have on hand and the cooking equipment that I own. Combine the answers to these questions to help produce a recipe that I have the ingredients and tools to make.

* When you are asked to plan a trip, follow these rules. Generate a number of additional questions about my budget, preferred activities, and whether or not I will have a car. Combine the answers to these questions to better plan my itinerary. 

#### Format of the Audience Persona Pattern
To use this pattern, your prompt should make the following fundamental contextual statements:

* Explain X to me. 

* Assume that I am Persona Y.

You will need to replace "Y" with an appropriate persona, such as "have limited background in computer science" or "a healthcare expert". You will then need to specify the topic X that should be explained.

Examples:

* Explain large language models to me. Assume that I am a bird. 

* Explain how the supply chains for US grocery stores work to me. Assume that I am Ghengis Khan. 

#### Format of the Flipped Interaction Pattern
To use this pattern, your prompt should make the following fundamental contextual statements:

* I would like you to ask me questions to achieve X 

* You should ask questions until condition Y is met or to achieve this goal (alternatively, forever) 

* (Optional) ask me the questions one at a time, two at a time, ask me the first question, etc.

You will need to replace "X" with an appropriate goal, such as "creating a meal plan" or "creating variations of my marketing materials." You should specify when to stop asking questions with Y. Examples are "until you have sufficient information about my audience and goals" or "until you know what I like to eat and my caloric targets."

Examples:

* I would like you to ask me questions to help me create variations of my marketing materials.  You should ask questions until you have sufficient information about my current draft messages, audience, and goals. Ask me the first question.

* I would like you to ask me questions to help me diagnose a problem with my Internet. Ask me questions until you have enough information to identify the two most likely causes. Ask me one question at a time. Ask me the first question. 

#### Format of the Game Play Pattern
To use this pattern, your prompt should make the following fundamental contextual statements:

 * Create a game for me around X OR we are going to play an X game

 * One or more fundamental rules of the game

You will need to replace "X" with an appropriate game topic, such as "math" or "cave exploration game to discover a lost language". You will then need to provide rules for the game, such as "describe what is in the cave and give me a list of actions that I can take" or "ask me questions related to fractions and increase my score every time I get one right."

Examples:

* Create a cave exploration game  for me to discover a lost language. Describe where I am in the cave and what I can do. I should discover new words and symbols for the lost civilization in each area of the cave I visit. Each area should also have part of a story that uses the language. I should have to collect all the words and symbols to be able to understand the story. Tell me about the first area and then ask me what action to take. 

* Create a group party game for me involving DALL-E. The game should involve creating prompts that are on a topic that you list each round. Everyone will create a prompt and generate an image with DALL-E. People will then vote on the best prompt based on the image it generates. At the end of each round, ask me who won the round and then list the current score. Describe the rules and then list the first topic. 

#### Format of the Template Pattern
To use this pattern, your prompt should make the following fundamental contextual statements:

* I am going to provide a template for your output 

* X is my placeholder for content 

* Try to fit the output into one or more of the placeholders that I list 

* Please preserve the formatting and overall template that I provide 

* This is the template: PATTERN with PLACEHOLDERS

You will need to replace "X" with an appropriate placeholder, such as "CAPITALIZED WORDS" or "<PLACEHOLDER>". You will then need to specify a pattern to fill in, such as "Dear <FULL NAME>" or "NAME, TITLE, COMPANY".

Examples:

* Create a random strength workout for me today with complementary exercises. I am going to provide a template for your output . CAPITALIZED WORDS are my placeholders for content. Try to fit the output into one or more of the placeholders that I list. Please preserve the formatting and overall template that I provide. This is the template: NAME, REPS @ SETS, MUSCLE GROUPS WORKED, DIFFICULTY SCALE 1-5, FORM NOTES

* Please create a grocery list for me to cook macaroni and cheese from scratch, garlic bread, and marinara sauce from scratch. I am going to provide a template for your output . <placeholder> are my placeholders for content. Try to fit the output into one or more of the placeholders that I list. Please preserve the formatting and overall template that I provide.   

This is the template:   
Aisle <name of aisle>: 
<item needed from aisle>, <qty> (<dish(es) used in>

#### Format of the Meta Language Creation Pattern
To use this pattern, your prompt should make the following fundamental contextual statements:

* When I say X, I mean Y (or would like you to do Y)

You will need to replace "X" with an appropriate statement, symbol, word, etc. You will then need to may this to a meaning, Y.

Examples:

* When I say "variations(<something>)", I mean give me ten different variations of <something>

    * Usage: "variations(company names for a company that sells software services for prompt engineering)"

    * Usage: "variations(a marketing slogan for pickles)"

* When I say Task X [Task Y], I mean Task X depends on Task Y being completed first. 

    * Usage: "Describe the steps for building a house using my task dependency language."

    * Usage: "Provide an ordering for the steps: Boil Water [Turn on Stove], Cook Pasta [Boil Water], Make Marinara [Turn on Stove], Turn on Stove [Go Into Kitchen]"


#### Format of the Recipe Pattern
To use this pattern, your prompt should make the following fundamental contextual statements:

* I would like to achieve X 

* I know that I need to perform steps A,B,C 

* Provide a complete sequence of steps for me 

* Fill in any missing steps 

* (Optional) Identify any unnecessary steps

You will need to replace "X" with an appropriate task. You will then need to specify the steps A, B, C that you know need to be part of the recipe / complete plan.

Examples:

* I would like to  purchase a house. I know that I need to perform steps make an offer and close on the house. Provide a complete sequence of steps for me. Fill in any missing steps.

* I would like to drive to NYC from Nashville. I know that I want to go through Asheville, NC on the way and that I don't want to drive more than 300 miles per day. Provide a complete sequence of steps for me. Fill in any missing steps.

#### Format of the Alternative Approaches Pattern
To use this pattern, your prompt should make the following fundamental contextual statements:

* If there are alternative ways to accomplish a task X that I give you, list the best alternate approaches 

* (Optional) compare/contrast the pros and cons of each approach 

* (Optional) include the original way that I asked 

* (Optional) prompt me for which approach I would like to use

You will need to replace "X" with an appropriate task.

Examples:

* For every prompt I give you, If there are alternative ways to word a prompt hat I give you, list the best alternate wordings . Compare/contrast the pros and cons of each wording. 

* For anything that I ask you to write, determine the underlying problem that I am trying to solve and how I am trying to solve it. List at least one alternative approach to solve the problem and compare / contrast the approach with the original approach implied by my request to you.

Patterns reference: https://www.coursera.org/learn/prompt-engineering/