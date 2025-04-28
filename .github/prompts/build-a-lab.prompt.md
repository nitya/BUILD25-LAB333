# Build a Workshop on Reasoning Models for Azure Application

1. Check if the docs/ folder exists in the repo. If not, create it.
1. Create a structured set of folders under docs/ for the workshop content.
1. Don't delete any existing files or folders in the docs/ folder.
1. Each created subfolder should represent a section of the workshop.
1. Subfolders should be named xx-<section-name> where xx is the section number and section-name is 2 words
1. Each subfolder should contain an index.md file with a short paragraph describing the section.
1. Each subfolder should files numbered 01.md, 02.md, etc. for each page in the section.
1. Each page should contain a 2-3 word title and a short paragraph describing the content.
1. Each page can then have one or more sections for content and exercises.
1. The index.md file should contain a table of contents for the section.
1. Each page should have frontmatter with the title and description.

---

Scaffold the workshop content for a technical audience using clear and concise language.
For each tutorial page, create alternate content and exercise sections to teach a concept and apply it.
Use technical language and examples that are relevant to a developer audience.
Provide clear instructions and concise explanations for each exercise.

Tell this story:

1. Introduction to Reasoning Models
    - What are reasoning models?
    - How do they work?
    - When should we use them?
    - When should we not use them?
    - Mention we are using o1, o3-mini, and gpt-4o-mini models - and write a short description of each
    - Summary: What are 3 takeways from this section?

2. Getting Started With Reasoning Models
    - Visit The Azure AI Foundry playground
    - Verify it has o1, o3-mini, and gpt-4o-mini models deployed
    - Exercise 1: Try a simple question as prompt for each model - compare results
    - Exercise 2: Try a logic problem as prompt for each model - compare results
    - Exercise 3: Try switching reasoning level (low, medium, high) for `o` models - observe results
    - Summary: What are 3 takeways from this section?

    In this section, make sure that prompts are placed in codefenced blocks to support copy/paste.
    For each exercise create a blank codefenced block for the user to fill in with the response they observed.
    Some insights we want to capture are how reasoning models differ from gpt in cost, latency and complexity.
    And how the two o models differ in their reasoning capabilities and cost given their generational differences.

3. Explore Reasoning Models Code-First

    - Launch GitHub Codespaces and authenticate with Azure
    - Copy the .env.sample file to .env and fill in the values
    - Now, open jupyter notebooks in order, and run them to understand the concepts
    - All jupyter notebooks should be created in the `notebooks` folder
    - Each notebook should have a title in the form XX-description.ipynb - where XX is the exercise number
    - Each notebook should alternate between Markdown explainers and Python code cells

    - Exerise 1: Getting Started 
        - Use the Azure AI model inference library to call each named model 
        - Create the client - then define a function that calls a given model with a given prompt
        - Have that function Pretty print the response to show various token counts and response time
        - Run the function for each of the 3 models with a "QA" prompt (bad for reasoning models)
        - Run the function for each of the 3 models with a "Logic" prompt (good for reasoning models)

    - Exercise 2: Reasoning Scenarios
        - Setup the same function as above
        - Identify 4 example domains (with prompts) where reasoning models are useful
        - Identify 4 example domains (with prompts) where reasoning models are not useful
        - For each of the 8 scenarios, run the function and capture the results
        - For each of the 8 scenarios, capture the token counts and response time
        - For each of the 8 scenarios, capture the model response
        - For each of the 8 scenarios, capture the model reasoning level (low, medium, high)

1. Build a Reasoning Model Application - apply prompt engineering best practices to a complex scenario

    In this section, we want to build a complex catering application that, given a set of recipes, and a set of catering orders, will generate a catering plan that covers ingredient purchase, recipe adjustments (for servings), and timing requirements.

    Talk about how we can use the reasoning models to help us with this task.
    - Explain metaprompting 
    - Explain orchestration (where reasoning model plans and gpt model executes)


---