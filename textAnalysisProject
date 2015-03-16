////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
/////////////////////////////////////////////////////////////////////////	* * * PROJECT 3 * * *	///////////////////////////////////////////////////////////////////////
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
import java.util.*;
import javax.swing.*;
import java.text.*;
import java.io.*;
public class project3Group8
{
   public static File generalFile;
   public static File lexFile;
   public static Scanner forMethods;
   public static PrintWriter generalPrintWriter;
   public static FileWriter generalFileWriter;
   public static ArrayList <String> tempArrayList= new ArrayList<String>();
   public static ArrayList<String> anotherArrayList= new ArrayList<String>();
   public static void main (String [] args)throws IOException
   {	        
           int menuChoice;     
           String choice ="";   
           String check_file_exist = JOptionPane.showInputDialog(null, "Enter the file name: ");
           
           generalFile  = checkingAnExistingFile(check_file_exist); 
           lexFile  = checkingAnExistingFile(check_file_exist); 
           tempArrayList =createTempArray(generalFile);           
           while ( choice !=null && !choice.equals("8"))
                 {
                   choice = getUserChoice();
                   if (choice != null)
                     {
                      menuChoice = Integer.parseInt(choice);   
                        if (menuChoice !=0)
                             {
                               switch (menuChoice)
                                     {
                                       case 1 : addWord();
                                       break;
                                       case 2 : deleteWordFromlist(check_file_exist);
                                       break;
									   case 3 : searchForWord();
                                       break;
                                       case 4 : displayItemOnList();
                                       break;
                                       case 5 : analysisOfEntries(tempArrayList);
                                       break;
                                       case 6 : analysisOfPassageFromtext(forMethods,tempArrayList);
                                       break;
                                       case 7 : lexicographer(check_file_exist);
                                       break;                                       
                                       
                                    }
                             }
                       }         
                 }
   }
   ///////////////////////////////////////////////////////////////***  Create a text file if file does not exist ***///////////////////////////////////////////////   
    
    public static String getUserChoice()
    {
      // Method displays a choice to the end user and returns it back to main.
      String pattern = "[1-8]";
      String errorMessage1  = "Invalid menu Selection.";
             errorMessage1  += "\n\nValid options are 1 to 7 inclusive.";
             errorMessage1  += "\nSelect OK to retry!";
      String menuItem = "";
      String menuDisplay = "1.) Add a Word ." +
    		  			   "\n2.) Delete a Word." +
    		  			   "\n3.) Search for a word." +
    		  			   "\n4.) Display." +
    		  			   "\n5.) Analysis of Entries." +
    		  			   "\n6.) Analyse a passage of txt."+
    		  			   "\n7.) Add words to dictionary file."+
    		  			   "\n8.) Exit";
      
      boolean validInput= false;
      
       while ( !validInput )
            {
             menuItem = JOptionPane.showInputDialog(null, menuDisplay,"Choose number of option you wish to have executed!",3);
             if ( menuItem == null || menuItem.matches(pattern))
                {
                  validInput=true;
                }
             else 
                 JOptionPane.showMessageDialog(null, errorMessage1,"Error in userinput!", 2);

           }
     return menuItem;
   }
   ////////////////////////////////////////////////////////////////////*** Reading the initial file ***////////////////////////////////////////////////////////////////////////////
    
    /* INPUT: User enter the file name he/she want to check.
     * PROCESSING: If the file does not exist it will create an empty text file with 0 bytes.
     * OUTPUT : Creating a text file or opening the existing one.
     */
    public static File checkingAnExistingFile (String check_file_exist) throws IOException
    {    	
        File generalFile = new File(check_file_exist);
        if(!generalFile.exists())
        {
       	 PrintWriter temporary = new PrintWriter (check_file_exist);
       	 JOptionPane.showMessageDialog(null,"The file did not exist but has been created.");       	 
        }
        return generalFile;        
    }
     public static ArrayList<String> createTempArray(File generalFile ) throws IOException
    {  	        	
        	forMethods= new Scanner (generalFile);
        	
	        	while(forMethods.hasNext())
		        	{
		             tempArrayList.add(forMethods.nextLine());        		
		        	}
	        	forMethods.close(); 	
        	   return tempArrayList;         
    } 	
   //////////////////////////////////////////////////////////////////*** Adding the word to the file ***///////////////////////////////////////////////////////////
    
