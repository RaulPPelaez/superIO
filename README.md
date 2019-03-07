superIO.h is a small drop in C++ header which provides a class called superIO::superFile that can read lines from a file or pipe super fast.  
It also provides some functions to transform strings to numbers (float, double, int...)  
For that it can use std of boost depending on the USE_BOOST define flag.  

# USAGE

```c++

superIO::superFile in("fileName");
//The default constructor uses stdin

int numberChars;
char *line = nullptr;
//Read lines and transform them to numbers, superFile will modify line to point to the start of the next line
while(numberChars = in->getNextLine(line)){
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

```
