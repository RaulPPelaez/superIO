superIO.h is a small drop in C++ header which provides a class called superIO::superFile that can read lines from a file or pipe super fast.  
It also provides some functions to transform strings to numbers (float, double, int...)  
For that it can use std of boost depending on the USE_BOOST define flag.  

# USAGE

```c++

superIO::superInputFile in("fileName");
//The default constructor uses stdin

if(!in.good()){
	cerr<<"ERROR: Could not read from file!"<<endl;
	exit(1);
}
int numberChars;
char *line = nullptr;

//Get the next line, but do not count it as a read (the position in the file is not advanced)
numberChars = in.peekNextLine(line);
//Check if the line is a comment
if(in.iscomment(line, numberChars, '#')){
//If it is a comment go to the next line
	numberChars = in->getNextLine(line)
}

//Read lines and transform them to numbers, superFile will modify line to point to the start of the next line
while(numberChars = in->getNextLine(line) or ! in.eof()){
	//Number of numbers in the file, you must count them yourself if unknown (i.e with an stringstream)
	
	//This function will transform the string starting with line to the number of elements of the type of numbers
	//Read 3 floats
	float numbers[3];
	int lastUsedChar = superIO::string2numbers(line, numberChars, 3, numbers);
	//And then 2 integers
    //lastUsedChar will be -1 if not enough numbers where found
	int numbersInt[2]
	if(lastUsedChars>0)
		lastUsedChar = superIO::string2numbers(line+lastUsedChar, numberChars-lastUsedChar, 2, numbersInt);			

}

//In a similar way you can use superFile to write

superIO::superOutputFile out("fileName");

float a=1.0f;
int b = 2;

string to_write;
number2string(to_write, a);
to_write += " ";
number2string(to_write, b);
to_write +="\n";

//Write the line to the file
out.write(to_write.c_str(), to_write.size());
//Force to flush to disk
out.flush();

//Now the file contains: 1.0 2


```