	public static void addWord() throws IOException{
		//User enters word to add to dictionary
		String wordToAdd = JOptionPane.showInputDialog(null, "Enter a word to add: ");
		if(searchDictionaryArrayList(wordToAdd)){//Word is passed to method to check if it is in the dictionary
			JOptionPane.showMessageDialog (null, "The word " + wordToAdd + " is already in the dictionary");//If in dictionary, do nothing 
		}
		else{
			JOptionPane.showMessageDialog(null, wordToAdd + " was not found in dictionary");//If not in dictionary pass word to add method
			addTempArrayList(wordToAdd);	
		}
	}	

	public static boolean searchDictionaryArrayList(String wordToSearch) throws IOException
	{
		int first = 0; int last = tempArrayList.size()-1; int middle = (first + last)/2;
		boolean found = false;
		while(first <= last && !found)
		{
			if((tempArrayList.get(middle)).equalsIgnoreCase(wordToSearch)) 			found = true;
			else if ((tempArrayList.get(middle)).compareToIgnoreCase(wordToSearch) > 0) last = middle - 1;
			else if ((tempArrayList.get(middle)).compareToIgnoreCase(wordToSearch) < 0) first = middle + 1;
			middle = (first + last)/2;
		}
		return found;	
		}

	   public static void addTempArrayList(String wordToSearch) throws IOException{//Method to binary search the array list and return a boolean
		int first = 0, last = anotherArrayList.size()-1; int middle = (first + last)/2;
		boolean found = false;
		while(first <= last && !found)
		{
			if((anotherArrayList.get(middle)).equalsIgnoreCase(wordToSearch)) 			found = true;
			else if ((anotherArrayList.get(middle)).compareToIgnoreCase(wordToSearch) > 0) last = middle - 1;
			else if ((anotherArrayList.get(middle)).compareToIgnoreCase(wordToSearch) < 0) last = middle + 1;
			middle = (first + last)/2;
		}
		if(!found){
			JOptionPane.showMessageDialog(null, "\na lexicographer has been requested to approve the word.\n");
			anotherArrayList.add(wordToSearch);//Adding the word to the temp file 
			Collections.sort(tempArrayList);
			updateWordTxt("Lexicographer.txt", 1);
			}
		else
			JOptionPane.showMessageDialog(null, "\nThe word is currently awaiting a lexicographers approval.\n");
		}
		
	public static void updateWordTxt(String file, int n) throws IOException// This method is used to update the file
	{
		PrintWriter outFile = new PrintWriter(file);
		if(n == 1){
			for(int i =0; i < anotherArrayList.size(); i++){
				outFile.println(anotherArrayList.get(i));
			}
		}
		else
		{
			for(int i =0; i < tempArrayList.size(); i++)
			{
				outFile.println(tempArrayList.get(i));
			}
		}

		outFile.close();
	}		
	
	 public static void lexicographer(String fileName)throws IOException	
	 {
		 File dir = new File("lexicographer.txt");
		 anotherArrayList = createTempArray(dir);
		 for(int i =0; i < anotherArrayList.size();i++)
		 {
			if(!(searchDictionaryArrayList(anotherArrayList.get(i))))
				tempArrayList.add(anotherArrayList.get(i));
		 }	
			Collections.sort(tempArrayList);
			updateWordTxt(fileName, 0);
			JOptionPane.showMessageDialog(null, "Word added to dictionary file.");
		
		 
	}
	                              
   
   /////////////////////////////////////////////////////////////////*** Deleting a word from the file ***////////////////////////////////////////////////////////
   
