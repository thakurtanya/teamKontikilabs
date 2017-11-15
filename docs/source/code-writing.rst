#############################################
The Standard Code Writing & Commenting Format
#############################################

Create a New File
=================

Whenever you create a new file, the first line of the file should start with a comment dedicated to the file. The comment structure should be like ::

/******************************************************************
// @desc             : A short description of the file 
// @author           : The name of the developer creating the file 
// @files_required   : Name the required system files 
// @requested_modules: Name the module dependencies, if any 
// @created_date     : Time and date when the file is created. 
/******************************************************************

Functions
=========

It is important that we **write meaningful function names**, following the `lowerCamelCase` naming convention.

Before you start writing the method, you should include a comment stating its purpose.
Remember, to indicate the data type for a ``@param`` or ``@return`` tag, put the data type in {} brackets ::

/******************************************************************
// @desc    : A short description of the function 
// @param   : {data_type_1} paramName1, {data_type_2} paramName2
// @return  : {data_type}
/******************************************************************

Example ::
	
	function processOrder (pdt, x) {     # Note spaces before, after function_name & parenthesis	
		const MAX_ITEMS = 10;        # maximum number of packets 
		const MASK = 0x1F;           # mask bit TCP  	
		return true;		
	}
	
	Avoid obvious comments such as:
	----------------------------------------------------------------------------------------------------------------------------------------------------
	if (a == 5)      // a equals 5
	counter = 0;     // setting the counter to zero
	
	Try to write comments that explain higher level mechanisms or clarify difficult segments of your code. Do not use comments to restate trivial things.


Variables
=========

Variables names should use `lowerCamelCase`. They should also be descriptive. Single character variables and uncommon abbreviations should generally be avoided ::

	var stringMatches = item.match(/ID_([^\n]+)=([^\n]+)/);  # Execute a regex : Add a comment to a global variable
 	----------------------------------------------------------------------------------------------------------------------------------------------------
	var numberCount = 0;   # The local variables need not to be described each time. Don’t wastes your time writing needless comments.


Special Tags
============

When working on code as a team, adopt a consistent set of tags to communicate among programmers.  For example, use a **TODO:** tag to indicate a section of code that requires additional work ::

	function estimate (x, y) {
	    // TODO: implement the calculations 
	    return 0;
	}


Few special tags are :: 

		-----------------------------------------------------------
		| BUG    - a known bug that should be corrected.          |
		-----------------------------------------------------------
		| FIXME  – should be corrected.                           |
		-----------------------------------------------------------
		| HACK   – a workaround.                                  |
		-----------------------------------------------------------
		| TODO   – something to be done.                          |
		-----------------------------------------------------------
		| UNDONE – a reversal or "roll back" of previous code.    |
		-----------------------------------------------------------
		| UX     – user experience, notice about non-trivial code.|
		-----------------------------------------------------------
		
End of the File
===============

Signal the end of any file with the comment structure as below ::

	/******************************************************************
	// EOF : File_Name (Signal the end of a file)
	/******************************************************************


Committing the Code
===================

Follow the below guidelines while pushing the code to the GIT repository:

-	Always create a README.md file using the Markdown Language format.
-	While pushing the code to the repo, add a valid description of the work you have done.
-	Commit code in batches, please avoid small code commits.




