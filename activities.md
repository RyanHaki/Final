<head>
    <meta charset="utf-8">  
    <title>Food Memory Game</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap');
        *{
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }
        p{
            font-size: 20px;
        }
        body{
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            background: #6563ff;
        }
        ::selection{
            color: #fff;
            background: #6563ff;
        }
        .wrapper{
            padding: 25px;
            background: #f8f8f8;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }
        .cards, .card, .view, .details, p{
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .cards{
            height: 350px;
            width: 350px;
            flex-wrap: wrap;
            justify-content: space-between;
        }
        .cards .card{
            cursor: pointer;
            position: relative;
            perspective: 1000px;
            transform-style: preserve-3d;
            height: calc(100% / 4 - 10px);
            width: calc(100% / 4 - 10px);
        }
        .card.shake{
            animation: shake 0.35s ease-in-out;
        }
            @keyframes shake {
                0%, 100%{
                    transform: translateX(0);
                }
                20%{
                    transform: translateX(-13px);
                }
                40%{
                    transform: translateX(13px);
                }
                60%{
                    transform: translateX(-8px);
                }
                80%{
                    transform: translateX(8px);
                }
            }
        .cards .card .view{
            width: 100%;
            height: 100%;
            user-select: none;
            pointer-events: none;
            position: absolute;
            background: #fff;
            border-radius: 7px;
            backface-visibility: hidden;
            transition: transform 0.25s linear;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
        }
        .card .front-view img{
            max-width: 17px;
        }
        .card .back-view{
            transform: rotateY(-180deg);
        }
        .card .back-view img{
            max-width: 40px;
        }
        .card.flip .front-view{
            transform: rotateY(180deg);
        }
        .card.flip .back-view{
            transform: rotateY(0);
        }
        .details{
            width: 100%;
            margin-top: 15px;
            padding: 0 20px;
            border-radius: 7px;
            background: #fff;
            height: calc(100% / 4 - 30px);
            justify-content: space-between;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
        }
        .details p{
            font-size: 18px;
            height: 17px;
            padding-right: 18px;
            border-right: 1px solid #ccc;
        }
        .details p span{
            margin-left: 8px;
        }
        .details p b{
            font-weight: 500;
        }
        .details button{
            cursor: pointer;
            font-size: 14px;
            color: #6563ff;
            border-radius: 4px;
            padding: 4px 11px;
            background: #fff;
            border: 2px solid #6563ff;
            transition: 0.3s ease;
        }
        .details button:hover{
            color: #fff;
            background: #6563ff;
        }
        @media screen and (max-width: 700px) {
            .cards{
                height: 350px;
                width: 350px;
            }
            .card .front-view img{
                max-width: 16px;
            }
            .card .back-view img{
                max-width: 40px;
            }
        }
        @media screen and (max-width: 530px) {
            .cards{
                height: 300px;
                width: 300px;
            }
            .card .back-view img{
                max-width: 35px;
            }
            .details{
                margin-top: 10px;
                padding: 0 15px;
                height: calc(100% / 4 - 20px);
            }
            .details p{
                height: 15px;
                font-size: 17px;
                padding-right: 13px;
            }
            .details button{
                font-size: 13px;
                padding: 5px 10px;
                border: none;
                color: #fff;
                background: #6563ff;
            }
        }
    </style>
</head>
<body>
    <div class="wrapper">
        <ul class="cards">
        <li class="card">
            <div class="view front-view">
            <img src="images/que_icon.svg" alt="icon">
            </div>
            <div class="view back-view">
            <img src="images/img-1.png" alt="card-img">
            </div>
        </li>
        <li class="card">
            <div class="view front-view">
            <img src="images/que_icon.svg" alt="icon">
            </div>
            <div class="view back-view">
            <img src="images/img-2.png" alt="card-img">
            </div>
        </li>
        <li class="card">
            <div class="view front-view">
            <img src="images/que_icon.svg" alt="icon">
            </div>
            <div class="view back-view">
            <img src="images/img-3.png" alt="card-img">
            </div>
        </li>
        <li class="card">
            <div class="view front-view">
            <img src="images/que_icon.svg" alt="icon">
            </div>
            <div class="view back-view">
            <img src="images/img-4.png" alt="card-img">
            </div>
        </li>
        <li class="card">
            <div class="view front-view">
            <img src="images/que_icon.svg" alt="icon">
            </div>
            <div class="view back-view">
            <img src="images/img-5.png" alt="card-img">
            </div>
        </li>
        <li class="card">
            <div class="view front-view">
            <img src="images/que_icon.svg" alt="icon">
            </div>
            <div class="view back-view">
            <img src="images/img-6.png" alt="card-img">
            </div>
        </li>
        <li class="card">
            <div class="view front-view">
            <img src="images/que_icon.svg" alt="icon">
            </div>
            <div class="view back-view">
            <img src="images/img-5.png" alt="card-img">
            </div>
        </li>
        <li class="card">
            <div class="view front-view">
            <img src="images/que_icon.svg" alt="icon">
            </div>
            <div class="view back-view">
            <img src="images/img-6.png" alt="card-img">
            </div>
        </li>
        <li class="card">
            <div class="view front-view">
            <img src="images/que_icon.svg" alt="icon">
            </div>
            <div class="view back-view">
            <img src="images/img-1.png" alt="card-img">
            </div>
        </li>
        <li class="card">
            <div class="view front-view">
            <img src="images/que_icon.svg" alt="icon">
            </div>
            <div class="view back-view">
            <img src="images/img-2.png" alt="card-img">
            </div>
        </li>
        <li class="card">
            <div class="view front-view">
            <img src="images/que_icon.svg" alt="icon">
            </div>
            <div class="view back-view">
            <img src="images/img-3.png" alt="card-img">
            </div>
        </li>
        <li class="card">
            <div class="view front-view">
            <img src="images/que_icon.svg" alt="icon">
            </div>
            <div class="view back-view">
            <img src="images/img-4.png" alt="card-img">
            </div>
        </li>
        <div class="details">
            <p class="time">Time: <span><b>20</b>s</span></p>
            <p class="flips">Flips: <span><b>0</b></span></p>
            <button>Refresh</button>
        </div>
        </ul>
    </div>
</body>

<script>
    const cards = document.querySelectorAll(".card"),
    timeTag = document.querySelector(".time b"),
    flipsTag = document.querySelector(".flips b"),
    refreshBtn = document.querySelector(".details button");

    let timePast = 0;
    let flips = 0;
    let matchedCard = 0;
    let disableDeck = false;
    let isPlaying = false;
    let cardOne, cardTwo, timer;
    let good = [
        "almond", "apple", "avocado", "banana", "beans", "blueberry", 
        "broccoli", "brusprouts", "carrot", "celery", "chickbreast", "cucumber",
        "eggs", "kiwi", "lettuce", "mushroom", "orange", "salmon",
        "spinach", "strawberry", "thethingyoudadlefttoget", "tomato", "walnut", "wholegrainbread"
    ];
    let bad = [
        "bacon","burger", "chicknug", "chips", "donut", "fries",
        "hotdog", "icecream", "pizza", "popcorn", "soda", "whitebread"
    ];

    function initTimer(){
        timePast+=0.01;
        timeTag.innerText = timePast.toFixed(2);
    }

    function flipCard({target: clickedCard}){
        if(!isPlaying) {
            isPlaying = true;
            timer = setInterval(initTimer, 10);
        }
        if(clickedCard !== cardOne && !disableDeck){
            flips++;
            flipsTag.innerText = flips;
            clickedCard.classList.add("flip");
            if(!cardOne) {
                return cardOne = clickedCard;
            }
            cardTwo = clickedCard;
            disableDeck = true;
            let cardOneImg = cardOne.querySelector(".back-view img").src,
            cardTwoImg = cardTwo.querySelector(".back-view img").src;
            matchCards(cardOneImg, cardTwoImg);
        }
    }

    function matchCards(img1, img2) {
        alert(img1.slice(56,-4));
        if(img1 === img2){
            if (bad.includes(img1.slice(56,-4))){
                timePast+=5;
            } else {
                matchedCard++;
                if(matchedCard == 4){
                    return clearInterval(timer);
                }
            }
            cardOne.removeEventListener("click", flipCard);
            cardTwo.removeEventListener("click", flipCard);
            cardOne = cardTwo = "";
            return disableDeck = false;
        }
        setTimeout(() => {
            cardOne.classList.add("shake");
            cardTwo.classList.add("shake");
        }, 0);
        setTimeout(() => {
            cardOne.classList.remove("shake", "flip");
            //cardTwo.classList.remove("shake", "flip");
            cardOne = cardTwo;
            cardTwo = "";
            disableDeck = false;
        }, 200);
    }

    function shuffleCard() {
        timePast = 0;
        flips = matchedCard = 0;
        cardOne = cardTwo = "";
        clearInterval(timer);
        timeTag.innerText = timePast.toFixed(2);
        flipsTag.innerText = flips;
        disableDeck = isPlaying = false;
        good.sort(() => Math.random() > 0.5 ? 1 : -1);
        bad.sort(() => Math.random() > 0.5 ? 1 : -1);
        let arr = good.slice(0,3).concat(bad.slice(0,1));
        arr = arr.concat(arr);
        arr.sort(() => Math.random() > 0.5 ? 1 : -1);
        cards.forEach((card, index) => {
            card.classList.remove("flip");
            let imgTag = card.querySelector(".back-view img");
            setTimeout(() => {
                imgTag.src = `images/img-${arr[index]}.png`;
            }, 500);
            card.addEventListener("click", flipCard);
        });
    }

    shuffleCard();

    refreshBtn.addEventListener("click", shuffleCard);

    cards.forEach(card => {
        card.addEventListener("click", flipCard);
    });
</script>