   public static void deleteWordFromlist(String fileName)throws IOException
   {
	   //User enters word to delete from dicitonary 
		String wordToDelete =JOptionPane.showInputDialog(null, "Please enter a word to delete: ");		
		if(searchDictionaryArrayList(wordToDelete)){//It is passed to the search method to check if it is in the array list
			tempArrayList.remove(wordToDelete);//Remove the word from the array list 
			updateWordTxt(fileName, 0);//Pass the file to the update method
			JOptionPane.showMessageDialog(null,"The word " + wordToDelete + " was deleted from the dictionary.");
		}
		else
		{
			JOptionPane.showMessageDialog(null, wordToDelete + " was not found in dictionary.");			
		}
	}     
  
   /////////////////////////////////////////////////////////////////*** Searching a word from the file ***//////////////////////////////////////////////////////
   
   public static void searchForWord()throws IOException
   {
		String wordToSearch= JOptionPane.showInputDialog(null, "Enter a word to search for: ");
		if(searchDictionaryArrayList(wordToSearch)){//Passes the string input to the search method
			JOptionPane.showMessageDialog (null, "The word " + wordToSearch+ " was found in the dictionary");
		}
		else{
			JOptionPane.showMessageDialog(null,"The word " + wordToSearch + " was not found in the dictionary");			
		}
	}	
  
   /////////////////////////////////////////////////////////////*** Displaying the dictionary file ***///////////////////////////////////////////////////////////
   
   public static void displayItemOnList()throws IOException
   {     
     Scanner in = new Scanner (generalFile);
     // Initialize the size of the text area.
     JTextArea textArea = new JTextArea(30,25);
     String x = "";
     
     while ((generalFile.exists()) && (in.hasNext()))
     {
    	 // Word from the text file is copied to the String x. Then x will be added to TextArea.
    	 x = in.next();
    	 textArea.append(x+"\n");    	 
     }
     in.close();
     JScrollPane scroll = new JScrollPane(textArea);
     JOptionPane.showMessageDialog(null, scroll);     
     
   }
   /////////////////////////////////////////////////////////////////////*** Analyzing the entries ***////////////////////////////////////////////////////////////
   
