import React, { useState, useEffect } from 'react';

// Define the dialogue data for the NPC.
// Each object represents a dialogue state with an ID, NPC text, and player choices.
// Choices have player text and a nextDialogueId to transition to.
const dialogueData = [
  {
    id: 'start',
    npcName: 'Michael, Boss Man',
    npcText: "Welcome team leads; what shall we discuss today?",
    portraitUrl: "https://ca.slack-edge.com/E01KZRWKX7W-U01U5ED5LAX-20cec3879f72-512", // All portrait URLs updated
    choices: [
      { playerText: "When are we getting a title/compensation change?", nextDialogueId: 'Compensation' },
      { playerText: "Are we to coninue JES work?.", nextDialogueId: 'JES' },
      { playerText: "Please Leave us alone.", nextDialogueId: 'end_dialogue' },
      { playerText: "Lemme go to china king wasabi -White boy", nextDialogueId: 'China' },
    ],
  },
  {
    id: 'Compensation',
    npcName: 'Michael, Frustrated Boss Man',
    npcText: "HaHa Don't you worry, we will get what's coming to us. Who cares about money anyways?",
    portraitUrl: "https://ca.slack-edge.com/E01KZRWKX7W-U01U5ED5LAX-20cec3879f72-512", // All portrait URLs updated
    choices: [
      { playerText: "Youre so right Michael we are content. -Pat", nextDialogueId: 'Thank you' },
      { playerText: "We just gotta be a fly on the wall - Jacob", nextDialogueId: 'Thank you' },
      { playerText: "This smells like some BS, I have 15 kids to provide for -Luis", nextDialogueId: 'JES' },
    ],
  },
  {
    id: 'Thank you',
    npcName: 'Mike I',
    npcText: "Now, I have some big news potentially coming up! I can't say what is is, or if it affects us even remotly.",
    portraitUrl: "https://ca.slack-edge.com/E01KZRWKX7W-U01U5ED5LAX-20cec3879f72-512", // All portrait URLs updated
    choices: [
      { playerText: "As a licesed phycologist I am excited, for any news is good news -Reece .", nextDialogueId: 'end_dialogue' },
      { playerText: "Can we stop doing JES work.", nextDialogueId: 'JES' },
    ],
  },
  {
    id: 'JES',
    npcName: 'Michael, Boss Man',
    npcText: "Everyone at the plant will be doing JES work now, from RJ down to enrique the janitor",
    portraitUrl: "https://ca.slack-edge.com/E01KZRWKX7W-U01U5ED5LAX-20cec3879f72-512", // All portrait URLs updated
    choices: [
      { playerText: "Thats fine, I'm done with R3 JES's already -Grace", nextDialogueId: 'end_dialogue' },
      { playerText: "It'll be my honor Sire! Although I don't have any done currently -Pat.", nextDialogueId: 'end_dialogue' },
    ],
  },
  {
    id: 'China',
    npcName: 'King Wasabi Mike',
    npcText: "We can't go to China, I can't trust you and you don't even know the language.",
    portraitUrl: "https://ca.slack-edge.com/E01KZRWKX7W-U01U5ED5LAX-20cec3879f72-512", // All portrait URLs updated
    choices: [
      { playerText: "我有护照，而且那个女人可能真的对我很好.", nextDialogueId: 'end_dialogue' },
    ],
  },
  {
    id: 'end_dialogue',
    npcName: 'Confused group Leader',
    npcText: "Until we meet again, please look busy rewatching virtual builds 200 times",
    portraitUrl: "https://ca.slack-edge.com/E01KZRWKX7W-U01U5ED5LAX-20cec3879f72-512", // All portrait URLs updated
    choices: [], // No choices, indicates end of conversation path
  },
];

