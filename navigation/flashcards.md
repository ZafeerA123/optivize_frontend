---
layout: base
title: Inventory Management
description: Flashcards
hide: true
permalink: /InventoryManagement
---


# Welcome to The Inventory Management Page !


<style>
  body {
    font-family: 'Inter', sans-serif;
    background: linear-gradient(135deg, #1e3c72, #2a5298);
    color: #ffffff;
    margin: 0;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
}

h1 {
    color: #ff7043;
    margin-bottom: 20px;
}

.container {
    margin-top: 80px;
    max-width: 900px;
    width: 100%;
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    border-radius: 20px;
    padding: 30px;
    box-shadow: 0 8px 32px rgba(31, 38, 135, 0.37);
}

.top-container, .bottom-container {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
}

.box {
    flex: 1;
    margin: 0 10px;
    padding: 20px;
    background: rgba(255, 255, 255, 0.2);
    border-radius: 15px;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.box h2 {
    color: #ff7043;
    margin-bottom: 15px;
}

button {
    background: #ff7043;
    color: white;
    border: none;
    border-radius: 8px;
    padding: 10px 16px;
    font-size: 14px;
    cursor: pointer;
    transition: all 0.3s ease;
    font-weight: bold;
    width: 100%;
}

button:hover {
    background: #d97706;
}

.deck-container, .InventoryItem-container {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;
}

.deck, .InventoryItem {
    width: 200px;
    height: 120px;
    border-radius: 10px;
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    background: #f5f5f5;
    color: #ff7043;
    font-size: 18px;
    font-weight: bold;
    transition: all 0.3s ease;
    box-shadow: 0 6px 15px rgba(0, 0, 0, 0.5);
}

.deck:hover, .InventoryItem:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.7);
}

.InventoryItem {
    height: 220px;
}