   public static void analysisOfEntries(ArrayList<String>dictionaryArray)throws IOException
   {    
	   JTextArea textArea = new JTextArea(30,30); 
	   
    /*Input: The input for this method comes from the tempArray which is created in the main method
      The tempArray in this method is refred to as the dictionaryArray    
    
      Process : The process is handled several small section, some of which make calls to ther methods.
      the number of entries in a dictionary file is given as the size of the array list tempArray
      To check whether a word is a palindrome, a loop passed only once through the dictionary file
      and takes each word which is passed to a seperate method to check. if a word is a palindrome
      true is returned here and the word is added to a string which contains confirmed palindromes.
      As the loop executes, the first letter of each word is taken and converted to char, if the 
      first letter matches a pattern of letters, the char is implicitly cast to an int, and this int
      is then used to increment a position in array of length 26, corresponding to each letter inthe alphabet.
      
      A second loop is then used to explicitly cast the wordArray index to a charcter, this character is printed out
      along with the value located at that index, giving the number of times a word begins each letter of the
      alphabet
      
      to determine the lognest and shortest words, a call is made to a seprate method which returns a string,
      containg the longest/shortes words and the length of these words */      
      
   	int x = dictionaryArray.size();
   	if (x != 0)
   	{
  	String result = "", result1 = "", isAPalindrome = "";
  	String word = "";
  	boolean isPalindrome = false, check = false;  	
  	
  	int wordArray [] = new int [26];
  	
  	textArea.append("There are " + x + " entries in the dictionary\n\nPalindrome Check : \n\n");
	String patternlocal = "[A-Za-z]";
	//loop to check what letter a word begins with and increments the value in a corresponding integer array
	for(int i = 0; i < x; i++)
	{
		word = dictionaryArray.get(i);
		//calls a method to check if a word is a palindrome
		isPalindrome = analyzePalindrome(word);
			if (isPalindrome == true)
			{
			check = true;
			textArea.append(word + " is a palindrome\n");
			}
			
		word = word.toLowerCase();
		String letter = word.substring(0,1);//takes first letter of word
		char fChar = letter.charAt(0);//cast the letter to a char
		int nLetter;
		if (letter.matches(patternlocal))
		{
			nLetter = fChar;//implicitly cast the char to an int
			wordArray[nLetter - 97]++;//increments a value in an array correcponding to an alphabetic chracter
		}
	}
	
	//if no words in file are palindromes
	if(check == false)
	textArea.append("No words contained in the dictionary \nwere palindromes");
	
	textArea.append("\n\nNumber of words beginning with letters of\nthe aplhabet : \n\n");
	
	//loop to output the number of times a word begins with a letter.
	for(int i = 0; i < wordArray.length; i++)
	{
		int y = i + 97;
		char c = (char) y;//explicitly casts an char back to a char.
		textArea.append("The number words beginning with '" + c + "' is " + wordArray[i] + "\n");
	}
	
  	String longShortWords = determineLongestShortestWord(dictionaryArray, x);
  	textArea.append("\n\n" + longShortWords);
  	
  	/*OutPut : Output is handled by way of scrolling message dialog box's. given the sheer quantity of information 
  	  that can be produced, particlaly by larger files, it was necessary to do this in order to prevent
  	  a dialog box appearing which prevented a user from seeing all the information. Also, the quantity
  	  of information displayed meant that a user could be subject to information overload due to lots of out
  	  put, as such, it is broken into 4 parts.*/
  
   	 JScrollPane scroll = new JScrollPane(textArea);
     JOptionPane.showMessageDialog(null, scroll);

   }
   else
   JOptionPane.showMessageDialog(null,"Could not analyse file : empty file");
}
   /////////////////////////////////////////////////////////////////*** Analyzing the passage from text ***///////////////////////////////////////////////////////
   
