<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css"
        integrity="sha512-z3gLpd7yknf1YoNbCzqRKc4qyor8gaKU1qmn+CShxbuBusANI9QpRohGBreCFkKxLhei6S9CQXFEbbKuqLg0DA=="
        crossorigin="anonymous" referrerpolicy="no-referrer" />
    <title>Temprature Converter</title>
    <link rel="stylesheet" href="style.css">
</head>

<body>
    <div class="container">
        <div class="title">
            <h1>Temprature Converter</h1>
            <span class="Temprature-icon"><i class="fa-solid fa-temperature-high"></i></span>
        </div>
        <div id="celcius">
            <input type="number" name="" placeholder="Celcius">
            <span class="icon">&#8451</span>
        </div>
        <div id="Fahrenheit">
            <input type="number" name="" placeholder="Fahrenheit">
            <span class="icon">&#8457</span>
        </div>
        <div id="Kelvin">
            <input type="number" name="" placeholder="Kelvin">
            <span class="icon">&#8490</span>
        </div>
        <div class="button">
            <button>All Clear</button>
        </div>
    </div>

    <script src="script.js"></script>

</body>
</html>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background-image: linear-gradient(skyblue, rgba(248, 223, 227));
     background-size: cover;
}

.container {
    max-width: 100vh;
    background: #003333;
    border-radius: 8px;
    box-shadow: 0px 0px 15px 3px rgba(0, 0, 0, 0.4);
    font-family: sans-serif;
    padding: 20px;
}

.title {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap-reverse;
    gap: 10px;
}

.Temprature-icon {
    font-size: 45px;
    color: #fff;
}

h1 {
    color: #fff;
    letter-spacing: 1.2px;
    font-size: 30px;
}

#celcius,
#Fahrenheit,
#Kelvin {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 25px;
}

input {
    flex: 5;
    height: 60px;
    font-size: 20px;
    font-weight: 600;
    text-align: center;
    border: none;
    outline: none;
    border-radius: 8px 0 0 8px;
    padding: 0 10px;
}


/* for chrome, safari, egde, opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
    -webkit-appearance: none;
}

/*for morzila firefox */

input {
    -moz-apprearance: textfield;
}

.icon {
    flex: 1;
    height: 60px;
    line-height: 60px;
    padding: 0 5px;
    text-align: center;
    font-size: 30px;
    background: #4d5964;
    color: #fff;
    border-radius: 0 8px 8px 0;
}

.button {
    margin-top: 25px;
    text-align: center;
}

.button button {
    border: none;
    outline: none;
    padding: 10px 30px;
    font-size: 20px;
    font-weight: 600;
    border-radius: 3px;
    cursor: pointer;
    transition: 0.3s;

}

.button button:hover {
    background: #000;
    color: #fff;
}

@media only screen and (max-width: 600px) {

    .container {
        width: 250px;

    }

    #celcius,
    #Fahrenheit,
    #Kelvin {
        text-align: center;
        justify-content: center;
        width: 200px;
    }

    input {
        width: 500px;
        overflow: hidden;
    }

    .container .title h1 {
        display: inline;
        font-size: 30px;
    let celciusInput = document.querySelector('#celcius > input')
let FahrenheitInput = document.querySelector('#Fahrenheit > input')
let kelvinInput = document.querySelector('#Kelvin > input')

let btn = document.querySelector('.button button')
  
function roundnumber(number){
    return Math.round(number*100)/100
}

/* Celcius to fahrenheit and kelvin */

celciusInput.addEventListener('input', function(){
    let ctemp = parseFloat(celciusInput.value)
    let ftemp = (ctemp*(9/5)) + 32
    let ktemp = ctemp + 273.15

    FahrenheitInput.value = roundnumber(ftemp)
    kelvinInput.value = roundnumber(ktemp)
})

/* Fahrenheit to Celcius and kelvin */

FahrenheitInput.addEventListener('input', function(){
    let ftemp = parseFloat(FahrenheitInput.value)
    let ctemp = (ftemp - 32) * (5/9)
    let ktemp = (ftemp - 32) * (5/9) + 273.15

    celciusInput.value = roundnumber(ctemp)
    kelvinInput.value = roundnumber(ktemp)
})

/* kelvin to Celcius ans Fahrenheit */

kelvinInput.addEventListener('input', function(){
    let ktemp = parseFloat(kelvinInput.value)
    let ctemp = ktemp - 273.15
    let ftemp = (ktemp - 273.15) * (9/5) + 32

    celciusInput.value = roundnumber(ctemp)
    FahrenheitInput.value = roundnumber(ftemp)
})

btn.addEventListener('click', ()=>{
    celciusInput.value = ""
    FahrenheitInput.value = ""
    kelvinInput.value = ""
})}
}