function App() {
  // State to hold the current dialogue node
  const [currentDialogue, setCurrentDialogue] = useState(
    dialogueData.find((d) => d.id === 'start')
  );

  // State to manage loading indicator for potential LLM calls
  const [isLoading, setIsLoading] = useState(false);

  // Function to handle player choice selection
  const handlePlayerChoice = async (nextDialogueId) => {
    // Find the next dialogue node based on the selected choice's ID
    const nextNode = dialogueData.find((d) => d.id === nextDialogueId);

    if (nextNode) {
      setCurrentDialogue(nextNode);

      // --- LLM Integration Placeholder (Future Enhancement) ---
      // If you wanted to dynamically generate NPC responses using an LLM,
      // you would make an API call here.
      // Example of how you might integrate an LLM call:
      /*
      if (nextNode.id === 'dynamic_response_point') { // Example: A specific node triggers LLM
        setIsLoading(true);
        try {
          const prompt = `Player said: "${currentDialogue.choices.find(c => c.nextDialogueId === nextDialogueId).playerText}". NPC previously said: "${currentDialogue.npcText}". Generate a suitable D&D NPC response.`;
          let chatHistory = [];
          chatHistory.push({ role: "user", parts: [{ text: prompt }] });
          const payload = { contents: chatHistory };
          const apiKey = ""; // Canvas will provide this at runtime
          const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

          const response = await fetch(apiUrl, {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(payload)
          });
          const result = await response.json();

          if (result.candidates && result.candidates.length > 0 &&
              result.candidates[0].content && result.candidates[0].content.parts &&
              result.candidates[0].content.parts.length > 0) {
            const llmResponse = result.candidates[0].content.parts[0].text;
            setCurrentDialogue(prev => ({ ...prev, npcText: llmResponse }));
          } else {
            console.error("LLM response structure unexpected:", result);
            setCurrentDialogue(prev => ({ ...prev, npcText: "I'm sorry, I seem to be having trouble finding the right words." }));
          }
        } catch (error) {
          console.error("Error calling LLM:", error);
          setCurrentDialogue(prev => ({ ...prev, npcText: "I'm sorry, I'm unable to respond at the moment." }));
        } finally {
          setIsLoading(false);
        }
      }
      */
      // --- End LLM Integration Placeholder ---
    }
  };

  // Function to restart the conversation
  const restartConversation = () => {
    setCurrentDialogue(dialogueData.find((d) => d.id === 'start'));
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-gray-900 to-gray-700 flex items-center justify-center p-4 font-inter text-gray-100">
      <div className="w-full max-w-2xl bg-gray-800 rounded-xl shadow-2xl p-6 md:p-8 border border-gray-700">
        <h1 className="text-3xl md:text-4xl font-bold text-center mb-6 text-yellow-400">
          Launch Weekly Recap
        </h1>

        {currentDialogue && (
          <div className="space-y-6">
            {/* NPC Section */}
            <div className="bg-gray-700 p-5 rounded-lg shadow-inner border border-gray-600 flex items-start space-x-4">
              {currentDialogue.portraitUrl && (
                <img
                  src={currentDialogue.portraitUrl}
                  alt={`${currentDialogue.npcName} portrait`}
                  className="w-24 h-24 rounded-full border-2 border-gray-500 flex-shrink-0 object-cover"
                  // Fallback for image loading errors
                  onError={(e) => { e.target.onerror = null; e.target.src="https://placehold.co/100x100/FF0000/FFFFFF?text=Error"; }}
                />
              )}
              <div>
                <p className="text-sm text-gray-400 mb-2 font-semibold">{currentDialogue.npcName}</p>
                {isLoading ? (
                  <p className="text-lg italic text-gray-300 animate-pulse">
                    Thinking...
                  </p>
                ) : (
                  <p className="text-lg text-gray-200 leading-relaxed">
                    "{currentDialogue.npcText}"
                  </p>
                )}
              </div>
            </div>

            {/* Player Choices Section */}
            <div className="space-y-3">
              {currentDialogue.choices.length > 0 ? (
                currentDialogue.choices.map((choice, index) => (
                  <button
                    key={index}
                    onClick={() => handlePlayerChoice(choice.nextDialogueId)}
                    className="w-full text-left bg-blue-700 hover:bg-blue-600 active:bg-blue-800 text-white font-semibold py-3 px-5 rounded-md shadow-md transition duration-200 ease-in-out transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-opacity-75 border border-blue-800"
                  >
                    {choice.playerText}
                  </button>
                ))
              ) : (
                <div className="text-center py-4">
                  <p className="text-gray-400 italic mb-4">
                    The conversation has ended.
                  </p>
                  <button
                    onClick={restartConversation}
                    className="bg-green-600 hover:bg-green-500 active:bg-green-700 text-white font-semibold py-2 px-4 rounded-md shadow-md transition duration-200 ease-in-out transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-opacity-75 border border-green-700"
                  >
                    Start Over
                  </button>
                </div>
              )}
            </div>
          </div>
        )}
      </div>
    </div>
  );
}

export default App;