    public static void analysisOfPassageFromtext(Scanner forMethods, ArrayList<String>tempArrayList)throws IOException
   {
    /*This method reads a file  with passages of text and  displays a unique list of words that!
    are present in the file but not in the Dictionary in addition this method writes these into the
    atemporary file soon to be vetted! */
    //Assignment Statements
    String errorMessage;
    String theChoice;
    String empty ="";
    File passageFile;
    Scanner in;
    boolean fileExistOrCorrectFormat= false;
    //check if file exist or user input is in correct format!
    // this method checks if the file format entered is correct
    theChoice = checkValidFile();
                //if Statement to avoid NullPOinter exception if user enters cance button!
                if (theChoice == null)
                fileExistOrCorrectFormat=true;
    
    while (!fileExistOrCorrectFormat )
          { 
            // this method checks if the file format entered is correct
            //avoid issues ff enduser eneters typos! 
            theChoice = theChoice.trim();
            theChoice = theChoice.replaceAll(" ","");
            errorMessage = "This file doesn't exist in Directory\n\nFile Entries are Case sensitive! ";
            //if user input passes format tests a file Object is assigned
              passageFile = new File (theChoice);
              if (!(passageFile.exists()))
                 //check if this file exist!
                 JOptionPane.showMessageDialog(null,errorMessage,"Error: File does not exist!",2);
              else 
                 {    
                  in = new Scanner (passageFile);
                  //Empty string 
                  String result="";
                  //pattern Assignments
                  String pattern= "[,|.|?|:|;|!|\\s|\"|_|%|&|*|+|=|@|#|>|<|0-9]+";
                  String pattern1= "[,|?|:|;|!|\\s|\"|_|%|&|*|+|=|@|(|)|#|>|<|0-9]+";
                    String pattern2="[-]+";
                  //ArrayList for the words in passage.txt file!
                  ArrayList<String> fileCopy =new ArrayList<String>();
                  //ArrayListfor words in Dictionary file
                  //While loop to read lines from passage file into fileCopy ArrayList
                  String tempWord="";
                  while (in.hasNext())
                       {
                        //splitt line from file at whitespace and assign each bit into String Array!
                        String [] lineFromPassageoftext = (in.nextLine()).split(" "); 
                        //for loop to grap each element in String Array                     
                   for ( int i =0; i < lineFromPassageoftext.length; i++)
                       {   
                        // replace all un desired Characters with an empty String 
                        tempWord =lineFromPassageoftext[i]; 
                        //convert tempWord to lowercase
                        tempWord = tempWord.toLowerCase();
                        //repalce all nonCharacters except . - ' with empty string
                        tempWord = tempWord.replaceAll( pattern1,"");
                        //check if temp word ends with txt!
                        if (tempWord.endsWith("txt"))
                           {
                            //if it does do nothing and keep the .in tempWord!
                           }
                           else
                               //replace EVERY nonwordCharacters except - ' with empty string
                               tempWord = tempWord.replaceAll( pattern,"");
                         //assign integer with value 0
                         int charCase=0;
                         int wordLength=tempWord.length(); 
                         //check does String starts and ends with a - 
                         if (tempWord.startsWith("-")&& tempWord.endsWith("-")) 
                                //if yes assgin 3 to charCase
                                charCase = 3; 
                          //check does String starts with a -  
                         else if (tempWord.startsWith("-")) 
                               //if yes assgin 1 to charCase
                               charCase=1;
                               //check does String ends with a - 
                         else if (tempWord.endsWith("-"))
                                 //if yes assgin  to charCase
                                 charCase=2;
                               //switch statements that call individual methods to remove hyphens!
                         switch(charCase)
                               {
                                 case 1: tempWord = removeAllStartHypens(tempWord);
                                 break;
                                 case 2: tempWord = removeAllEndHypens(tempWord);
                                 break;
                                 case 3: tempWord = removeAllStartHypens(tempWord);
                                         tempWord = removeAllEndHypens(tempWord);   
                                 break;
                               }
                        //replace all unnecessary occurences of hyphens in a word!
                        tempWord= tempWord.replaceAll(pattern2,"-");
                        lineFromPassageoftext[i]= tempWord;
                        //if statement to establish that index in Array is NOT EMPTY! lineFromFilePassageoftext[i]
                        if ( !lineFromPassageoftext[i].equals(" ")) 
                              {
                               /*if statement that checks if the Arraylist fileCopy and the ArrayList
                                 dictionaryArray  DO NOT CONTAIN the word which is in the current Array index! */ 
                               if (!fileCopy.contains(lineFromPassageoftext[i]) && !tempArrayList.contains(lineFromPassageoftext[i]))
                                  {
                                    //If Above condition is satisfied the word at the current Array index
                                    //will be added into filecopyArrayList! 
                                    fileCopy.add(lineFromPassageoftext[i]);
                                     Collections.sort(fileCopy);
                                  }
                              }
                        }
                   
                        } 
                  //close Scanner!                       
                  in.close();
                  int check = 0;
                  //call Method to write all words that are in arrayList fileCopy into Lexicographer file 
                  createVettingFile(forMethods, generalPrintWriter, fileCopy, generalFileWriter);
                  String result2 ="";
                  //final boolean statement to stop while Loop!
                  fileExistOrCorrectFormat =true;
                  //Method to display UniqueWords on screen!
                  displayUniqueWords(fileCopy);
         }
      }
   }
   public static void createVettingFile(Scanner forMethods, PrintWriter generalPrintWriter, ArrayList<String>fileCopy, FileWriter generalFileWriter)throws IOException
   {
    /*This Method accepts an Araylist of String type and prints the content of this ArrayList into 
       into the vetting file e.g "Lexicographer.txt" In addidtion this method checks if this file exist at start of 
        method if the file does not exist a file will be created!*/

      //A temp ArrayList that will contain temporary all entries that are present in the FileCopy ArrayList 
      ArrayList<String>tempFileCopy = new ArrayList<String>();
      String vettingFile = "Lexicographer.txt";
      File tempFile = new File (vettingFile);
      
      if (!tempFile.exists())
        {
         PrintWriter aWriter = new PrintWriter(tempFile);
        }
       String lineFromFile = "";
       forMethods = new Scanner (tempFile);
         generalFileWriter =new FileWriter (tempFile, true);
         generalPrintWriter = new PrintWriter(generalFileWriter);
         while(forMethods.hasNext())
               {
                 lineFromFile=forMethods.nextLine();
                 //read line into tempFileCopy
                 tempFileCopy.add(lineFromFile);   
             }
             //close scanner
             forMethods.close();
             // loop to select uniqueList of words!
          for( int index =0; index < fileCopy.size(); index++)
              {   
                //check if tempFileCopy does not contain the word and index in FileCopy!
               if ( !tempFileCopy.contains(fileCopy.get(index)) )
                //if it doesn't print this word into txt file!
               generalPrintWriter.println(fileCopy.get(index));
              }
            //close generalPrintWriter
             generalPrintWriter.close();
            //close generalFileWriter
             generalFileWriter.close();          
   }
   public static void writeToDictionary(String fileName,PrintWriter generalPrintWriter, ArrayList<String>fileCopy, FileWriter generalFileWriter,File textFile)throws IOException
   {
         /*This method accepts a File and writes its contents into DictionaryFile*/
         generalFileWriter =new FileWriter (textFile, true);
         generalPrintWriter = new PrintWriter(generalFileWriter);
         for ( int index =0; index < fileCopy.size(); index++)
              generalPrintWriter.println(fileCopy.get(index));
         generalPrintWriter.close();
         generalFileWriter.close();
        
   }
   
