# Do you know me

> Cli quiz about me hosted on replit and written using replit.
> 
> Tech stack => {nodejs}
> 
> [Click here to play the quiz](https://replit.com/@shmbajaj/doyouknowme#index.js?embed=1&output=1)
> 
> [Click here to view the code on replit](https://replit.com/@shmbajaj/doyouknowme#index.js)

<details>

  <summary>Click here to expand code</summary>
  
  ```javascript
  
const readlinesync = require('readline-sync');
const questionUser = readlinesync.question;
const logger = console.log;

const closestFriend = {
  userName:"Amit Thakur",
  score:3
}

let data = {
  "In which city shubham bajaj born? ":"yamunanagar",
  "Shubham's favourite content creator? ":"none",
  "Shubham's birthdate(DD) ? ":"5",
  "In which city shubham is currently living? ":"bangalore",
  "What he want to be in life? ": "dontknow" 
};

function putSeparator(){
  logger("-----------------------");
  logger("\n");
}

function getUserName(){
  let score = 0;
  let userName = questionUser('May I have your name? ');
  putSeparator();
  return {userName,score};
}

function updateUser(message,answer,score){
    logger(message,answer);
    logger("Your score is",score);
    putSeparator();
}

function askQuestion(question,defaultAnswer,score){
    let userAnswer = questionUser(question).toLowerCase();
    if(userAnswer === defaultAnswer){
        updateUser("You'r right","",++score);
    }else{
        updateUser("You'r wrong correct answer is",defaultAnswer,--score);
    }
    return score;
}

function playQuiz(score){
  let questions = Object.keys(data);
  questions.forEach( ques => {
          score = askQuestion(ques,data[ques],score);
  });
  return score;
}

 function quizRules(user){
   logger("Hi","@"+user.userName);
   logger("Welcome to Do you know me Quiz by @shubhambajaj");
   logger("Here are total",Object.keys(data).length,"questions you have to answer each questions and at the end of quiz you will get to know, How much you know ShubhamBajaj.");
   logger("Get Set Ready!!");
   putSeparator();
}

function displayScore(user){
  logger("Hey",user.userName);
  logger("Thanks for playing Do you know me Quiz by and for @shubhambajaj");
  if(user.score >= closestFriend.score){
      logger("You are closest friend of shubhambajaj","share your score with him to update the closest friend in his records.");
  }
    logger("You scored",user.score);
}

let user = getUserName();
quizRules(user);
user.score = playQuiz(user.score);
displayScore(user);
  ```

</details>
