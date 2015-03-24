varun seth presents : revision program , the great flashcards memorizer


# Revision Program (hosted on Google code) #
This is Revision Program . I made this program for learning stuff and keeping them in memory with minimum number of revisions. It lets you create flash cards, with question and answer. It uses an algorithm to minimize the time of revising stuff, and use "practice" instead of "studying" to ensure better memorization.  If you don't wanna type your flash cards, check out www.quizlet.com for free flash cards. Revision Program is a free for personal use.

## Tutorial on using Revising Program ##
1) Download setup file for Revision Program [rev\_Setup\_0.30c](http://revisionprogram.googlecode.com/files/rev_Setup_0.30c.exe) or any similar file in downloads-list to get the installer of **Revision Program** or **Rev**. After download, run it, and install it at your favorite place!!

2) Download a deck of flash cards, for the first time, you may download [Multiplication Tables](http://revisionprogram.googlecode.com/files/MultiplicationTables.mindz) , later on you can go to [Barron's list](http://revisionprogram.googlecode.com/files/Barron%27s%20GRE%20WordList.mindz). After downloading, just run the minz file . If you have installed **Rev**, it will immediately extract a `"MultiplicationTables"` file in the directory of the downloaded file, and you can go to step 3.
Other wise you will have to hack "minz" file, it is an archive file, with special LZMA compression. Since **rev** is not a commercial program, I have taken the commandline extraction and compression program for LZMa archive's from Igor Pavlov. It is included in **Rev**'s bin directory. So you need to send a commandline argument to that LZMA.exe to extract the compressed "mindz" file.

3) After the extraction, run `"MultiplicationTables"` (mind file) . Again if **Rev** is installed, you will see a pop-up window with heading **Revision Program**. If yes, go to step 4, Otherwise, hack around and somehow send command-line argument to **Rev** as :  `rev <-filename->`

4) Now press enter, and the test begins ( mouse wont work on **Rev**, because mouse keys have not been coded inside **Rev** But everything inside the program can be done using arrow-keys and numerical buttons). Now it asks you a question, say " 3 x 15 = " , now you are supposed to think of its answer in your brain, and then hit enter. The answer appears. If you thought answer matches this , ie, if you had a correct answer, the just hit enter again for next question , and the chain continues. Other wise if the answer was wrong, now you need to manually give a grade yourself. If you are seeing this question for the first time and want to learn this before being able to practice, hit zero.
If you just got the answer wrong then hit 1. If you answer was very close to correct but not correct,(or was incomplete) then hit 2. If there is still some other case, then email that case to me!! :P

5) The program will anaylize you weak points and strong points and from next time, it will try to reduce your time to answer / recall the same question. To exit program ( and save the analysis report) press ESC button. To ext program without saving report, hit the red cross.
> Also , while revising, when a question shows up, we can type the answer and press enter to see answer. Unfortunately, **rev** will not check if the two answers match, so thinking the answer in mind would be fastest deal!! Because the aim of this game is to get faster and faster!!!


## Tutorial on Adding flash cards ##
Open the program and goto "Add Data" button.(use arrow keys) ( or hit 1 ) . You may add questions and answers manually or you may also right click and paste the whole line.

First it takes question, as a line without any `enter` or `tab` in the middle of that line. So just type a plain line. When done, hit enter to give a line for the answer of that flash card. Hitting enter again will continue to the next question. When you dont want to add more questions, hit `ESC` button. It will show `Data Stored ---` This means that yes the data is now stored and you can safely turn off the program.
To create a title, start a line with `:` colon, and it will be taken as a title. (when program asks to add question) . To make a subtitle, go for `::` .
To make a comment, start a line with `;` semicolon. To save a note, start a line with `@` . A comment would only appear when you open the mind file in a notepad (any text-editor), but a note also appears in tests but doesn't ask anything.


**Revison Program** also takes some special characters while taking input. You can play around by hitting `CTRL` + `A' to get an alpha symbol. Try other combination and find out what you like!! There are also certain hidden features deep inside the program, which will remain un-documented :P :P !!! For example while adding data, if we press `CTRL` + `Backspace` then it takes it as an alarm and every time the question appears it plays an alarm sound!!! A lot of suck Easter eggs have bean hidden to surprise you  on a rainy day :)


# More about Grades #
When revising (testing), it shows up question, you may try typing answer or think of it in mind. when done, it will display the answer to compare it with your original answer.

After this it will ask for grade. It means "what do you think how much you remember??"
It will accept grade in this manner :-

0 = I just donn know at all

1 = poor response

2 = I sort of remembered it

3 = Yes, correctly recalled

4 = better than 3

5 = better than 4  ... Ans so on till 9

It stores this grade and judges our memory. If we remember something very easily, and give good responses, the question will come less often. On the other hand, bad response will give higher frequency of that question so that we get more chance to learn it.

Technically, it makes a number "LEVEL" for every question-answer pair. When the response is good, the number LEVEL is increased . High "LEVEL" questions come less often. If the grade is low, the number LEVEL is lowered, and the frequency of that question increases.

Highest frequency = question comes on every run of the program
Lowest frequency = Question repeats after 50 years (If program is run 4 times each day.)

It is can be calculated (easily) that lowest frequency come only after 25th revision if that question is graded 3 each time it came.


This program creates text files to store these sets of question-answers . The format is :-

Question   `<TAB>`   Answer     `<Enter>`

Another Question........`<and so on>`

OR

Question   `<TAB>`   Answer     `<TAB>`   LEVEL  `<TAB>`  Delay   `<Enter>`

check out [Syntax](Syntax.md) for better experience.

Here this program stores that number number LEVEL inside file after the question-answer set. (After a tab.)
The number "DELAY" is also stored next. Delay is the number which tell the software how much later should the question come. I mean, if delay is zero, question will appear otherwise the delay is reduced by one and stored. (delay = 5 gets delay =4 and so on after every run , untill it gets zero)

When delay = 0 , the corresponding question is taken into test, asked to user, the grade is taken and then, a new delay is calculated using the updated number LEVEL . I have used very simple Fibonacci series for this purpose. LEVEL goes like 0,1,2,3,4...and so on.
The corresponding delay is the Fibonacci no. 0,1,1,2,3,5,8,13......


I took this series for 3 reasons :
1) We need to recall things very often if its new. Old things hardly need any revision
Its that a fact which we learned long ago, if it is revised, it will keep in memory for extremely long period.

2) The curve in the Fibonacci sequence goes in a very unique way. It is slow at start but very high after some time. This happens at every step!!!

3) Nature uses Fibonacci sequence in many ways, I also tried to do so

## Input ##
Keyboard is fully supported, but the modern keys like play, or volume are simply ignored.

Mouse is not supported as a GUI program with big click-able buttons, but mouse wheel can be used to move up/down, and slider on the left can be moved with mouse. Also right click and copy-paste works. To copy, you need to rightclick -> mark -> hold left mouse button down and drag to make a selection. Let the left mouse button free. Right click again and that selection is copied. This program works good with keyboard only. You may contact me to enable mouse or other features.

Game-pad is not supported, because of lack of API's to get input from all gamepads. But still, I myself use gamepad by emulating the keyboard keys onto game-pad. Example, when I press gamepad.3, program thinks as if it is keyboard.3