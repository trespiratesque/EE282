Nathan Gold
### Eco Evo 282 Homework 2

* Question 1A
  * a) What sequence of commands could you use to move to your home directory, then create a directory called Music with subdirectories called Cher, Madonna, Bjork, and Nickelback?
  * b) From your home directory, what sequence of commands could you use to travel to the Music directory and delete the Nickelback directory? 
  * c) How might you delete the Nickelback directory if you were in the Cher subdirectory, WITHOUT first navigating to the Music directory? How could you delete the Nickelback directory from an arbitrary location?


* Question 1B
  * a) From inside the Madonna directory, what sequence of commands might you use to quickly create empty files called Vogue.mp3, Cherish.mp3, Believe.mp3, Imagine.mp3,  and Bedtime Story.mp3?
  * b) How would you then view a list of all the files contained in your current directory? Using the file structure from Question 1A, how would you view the files in the Madonna directory if you were currently working in the Cher directory?
  * c) What commands would you use to perform the following operations from inside ~/Music/Madonna: Move Believe.mp3 to ~/Music/Cher, remove Imagine.mp3 from ~/Music/Madonna, and copy Bedtime Story from ~/Music/Madonna to ~/Music/Bjork?

* Question 2
Given the following, where dogNotes is a matrix and catNotes is a dataframe:
```
>dogNotes
             Mass    Color    
Bird         "45lbs" "Brown"  
Jackson      "55lbs" "Black"  
Harley       "75lbs" "Yellow" 
Liberty Bell "40lbs" "Mottled"

> catNotes
             Mass            Color
Agatha       10.0           Calico
Empires       8.0            Black
Ruckus        9.0 Gray/White Tabby
Big Kitty    11.5           Orange
Little Kitty 10.0            Gray
```
  * a) How would you access Harley's mass, using row and column names? What about Big Kitty's color?
  * b) There are at least three ways to return the values in a dataframe's column as a vector. Give two ways to return a vector of cat colors, and one way to return a dataframe of cat names and colors. 

* Question 3
Given the following file structure:
```
/usr/
    bwehrle/
           data/
           kites/
           scripts/
                  helloWorld.txt
```
What chmod commands would you use to make helloWorld.txt readable by anyone, without exposing other files or directories to being read? Hint: In order to view a file, all of its parent directories must be executable, and the file itself must be readable.

##### Answer Key
* Answer 1A
  * a)
```
cd ~ #This will always take you to your home directory, as will just plain cd
mkdir Music #Make a subdirectory in my current location and call it Music
cd Music #Move (or "change directory") into the Music directory
mkdir Cher Madonna Bjork Nickelback  #Make subdirectories in my current location called Cher, Madonna, Bjork, and Nickelback
```
Another way, using the **-p** flag and a brace expansion list:
```
cd ~ #Go to home directory
mkdir -p Music/{Cher,Madonna,Bjork,Nickelback} #Make a directory called Music if one doesn't exist already, and make these other directories inside. Without the -p switch, mkdir would fail is the Music folder didn't already exist.
```
  * b)
```
cd Music
rmdir Nickelback #Remove the directory called Nickelback - if it contained files, you would need to use a different command
```
  * c)
```
rmdir ../Nickelback #In the directory one level above my current directory, remove a subdirectory called Nickelback
```
To remove a directory from an arbitrary location, use its full or absolute path, instead of its path relative to your location:
```
rmdir ~/Music/Nickelback
```

* Answer 1B
  * a)
```
touch Vogue.mp3 Cherish.mp3 Believe.mp3 "Bedtime Story.mp3"  #You could also contain the filenames inside {}, separated by commas, as with mkdir in question 1A
```
  * b)
```
ls  #list all normal files in my current directory. Add the -a switch to list all files including hidden files (i.e. files whose names start with a .
```
You can use *ls* to view the contents of any directory you have access to on your working server, simply by passing it as an argument to *ls*
```
ls ~/Music/Madonna
```
  * c)
```
mv Believe.mp3 ~/Music/Cher
rm Imagine.mp3
cp "Bedtime Story.mp3" ~/Music/Bjork  #be sure to use quotes if there are spaces in a filename, but try not to create filenames with spaces
```

* Answer 2
  * a) 
```
dogNotes['Harley', 'Mass'] #return the value from the matrix dogNotes at the intersection of row 'Harley' and column 'Mass'
catNotes['Big Kitty', 'Color'] #return the value from the dataframe catNotes at the intersection of row 'Big Kitty' and column 'Color'
```
  * b)
Three ways to return a vector of cat colors:
```
catNotes[,'Color'] 
catNotes$Color
catNoters[['Color']]
```
And one way to return a subsetted dataframe of row names and corresponding colors:
```
catNotes['Color']
```

* Answer 3
```
chmod o+r /usr/bwehrle/scripts/helloWorld.txt #give "others" group read permissions on the helloWorld file
<STILL NEED TO CHANGE PERMS ON DIRECTORIES
```