   public static String checkValidFile()
   {
    /*This Method Validates userInput in order to obtain a valid and existing file!*/

    //pattern Assignment 
    String pattern1 = "[A-Za-z.| A-Za-z0-9.]+[A-Za-z]{1}";
    //boolean assignment for while loop
    boolean notValidInput= true;
    //user choice String
    String userChoice ="";      
    //String for error Message 
    String errorMessage1 ="Invalid input for File!\n\nValid format is <filename>.txt";
    //while loop that keeps usre in Input mode until he enters proper value!
    while (notValidInput)
          {
            //display to the enduser a Appropiate Message!
            userChoice = JOptionPane.showInputDialog(null, "Please enter the name of the file!");
             // check if userInput doesn't enter cancel Button! (*)
             if (userChoice != null) 
             {
               //check if user Input matches pattern!
               if (!userChoice.matches(pattern1))
                 {
                   //display to the enduser an Appropiate error Message!
                   JOptionPane.showMessageDialog(null, errorMessage1,"Error in userinput!", 2);
                 }
               else
                  //if it is correct fromat terminate while loop
                  notValidInput =false;
             } 
             else
                  //(*) if user eneters cancel terminate while loop!
                  notValidInput =false;
          }
    //return file name e.g user choice
    return userChoice;
   }
	///////////////////////////////////////////////////////////*** Determine longest/shortest words ***///////////////////////////////////////////////////////////
	
