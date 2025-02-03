# chatbot_sassy
Initializing a ConversationManager object in Streamlit's Session State 

Adding the ConversationManager class
For the first task, let's integrate the ConversationManager class. This class makes up the logic of our chatbot's backend. It handles the API interactions, token counting, conversation history management, and system message updates. Make sure you have the class definition and all necessary imports in your main code editor.

Because Streamlit is designed to integrate with existing code, we can use the ConversationManager class without any modifications. You're encouraged to use your version of the ConversationManager class you created in the previous project, or you can use our provided exemplar. If you choose to use your version, ensure you have the following methods in this class so that you can follow along with all of the steps of this guided project:

__init__: Sets up the chatbot environment.
set_persona: Adjusts the chatbot's personality.
set_custom_system_message: Allows users to set a custom system message.
chat_completion: Generates responses based on user input.
reset_conversation_history: Clears chat history.

Initializing a ConversationManager object in Streamlit's Session State
Let's get your Streamlit app ready to interact with the ConversationManager class. Streamlit’s session_state is used to persist information between user interactions. This concept is critical for our chatbot since we want to keep track of the conversation as the user interacts with the app. If you incorrectly initialize the session state (or forget to do it altogether), you'll see an error or only see one message at a time in the chat interface.

Understanding Streamlit's Session State for Chatbot Functionality
Using Streamlit’s session_state is integral to building our chatbot app. It’s like our app's memory, crucial for holding onto the conversation's thread as users interact. Without it, the chatbot would forget previous interactions after each new message, leading to a disjointed experience. By correctly initializing and managing the session_state, we ensure a smooth, continuous conversation flow, making our chatbot seem more intelligent and responsive. This step is not just about avoiding errors; it's about enhancing the user experience by maintaining a coherent dialogue history.

Creating the Layout
As we begin creating the Streamlit interface for the chatbot app, we want to consider what elements are important to include. We can add many elements and widgets to the app, but we also want to be aware of UI design principles and not overcrowd the page. Including too many options can overwhelm users and lead to a less enjoyable app!

With this in mind, we recommend creating widgets in a sidebar that do the following:

A slider to adjust the conversation temperature.
A slider to set the maximum number of tokens allowed per message.
A slider to set the total maximum number of tokens allowed in the conversation history.
A select box to select a chatbot persona.
A button to reset the chat history. We recommend using the on_click parameter combined with the ConversationManager object's reset_conversation_history method.

Chat history and elements
The message interface is the final thing we need to create an effective chatbot app. Luckily, Streamlit has two dedicated chat elements: chat_message and chat_input. Because these will make up the heart of the app, we should locate them in the main section of the app (and as of Streamlit version 1.29.0, the chat_input element can only be added to the main section of the app, which makes our choice more straightforward).

To make the chat interface function, we will need to add four things to our code:

A conversation history session state variable.
A user input variable that collects user input from the chat_input element.
The chat_completion method from our ConversationManager object.
This step is where the pieces all come together because you can fill in the chat_completion parameters with the widget values from the sidebar.

Step 1: Add the ConversationManager class and import all necessary libraries
Copy your ConversationManager class (and all necessary import statements) into the main code editor. You can use your own code or download the code provided in the code editor tab labeled "ConversationManager_Exemplar.py". Once you click on the tab, a "Download" icon should appear next to the file name.

Import streamlit at the top of your code.

Step 2: Title Your Streamlit App
Add a title for your chatbot.

Run and Deploy your app to ensure the ConversationManager class and the Streamlit library work as expected.

Step 3: Intialize Session State and Chat Manager
Use conditional logic to check if a key exists in the session state to prevent reinitialization.

Within the conditional logic, initialize an instance of the ConversationManager in Streamlit's session_state.

Assign the initialized session state variable to a dedicated variable (i.e., x = st.session_state['x']).

Step 4: Create Sidebar Widgets
In the app's sidebar:

Add sliders for token budget and chat temperature. Each interactive widget should have its own variable name so you can use the values in other app areas.

Create a selectbox for users to choose different chatbot personalities.

Use conditional logic (if/elif/else) to set the persona depending on the selected chatbot personality. You will need to use the set_persona method of your conversation manager session state variable.

If a user selects the "Custom" persona, use nested conditional logic to display a textbox.

In a nested if statement, create a button for users to click that will call the set_custom_system_message method (this will prevent the app from throwing a ValueError if the textbox is empty).
Step 5: Add Chat Functionality
Use Streamlit's chat input function to capture user inputs. Assign user input to a variable named user_input.

Initialize a session state variable for the conversation history created from the conversation_history attribute of your ConversationManager object.

Check if a user has entered input. If so, call the chat_completion method from your ConversationManager object.

Add your sidebar widget variables as arguments to the chat_completion method to connect the custom token budget, temperature, and persona values.

Step 6: Display Conversation History
Display the conversation history using Streamlit's chat_message function.

Consider how to ensure you only display messages from the user and the assistant but NOT the system message.

Step 7: Add a Reset History Button
Add a button to reset the conversation history in the sidebar. You will need to consider what line to place this code on so that it runs in the correct order with Streamlit's refresh logic.