.InventoryItem-content {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.InventoryItem-content span {
    margin: 5px 0;
}

.hidden {
    display: none;
}
</style>


<div class="container">
  <h1>Inventory Items</h1>
  <div class="top-container">
    <div class="box" id="add-deck-box">
      <h2>Create a New Inventory</h2>
      <button id="create-deck-btn">+ Create Inventory</button>
      <div id="add-deck-form" class="hidden">
        <input type="text" id="deck-title" placeholder="Enter Inventory title" />
      </div>
    </div>
    <div class="box" id="open-deck-box">
      <h2>Your Inventories</h2>
      <div class="deck-container" id="deck-container"></div>
    </div>
  </div>

  <div class="bottom-container hidden" id="deck-interaction">
    <div class="box" id="InventoryItems-box">
      <h2>Inventory Items</h2>
      <div class="InventoryItem-container" id="InventoryItem-container">
        <div class="InventoryItem hidden" id="InventoryItem"></div>
        <button id="next-card-btn" class="hidden">Next Card</button>
        <button id="close-deck-btn" class="hidden">Close Deck</button>
      </div>
    </div>
    <div class="box" id="add-InventoryItem-box">
      <h2>Add a Inventory Item</h2>
      <div id="add-InventoryItem-form" class="hidden">
        <h3 id="current-deck-name">Add Inventory Item to Inventory: <span id="deck-name-placeholder"></span></h3>
        <input type="text" id="question" placeholder="Enter Item Name" />
        <input type="text" id="answer" placeholder="Enter Item Description" />
        <button id="add-card-btn">Add Inventory Item</button>
      </div>
    </div>
  </div>
</div>











<script type="module">
  import { pythonURI, fetchOptions } from '{{site.baseurl}}/assets/js/api/config.js';
  console.log("Python URI:", pythonURI); // Check if it's correctly imported




  const createDeckBtn = document.getElementById('create-deck-btn');
  const addDeckForm = document.getElementById('add-deck-form');
  const deckInfoPhase = document.getElementById('deck-info-phase');
  const questionPhase = document.getElementById('question-phase');
  const deckContainer = document.getElementById('deck-container');
  const InventoryItemContainer = document.getElementById('InventoryItem-container');
  const InventoryItem = document.getElementById('InventoryItem');
  const nextCardBtn = document.getElementById('next-card-btn');
  const closeDeckBtn = document.getElementById('close-deck-btn');


  let decks = []; // Array to store all decks
  let currentDeck = null; // Deck currently being viewed
  let currentCardIndex = 0; // Index of the current card being viewed


  // Show deck creation form
  createDeckBtn.addEventListener('click', () => {
    addDeckForm.classList.remove('hidden');
    deckInfoPhase.classList.remove('hidden');
    questionPhase.classList.add('hidden');
  });



document.getElementById('create-deck-btn').addEventListener('click', async () => {
    const deckTitle = document.getElementById('deck-title').value.trim();
    if (!deckTitle) {
        alert('Please provide an inventory title.');
        return;
    }


    try {
        const response = await fetch(`${pythonURI}/api/deck`, {
            ...fetchOptions,
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            credentials: 'include',
            body: JSON.stringify({ title: deckTitle, user_id: 1 }), // Replace user_id as needed
        });


        if (response.ok) {
            const newDeck = await response.json();
            decks.push(newDeck); // Add the new deck to the local array
            alert(`Deck "${newDeck.title}" created successfully!`);
            document.getElementById('deck-title').value = ''; // Clear the input
            displayDeck(newDeck); // Show the new deck
        } else {
            alert('Failed to create Inventory. Please try again.');
        }
    } catch (error) {
        console.error('Error creating Inventory:', error);
        alert('An error occurred while creating the Inventory.');
    }
});






document.getElementById('add-card-btn').addEventListener('click', async () => {
    const question = document.getElementById('question').value.trim();
    const answer = document.getElementById('answer').value.trim();

    if (!question || !answer) {
        alert('Please provide both a question and an answer.');
        return;
    }

    if (!currentDeck || !currentDeck.id) {
        alert('No deck selected. Please select or create a deck first.');
        return;
    }

    try {
        const response = await fetch(`${pythonURI}/api/flashcard`, {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            credentials: 'include',
            body: JSON.stringify({
                title: question,
                content: answer,
                deck_id: currentDeck.id,
                user_id: 1  // ✅ Ensure this is correct
            }),
        });

        if (!response.ok) throw new Error("Failed to add Inventory Item.");

        const newCard = await response.json();
        currentDeck.cards.push(newCard);
        alert(`Inventory Item added to ${currentDeck.title}!`);
        document.getElementById('question').value = '';
        document.getElementById('answer').value = '';
        displayInventoryItems(currentDeck.cards);
    } catch (error) {
        console.error('Error adding InventoryItem:', error);
        alert('An error occurred while adding the InventoryItem.');
    }
});






function displayInventoryItems(cards) {
    const container = document.getElementById('InventoryItem-container');
    container.innerHTML = ''; // Clear existing InventoryItems

    cards.forEach(card => {
        const cardElement = document.createElement('div');
        cardElement.classList.add('InventoryItem');
        cardElement.innerHTML = `
            <div class="InventoryItem-content">
                <span class="question-text">${card.title}</span>
                <span class="edit-icon" style="cursor: pointer; font-size: 16px; margin-left: 8px;">✏️</span>
                <span class="delete-icon" style="cursor: pointer; font-size: 16px; margin-left: 8px;">❌</span>
            </div>
        `;

        // Ensure the element exists before adding event listeners
        const questionElement = cardElement.querySelector('.question-text');
        if (!questionElement) {
            console.error("InventoryItem question text not found!");
            return;
        }

        // Handle flipping between question and answer
        cardElement.onclick = (event) => {
            if (!event.target.classList.contains("edit-icon") && !event.target.classList.contains("delete-icon")) {
                if (questionElement.textContent === card.title) {
                    questionElement.textContent = card.content;
                    cardElement.classList.add('answer');
                } else {
                    questionElement.textContent = card.title;
                    cardElement.classList.remove('answer');
                }
            }
        };

        // Enable Editing a InventoryItem
        const editIcon = cardElement.querySelector('.edit-icon');
        editIcon.addEventListener('click', () => editInventoryItem(card, cardElement));

        // Enable Deleting a InventoryItem
        const deleteIcon = cardElement.querySelector('.delete-icon');
        deleteIcon.addEventListener('click', async () => {
            const confirmDelete = confirm(`Are you sure you want to delete this InventoryItem?`);
            if (confirmDelete) {
                await deleteInventoryItem(card.id, cardElement);
            }
        });

        container.appendChild(cardElement);
    });

    if (cards.length === 0) {
        container.innerHTML = '<p>No Inventory Items available. Add one to get started!</p>';
    }
}


// Function to Edit InventoryItem
function editInventoryItem(card, cardElement) {
    console.log('Editing InventoryItem:', card);

    const editForm = document.createElement('div');
    editForm.innerHTML = `
        <input type="text" value="${card.title}" class="edit-input" style="width: 90%; padding: 5px; border-radius: 5px;">
        <input type="text" value="${card.content}" class="edit-input" style="width: 90%; padding: 5px; margin-top: 5px; border-radius: 5px;">
        <button class="save-edit-btn" style="margin-top: 5px; padding: 5px 10px; border-radius: 5px;">Save</button>
    `;

    cardElement.innerHTML = ''; // Clear the card content
    cardElement.appendChild(editForm);

    const inputs = editForm.querySelectorAll('.edit-input');
    const saveButton = editForm.querySelector('.save-edit-btn');

    saveButton.addEventListener('click', async () => {
        const updatedTitle = inputs[0].value.trim();
        const updatedContent = inputs[1].value.trim();

        if (!updatedTitle || !updatedContent) {
            alert("Both question and answer are required.");
            return;
        }

        await updateInventoryItem(card.id, updatedTitle, updatedContent, cardElement);
    });
}

async function updateInventoryItem(InventoryItemId, newTitle, newContent, cardElement) {
    try {
        const response = await fetch(`${pythonURI}/api/flashcard/${InventoryItemId}`, {
            method: 'PUT',
            headers: { 
                'Content-Type': 'application/json',
                'Accept': 'application/json'
            },
            credentials: 'include',
            body: JSON.stringify({ title: newTitle, content: newContent }),
        });

        if (!response.ok) throw new Error(`Failed to update Inventory Item: ${response.statusText}`);

        const updatedInventoryItem = await response.json();
        alert(`Inventory Item Name updated successfully!`);

        cardElement.innerHTML = `
            <div class="InventoryItem-content">
                <span class="question-text">${updatedInventoryItem.title}</span>
                <span class="edit-icon" style="cursor: pointer;">✏️</span>
                <span class="delete-icon" style="cursor: pointer;">❌</span>
            </div>
        `;

        cardElement.dataset.answer = updatedInventoryItem.content;

        const questionElement = cardElement.querySelector('.question-text');

        cardElement.onclick = (event) => {
            if (!event.target.classList.contains("edit-icon") && !event.target.classList.contains("delete-icon")) {
                const isQuestion = questionElement.textContent === updatedInventoryItem.title;
                questionElement.textContent = isQuestion ? cardElement.dataset.answer : updatedInventoryItem.title;
                cardElement.classList.toggle('answer', isQuestion);
            }
        };

        cardElement.querySelector('.edit-icon').addEventListener('click', () => editInventoryItem(updatedInventoryItem, cardElement));
        cardElement.querySelector('.delete-icon').addEventListener('click', () => deleteInventoryItem(updatedInventoryItem.id, cardElement));

    } catch (error) {
        console.error('Error updating Inventory Item:', error);
        alert('An error occurred while updating the Inventory Item.');
    }
}




async function deleteInventoryItem(InventoryItemId, cardElement) {
    try {
        const response = await fetch(`${pythonURI}/api/flashcard/${InventoryItemId}`, {
            method: 'DELETE',
            headers: { 'Content-Type': 'application/json' },
            credentials: 'include',
        });

        if (!response.ok) throw new Error(`Failed to delete Inventory Item: ${response.statusText}`);

        alert('Inventory Item deleted successfully!');
        cardElement.remove();
    } catch (error) {
        console.error('Error deleting Inventory Item:', error);
        alert('An error occurred while deleting the Inventory Item.');
    }
}










async function fetchDecks() {
    try {
        const response = await fetch(`${pythonURI}/api/deck`, {
            ...fetchOptions,
            method: 'GET',
            headers: { 'Content-Type': 'application/json' },
            credentials: 'include',
        });


        if (response.ok) {
            const fetchedDecks = await response.json();
            console.log('Fetched decks:', fetchedDecks);


            deckContainer.innerHTML = ''; // Clear container


            fetchedDecks.forEach(deck => {
                displayDeck(deck);
            });
        } else if (response.status === 401) {
            alert('You are not authorized. Please log in.');
            window.location.href = '/optivize_frontend/login';
        } else {
            const error = await response.json();
            console.error('Failed to fetch Inventories:', error);
        }
    } catch (error) {
        console.error('Error fetching Inventories:', error);
    }
}










// Fetch all InventoryItems from the backend
async function fetchInventoryItems() {
    try {

        // Send a GET request to the backend
        const response = await fetch(`${pythonURI}/api/flashcard`, {
            ...fetchOptions,
            method: 'GET',
            headers: {
                'Content-Type': 'application/json',
            },
            credentials: 'include', // Include cookies in the request
        });


        if (response.ok) {
            // Parse the response as JSON
            const InventoryItems = await response.json();
            console.log('Fetched InventoryItems:', InventoryItems);


            // Group InventoryItems by deck title (if applicable) or display as one deck
            const groupedDeck = { title: "Created InventoryItems", cards: [] };
            InventoryItems.forEach((InventoryItem) => {
                groupedDeck.cards.push({
                    question: InventoryItem.title,
                    answer: InventoryItem.content,
                });
            });


            // Display the deck in the deck container
            displayDeck(groupedDeck);
        } else {
            console.error('Failed to fetch Inventory Items:', await response.text());
        }
    } catch (error) {
        console.error('Error fetching Inventory Items:', error);
    }
}


// Create a new deck when "Create Deck" is clicked
createDeckBtn.addEventListener('click', () => {
    addDeckForm.classList.remove('hidden');
    deckInfoPhase.classList.remove('hidden');
    questionPhase.classList.add('hidden');
    currentDeck = null; // Reset the current deck to avoid issues
});





function displayDeck(deck) {
    console.log('Displaying deck:', deck); // Log the deck object for debugging

    const deckElement = document.createElement('div');
    deckElement.classList.add('deck');
    deckElement.innerHTML = `
        <div style="display: flex; align-items: center; gap: 5px;">
            <h3 class="deck-title" style="margin: 0; flex-grow: 1;">${deck.title}</h3>
            <span class="edit-icon" style="cursor: pointer; font-size: 16px;">✏️</span>
        </div>
        <div style="display: flex; gap: 5px; justify-content: center; margin-top: 10px;">
            <button class="open-deck-btn">Open</button>
            <button class="delete-deck-btn">Delete</button>
        </div>
    `;

    const titleElement = deckElement.querySelector('.deck-title');
    const editIcon = deckElement.querySelector('.edit-icon');

    // Enable editing the title when clicking the pencil icon
    editIcon.addEventListener('click', () => {
        const input = document.createElement('input');
        input.type = 'text';
        input.value = deck.title;
        input.classList.add('edit-deck-input');
        input.style.width = "80%";
        input.style.padding = "5px";
        input.style.borderRadius = "5px";
        input.style.border = "1px solid #facc15";
        input.style.background = "rgba(255, 255, 255, 0.1)";
        input.style.color = "white";
        input.style.fontSize = "16px";

        titleElement.replaceWith(input);
        input.focus();

        // Save the new title when input loses focus or on Enter key
        const saveTitle = async () => {
            const newTitle = input.value.trim();
            if (newTitle && newTitle !== deck.title) {
                await editDeckTitle(deck.id, newTitle, input, titleElement);
            } else {
                input.replaceWith(titleElement); // Revert if no change
            }
        };

        input.addEventListener('blur', saveTitle);
        input.addEventListener('keydown', async (event) => {
            if (event.key === 'Enter') {
                await saveTitle();
            }
        });
    });

    // Attach event listener for opening the deck
    deckElement.querySelector('.open-deck-btn').addEventListener('click', () => {
        console.log('Deck clicked:', deck); // Log the deck object on button click
        openDeck(deck);
    });

    // Attach event listener for deleting the deck
    deckElement.querySelector('.delete-deck-btn').addEventListener('click', async () => {
        const confirmDelete = confirm(`Are you sure you want to delete the deck "${deck.title}"?`);
        if (confirmDelete) {
            try {
                const response = await fetch(`${pythonURI}/api/deck/${deck.id}`, {
                    ...fetchOptions,
                    method: 'DELETE',
                    headers: { 'Content-Type': 'application/json' },
                    credentials: 'include',
                });

                if (response.ok) {
                    alert('Inventory deleted successfully!');
                    await fetchDecks(); // Refresh the decks list
                } else {
                    const error = await response.json();
                    alert(`Failed to delete Inventories: ${error.error}`);
                }
            } catch (error) {
                console.error('Error deleting Inventory:', error);
                alert('An error occurred while deleting the Inventory.');
            }
        }
    });

    deckContainer.appendChild(deckElement);
}

async function editDeckTitle(deckId, newTitle, inputElement, titleElement) {
    try {
        const response = await fetch(`${pythonURI}/api/deck/${deckId}`, {
            ...fetchOptions,
            method: 'PUT',
            headers: { 'Content-Type': 'application/json' },
            credentials: 'include',
            body: JSON.stringify({ title: newTitle }), 
        });

        if (response.ok) {
            const updatedDeck = await response.json();
            titleElement.textContent = updatedDeck.title; 
            inputElement.replaceWith(titleElement);
            alert(`Inventory Name updated successfully to: ${updatedDeck.title}`);
        } else {
            const error = await response.json();
            alert(`Error updating Inventory: ${error.error}`);
            inputElement.replaceWith(titleElement);
        }
    } catch (error) {
        console.error('Error updating Inventory Name:', error);
        alert('An error occurred while updating the Inventory.');
        inputElement.replaceWith(titleElement);
    }
}



async function openDeck(deck) {
    console.log('Opening deck:', deck);

    if (!deck.id) {
        alert('Deck ID is missing!');
        return;
    }

    try {
        const response = await fetch(`${pythonURI}/api/deck/${deck.id}`, {
            ...fetchOptions,
            method: 'GET',
            headers: { 'Content-Type': 'application/json' },
        });

        if (response.ok) {
            const detailedDeck = await response.json();
            currentDeck = detailedDeck;
            currentCardIndex = 0;

            document.getElementById('deck-name-placeholder').textContent = currentDeck.title;

            if (currentDeck.cards.length > 0) {
                displayInventoryItems(currentDeck.cards);
            } else {
                document.getElementById('InventoryItem-container').innerHTML = '<p>No Inventory Items yet. Add one!</p>';
            }

            document.getElementById('add-InventoryItem-form').classList.remove('hidden');
            document.getElementById('deck-interaction').classList.remove('hidden');
        } else {
            console.error('Failed to fetch Inventory details:', await response.text());
        }
    } catch (error) {
        console.error('Error fetching Inventory details:', error);
    }
}












function showInventoryItem(card) {
    const InventoryItem = document.getElementById('InventoryItem'); // Re-fetch the InventoryItem element
    if (!InventoryItem) {
        console.error('Inventory Item element not found in the DOM.');
        return;
    }


    console.log('Displaying Inventory Item:', card);


    InventoryItem.textContent = card.title; // Set the question as the default content
    InventoryItem.classList.remove('hidden');
    InventoryItem.classList.remove('answer');


    // Toggle between question and answer
    InventoryItem.onclick = () => {
        if (InventoryItem.textContent === card.title) {
            InventoryItem.textContent = card.content;
            InventoryItem.classList.add('answer');
        } else {
            InventoryItem.textContent = card.title;
            InventoryItem.classList.remove('answer');
        }
    };
}




// Event listener for showing the next card
nextCardBtn.addEventListener('click', () => {
    if (currentDeck.cards.length > 0) {
        currentCardIndex = (currentCardIndex + 1) % currentDeck.cards.length;
        showInventoryItem(currentDeck.cards[currentCardIndex]);
    }
});


// Event listener for closing the deck
closeDeckBtn.addEventListener('click', () => {
    InventoryItemContainer.classList.add('hidden');
    deckContainer.classList.remove('hidden');
    nextCardBtn.classList.add('hidden');
    closeDeckBtn.classList.add('hidden');
});


// Fetch and display InventoryItems when the page loads
document.addEventListener('DOMContentLoaded', fetchDecks);








  // Close the deck and return to deck view
  closeDeckBtn.addEventListener('click', () => {
    InventoryItemContainer.classList.add('hidden');
    deckContainer.classList.remove('hidden');
    nextCardBtn.classList.add('hidden');
    closeDeckBtn.classList.add('hidden');
  });
</script>




<script>
document.addEventListener('DOMContentLoaded', () => {
  const importForm = document.getElementById('import-form');
  if (!importForm) {
    console.warn('No element with id "import-form" found. Skipping import handler.');
    return;
  }

  importForm.addEventListener('submit', async (event) => {
    event.preventDefault(); // Prevent form from reloading the page

    const amount = document.getElementById('amount')?.value || 10;
    const category = document.getElementById('category')?.value;

    let apiUrl = `${pythonURI}/api/import-flashcards?amount=${amount}&difficulty=medium`;
    if (category) {
      apiUrl += `&category=${category}`;
    }

    try {
      const response = await fetch(apiUrl, {
        ...fetchOptions,
        method: 'GET',
        headers: { 'Content-Type': 'application/json' },
      });

      if (response.ok) {
        const data = await response.json();
        alert(`Successfully imported ${data.InventoryItems.length} Inventory Items!`);
        await fetchDecks(); // Refresh deck list after import
      } else {
        const error = await response.json();
        alert(`Error: ${error.error}`);
      }
    } catch (error) {
      console.error("Error importing Inventory Items:", error);
      alert("An error occurred while importing Inventory Items.");
    }
  });
});
</script>