   public static String determineLongestShortestWord(ArrayList<String> word, int length)
	{
		int x, max, min;
		char aChar;
		String wordCopy, longWord = "", shortWord = "", result = "";
		String shortString = "";
		String longString = "";
		String [] wordArray = new String [length];
				int [] numArray = new int [length];
		for(int i = 0; i < length; i++)
		{
			wordArray[i] = word.get(i);
		}

		//loop to assign values paralell integer array containing lengths of the words in the wordArray
		for(int i = 0; i < wordArray.length; i++)
		{
			wordCopy = wordArray[i];
			x = wordCopy.length();
			numArray[i] = x;
		}
    	max = numArray[0];
		min = numArray[0];
		//Assign the min and max values
		for (int i = 0; i < wordArray.length; i++)
		{
			if (numArray[i] > max)
			max = numArray[i];
			if (numArray[i] < min)
			min = numArray[i];
		}
		//2 loops to add the words matching the longest and shortest words to a string seperated by a space.
		for (int i = 0; i < wordArray.length; i++)
		{
			if (wordArray[i].length() == min)
			shortWord += wordArray[i] + " ";
		}
		for (int i = 0; i < wordArray.length; i++)
		{
			if (wordArray[i].length() == max)
			longWord += wordArray[i] + " ";
		}
		//Add the longest and shortest words to 2 arrays, splitting where a space is found.
		String [] shortArray = shortWord.split(" ");
		String [] longArray = longWord.split(" ");  
		//Below : if a short word is found in an array it is added to a new empty string, unless it is already present in the new string
		for (int i = 0; i < shortArray.length; i++)
		{
		if ((shortWord.contains(shortArray[i])) && (!(shortString.contains(shortArray[i]))))
		{
			shortString += shortArray[i] + " ";
		}
		}
		shortString = shortString.replaceAll(" ",", ");//replace all spaces with commas and a space
		//below : if a long word is found in an array it is added to a new empty string, unless it is already present in the new string
		for (int i = 0; i < longArray.length; i++)
		{
		if ((longWord.contains(longArray[i])) && (!(longString.contains(longArray[i]))))
		{
			longString += longArray[i] + " ";
		}
		}
		longString = longString.replaceAll(" ",", ");////replace all spaces with commas and a space
		
		//OUTPUT : The output that is displayed to the user is added to an empty string called result. result is then passed to an output method. 
		result += "The longest word is " + max + " characters in length.\nThe Shortest word is " + min + " characters in length.";
		result += "\nThe longest word/s is/are: " + longString + "\nThe shortest word/s is/are: " + shortString;
		
		return result;
	}
	/////////////////////////////////////////////////////////////////*** Check palindrome ***//////////////////////////////////////////////////////////////////////
		  		 	
	public static boolean analyzePalindrome(String word)
	{
		int wordLength,index, j, k, count = 0;
		String reverseWord = "", trimmedWord = ""; 
		char aChar;
		boolean palin = false;
			for(index = 0; index < word.length(); index++)
			{
				aChar = word.charAt(index);
				if(Character.isLetter(aChar))
				trimmedWord += aChar;
			}
			int length = trimmedWord.length();
				
			for (int i = length - 1; i >= 0; i--)
			{
				reverseWord += trimmedWord.substring(i,i + 1);
			}
			palin = trimmedWord.equalsIgnoreCase(reverseWord);
		return palin;	
	}
  public static String removeAllStartHypens(String tempWord)
  {   
    /*This Method accepts a String and keeps on removin all hypens at the BEGINNING of the word!
      until all hypens in fronT of the word are removed!*/
     boolean notSorted =true;
     while (notSorted)
           {
         int wordLength = tempWord.length();
         tempWord = tempWord.substring(1);
         if (!tempWord.startsWith("-"))
             notSorted=false;
         }
         return tempWord;
   }
   public static String removeAllEndHypens(String tempWord)
   {
     /*This Method accepts a String and keeps on removin all hypens at the END of the word!
      until all hypens  of the word are removed!*/
     boolean notSorted =true;
     
       int wordLength=0;
       while (notSorted)
             { 
            if (tempWord.endsWith("-"))
                   {
               wordLength = tempWord.length();
             tempWord = tempWord.substring(0,wordLength-1 );
          
               }
               else 
                 notSorted =false;
              }       
       return tempWord;
  }
  public static void displayUniqueWords(ArrayList<String>fileCopy)
  {
     JTextArea textArea = new JTextArea(30,25);
     String x = "";
     int i =0; fileCopy.size();
     
     for ( i =0 ; i< fileCopy.size(); i++)
     {
       // Word from the text file is copied to the String x. Then x will be added to TextArea.
       x = fileCopy.get(i);
       textArea.append(x+"\n");      
     }
     JScrollPane scroll = new JScrollPane(textArea);
     JOptionPane.showMessageDialog(null, scroll);     
     
  }
}
