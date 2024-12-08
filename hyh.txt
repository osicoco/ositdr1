// Juego de las emociones
document.getElementById('gameButton').addEventListener('click', function() {
    alert('¡Juguemos a adivinar emociones! Se te presentarán situaciones y tendrás que identificar cómo te sentirías.');
});

// Quizz
let questions = [
    {
        question: "¿Qué es la inocencia infantil?",
        options: ["Desarrollo emocional", "Falta de conocimiento", "Ambas"],
        answer: "Ambas"
    },
    {
        question: "¿A qué edad los niños empiezan a perder parte de su inocencia?",
        options: ["3 años", "6 años", "12 años"],
        answer: "6 años"
    },
    {
        question: "¿Cuál es una forma efectiva de acompañar a un niño durante este proceso?",
        options: ["Ignorar sus preguntas", "Escuchar sus sentimientos", "Dejar que lo maneje solo"],
        answer: "Escuchar sus sentimientos"
    }
];

function startQuiz() {
    let quizHTML = "<h3>Responde las siguientes preguntas:</h3>";
    questions.forEach((q, index) => {
        quizHTML += `
        <p>${q.question}</p>
        <ul>
            ${q.options.map(option => `<li><input type="radio" name="q${index}" value="${option}">${option}</li>`).join('')}
        </ul>
        `;
    });
    quizHTML += `<button onclick="checkAnswers()">Enviar respuestas</button>`;
    document.getElementById('quizz').innerHTML = quizHTML;
}

function checkAnswers() {
    let score = 0;
    questions.forEach((q, index) => {
        let selected = document.querySelector(`input[name="q${index}"]:checked`);
        if (selected && selected.value === q.answer) {
            score++;
        }
    });
    alert(`Tu puntaje es ${score} de ${questions.length}`);
}
