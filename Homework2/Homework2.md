Nathan Gold
###Eco Evo 282 Homework 2

* Question 1A
  * a)What sequence of commands could you use to move to your home directory, then create a directory called Music with subdirectories called Cher, Madonna, U2, and Nickelback?
  * b)From your home directory, what sequence of commands could you use to travel to the Music directory and delete the Nickelback directory and all the terrible files inside 
  * c)How would you delete the Nickelback directory WITHOUT traveling to the Music directory?

* Question 1B
  * a)




#####Answer Key
* Answer 1A
  * a)```
cd ~ #or just cd
mkdir Music
cd Music
mkdir Cher Madonna U2 Nickelback 
```
Another way, using the -p flag and a brace expansion list:
```
cd ~
mkdir -p Music/{Cher,Madonna,U2,Nickelback} #whitespace matters here!



