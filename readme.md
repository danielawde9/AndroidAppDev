# MVC
Used for small application

the class Question.kt holds two peices of data: the question text and the question answer (true or false)

    data class Question(@StringRes val textResId: Int, val answer: Boolean)

the data keyword for all model classes (the class will hold data) also the compiler will create extra classes such as equals() and hashcode() and toString()
    
the @string Rest annotation is not required but we recommend you include it 

- the annotation helps the code inspector built into android studio named Lint verify at compile time that usages of the constructor provide a valid string resource ID
- the annotation makes your code more readble for other developer

TestResId is an Int not String because it will hold the ID of the string resource

## Model Question.kt
hold the application's data and "business logic", model the things your app is concerned with, such as user, a product in a store a photo on a server, a television shor or a true false question. 

Model objecs have no knowledge of the UI

## Controller MainActivity.kt
Controller objects tie the view and model objects together. they contain "application logic"
controller are disgned to respind to various events triggered by view objects and to manage the *flow of data from model objects and the view layer*

## View (layout)
view objects know how to draw themselves on the screen and how to respond to a user input like souched

u can use android view classes or create custom classes

## updating the controller layer

we add the questions in string resource folder

then we can create 

        
    private val questionBank = listOf(
        Question(R.string.question_australia, true),
        Question(R.string.question_oceans, true),
        Question(R.string.question_mideast, false),
        Question(R.string.question_africa, false),
        Question(R.string.question_americas, true),
        Question(R.string.question_asia, true))
        
    private var currentIndex = 0
   
later we will see better option to storeing models data
in oncreate

    val questionTextResId = questionBank[currentIndex].testResId
            
    questionTextView.setText(questionTextResId)

create an ID for the questionBank from the model ID
set the value for textview from the ID of the questionBank 

    
    nextButton.setOnClickListener {
        currentIndex = (currentIndex + 1) % questionBank.size
        val questionTextResId = questionBank[currentIndex].textResId
        questionTextView.setText(questionTextResId)
    }
    
increment the currentIndex of the questionBankID
the code is repeated so we make a function of it 

    
    private fun UpdateQuestion(){
        val questionTextResId = questionBank[currentIndex].textResId
        questionTextView.setText(questionTextResId)
    }
 

the next button think each answer is true, let's fix that

/ state / in memory / visible to user / in foreground
/ stopped / yes / no / no
/ paused / yes / partially,yes / no
/ resumed / yes / yes / yes

when rotating the device it will destroy the whole activity 