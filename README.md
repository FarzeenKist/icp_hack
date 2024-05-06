Starting the application
git clone https://github.com/ogola5/icp_hack
# requirements
`dfx --version 16 and above`
`rustup within your system`

dfx start --background
dfx deply
# Description
This code implements a basic assistant service using the Azle framework. The service provides functionality for users to interact with an AI assistant and manage conversation threads.

# Key Functionalities:

`Save User Conversation:` Users can interact with the assistant by providing input text. The service stores the user's input and a placeholder AI response in a conversation thread.
Retrieve Conversation Thread: Users can retrieve their conversation history with the assistant using their user ID.
`Delete Conversation Thread`: Users can delete their conversation thread with the assistant.
`Check for Existing Thread:` Users can check if they have a saved conversation thread with the assistant.
# Current Limitations:

The AI response is currently a placeholder and needs to be integrated with an actual AI model.
`getAssistant(assistantId: string)`: Retrieves the ID of an AI assistant, confirming the presence of an assistant in the system.
saveThread(userIdentity: string, userInput: string): Saves or updates a conversation thread based on user input. It automatically generates an AI response as a placeholder.
`getThread(userIdentity: string)`: Fetches an existing conversation thread for a user, if available.
`deleteThread(userIdentity: string)`: Removes a conversation thread associated with a user from the system.
`hasASavedThread(userIdentity: string)`: Checks whether there is an existing conversation thread for a user.
Data Models
`Thread`: Represents a conversation thread containing multiple entries of user interactions.
`ConversationEntryType`: Captures individual entries in a conversation, storing user input and the corresponding AI response.

# Azle framework
StableBTreeMap (for persistent thread storage)
Understanding the Code:

# Imports:

The code imports necessary functions and data types from the Azle framework (update, text, Ok, Err, Result, etc.) and custom models (ErrorResponse, ThreadType, Thread, ConversationEntryType).
Thread Storage:

`A StableBTreeMap data structure (threadStorage) is created to persistently store conversation threads. It uses user IDs (text) as keys and conversation thread objects (Thread) as values. The capacity is set to 4 (adjustable for performance optimization).`
`Assistant Class:`

The Assistant class defines methods for interacting with the service:

getAssistant(assistantId: string) (placeholder): Currently a placeholder for retrieving assistant details.

`saveThread(userIdentity:` string, userInput: string): Saves a new conversation thread or updates an existing one:

`Validates if userIdentity and userInput are not empty.`
Creates a placeholder AI response for userInput.
Constructs a new conversation entry object with userInput and aiResponse.
Retrieves the existing thread for userIdentity from threadStorage.
If no thread exists, a new thread is created with userIdentity, "Chat Thread" object type, current timestamp, and the new conversation entry.
If a thread exists, the new conversation entry is appended to its conversation array.
Updates threadStorage with the modified or new thread.
Returns the updated thread object upon success.
getThread(userIdentity: string): Retrieves a conversation thread:

# Validates if userIdentity is not empty.
Retrieves the thread for userIdentity from threadStorage.
If no thread exists, returns an error message.
If a thread exists, returns the thread object.
`deleteThread(userIdentity: string):` Deletes a conversation thread:

Validates if userIdentity is not empty.
Retrieves the thread for userIdentity from threadStorage.
If no thread exists, returns an error message.
If a thread exists, removes it from threadStorage.
Returns a success message ("Deleted") upon deletion.
hasASavedThread(userIdentity: string): Checks if a conversation thread exists:

`Retrieves the thread for userIdentity from threadStorage.`
Returns true if a thread exists, false otherwise.
Creating an Assistant Instance:

An instance of the Assistant class (assistant) is created.
`Exporting the Assistant:`

The assistant object is exported, allowing other parts of your application to use its functionalities.
Usage (Example):