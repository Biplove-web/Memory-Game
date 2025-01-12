const cards = [
  { id: 1, value: 'A' }, { id: 2, value: 'B' }, { id: 3, value: 'C' },
  { id: 4, value: 'D' }, { id: 5, value: 'E' }, { id: 6, value: 'F' },
  { id: 7, value: 'A' }, { id: 8, value: 'B' }, { id: 9, value: 'C' },
  { id: 10, value: 'D' }, { id: 11, value: 'E' }, { id: 12, value: 'F' }
];
let flippedCards = [];
let matchedPairs = 0;
let timer;
let timeLeft = 30;

function shuffleCards() {
  return cards.sort(() => Math.random() - 0.5);
}

function createBoard() {
  const gameBoard = document.getElementById('gameBoard');
  const shuffledCards = shuffleCards();
  gameBoard.innerHTML = ''; // Clear any previous board

  shuffledCards.forEach((card, index) => {
    const cardElement = document.createElement('div');
    cardElement.classList.add('card');
    cardElement.dataset.id = index;
    cardElement.dataset.value = card.value;

    const front = document.createElement('div');
    front.classList.add('front');
    front.textContent = '?'; // Show the question mark initially

    const back = document.createElement('div');
    back.classList.add('back');
    back.textContent = card.value; // Show the card value when flipped

    cardElement.appendChild(front);
    cardElement.appendChild(back);

    cardElement.addEventListener('click', () => flipCard(cardElement));

    gameBoard.appendChild(cardElement);
  });

  startTimer();
}

function flipCard(cardElement) {
  if (cardElement.classList.contains('flipped') || flippedCards.length === 2) return;

  cardElement.classList.add('flipped');
  flippedCards.push(cardElement);

  if (flippedCards.length === 2) {
    checkMatch();
  }
}

function checkMatch() {
  const [card1, card2] = flippedCards;

  if (card1.dataset.value === card2.dataset.value) {
    matchedPairs++;
    flippedCards = [];
    if (matchedPairs === cards.length / 2) {
      showWinPopup();
      clearInterval(timer);
    }
  } else {
    setTimeout(() => {
      card1.classList.remove('flipped');
      card2.classList.remove('flipped');
      flippedCards = [];
    }, 1000);
  }
}

function startTimer() {
  timer = setInterval(() => {
    if (timeLeft <= 0) {
      clearInterval(timer);
      showTimeUpPopup();
    } else {
      document.getElementById('timeLeft').textContent = timeLeft;
      timeLeft--;
    }
  }, 1000);
}

function showWinPopup() {
  const winPopup = document.getElementById('winPopup');
  winPopup.style.display = 'flex';
}

function showTimeUpPopup() {
  const timeUpPopup = document.getElementById('timeUpPopup');
  timeUpPopup.style.display = 'flex';
}

function resetGame() {
  timeLeft = 30;
  matchedPairs = 0;
  flippedCards = [];
  document.getElementById('startBtn').style.display = 'block';
  document.getElementById('timer').style.display = 'none';
  document.getElementById('resetBtn').style.display = 'none';
  document.getElementById('gameBoard').innerHTML = '';
  document.getElementById('winPopup').style.display = 'none';
  document.getElementById('timeUpPopup').style.display = 'none';
}

document.getElementById('startBtn').addEventListener('click', () => {
  document.getElementById('startBtn').style.display = 'none';
  document.getElementById('timer').style.display = 'block';
  document.getElementById('resetBtn').style.display = 'block';
  createBoard();
});

document.getElementById('resetBtn').addEventListener('click', resetGame);

document.getElementById('closePopupBtn').addEventListener('click', () => {
  document.getElementById('winPopup').style.display = 'none';
  resetGame();
});

document.getElementById('closeTimeUpBtn').addEventListener('click', () => {
  document.getElementById('timeUpPopup').style.display = 'none';
  resetGame();
});
