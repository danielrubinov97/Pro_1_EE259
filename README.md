# Pro_1 OUTLINE FROM EE259 COURSE
## My Solution: Daniel Rubinov
###	\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
###	\_                                                                    \_
###	\_   THE CITY COLLEGE OF NEW YORK, ELECTRICAL ENGINEERING DEPARTMENT  \_
###	\_                EE259, DAY-EVENING SECTIONS, FALL 2018              \_
###	\_                                                                    \_
###	\_                              PROJECT 1                             \_
###	\_                                                                    \_
###	\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

PROJECT 1 DESCRIPTION:

Write a C++ class definition called STUDENT_GRADE which will inherit 
from STUDENT_ID class as described below. 

  class STUDENT_GRADE: public STUDENT_ID{
     public:      // public methods for this class

        STUDENT_GRADE(int, int); // example usage: STUDENT_ID C(5, 4);
			// constructor;
			// instantiates object C with 5 students and 4 grades each

	void LIST_IDS(); // list the student ids using p0.h implementation

        void LIST_GRADE(int); // example usage: C.LIST_GRADE(3333);
			// list the grades of student with id 3333
			// returns no values

        void LIST_RANGE(int); // example usage: C.LIST_RANGE(2);
			// list the range of grades in exam 2
			// returns no values

   // protected vars below can only be accessed within this class and inherited classes
   // they are not directly accessible from main
   protected: 	
	int p;
	int grades[20][10]; // 20 students and 10 exams per student max
   };

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

The objects of STUDENT_GRADE class will read the input values from a file called
studentGrade.txt given in the following format:

	int_11 int_12 int_13
	int_21 int_22 int_23
	...
	int_n1 int_n2 int_n3

where each line corresponds to the same line in studentId.txt file as defined
for project 0.


\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

An example of  constructor is as follows:

        STUDENT_GRADE g(x, y); 

which instantiates an object g of class STUDENT_GRADE with x students and
y exams for each student.  The constructor should call base class constructor
as follows:

	STUDENT_GRADE::STUDENT_GRADE(int x, int y)
		: STUDENT_ID(x) // call base class constructor
	{
		// your code for constructor
	}

Base constructor call will make STUDENT_ID class read the id values into 
ids variable as described in project 0. 

After reading the exam values into protected variables, the output message
to out.1.txt file is as follows:
	+ P0 START +
	+ P0 OUTPUT FROM STUDENT_ID CONSTRUCTOR:
	+ P0 INSTANTIATED AN OBJECT OF CLASS STUDENT_ID WITH x STUDENT IDS.
	+ P0 END +
	++ P1 START ++
	++ P1 OUTPUT FROM STUDENT_GRADE CONSTRUCTOR
	++ P1 AN OBJECT OF STUDENT_GRADE IS CREATED WITH x STUDENTS AND y EXAMS EACH.
	++ P1 END ++

Note that the lines starting with P0 are generated by the base class.

Student id values will be between 0 and 9,999, inclusive.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Definition of LIST_IDS method is as follows:

	G.LIST_IDS();

where G is an object of STUDENT_GRADE class.

This class will call LIST_ID method defined in STUDENT_ID class.
The expected output is as follows:

	++ P1 START ++
	++ P1 OUTPUT FROM LIST_IDS
	+ P0 START +
	+ P0 OUTPUT FROM LIST_ID METHOD:
	+ P0 STUDENT IDS FOR n STUDENTS:
	+ P0 id_0
	+ P0 id_2
	...
	+ P0 id_n-1
	++ P1 END ++

Note that the output lines starting with P0 are generated by the base class.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Definition of LIST_GRADE method is as follows:

        C.LIST_GRADE(x);

where C is an object of STUDENT_GRADE class and integer x is the student id.

This method will list the grades for student with id x as follows:

	++ P1 START ++
	++ P1 OUTPUT FROM LIST_GRADE METHOD:
	++ P1 GRADES FOR STUDENT x:
	++ P1 GRADE FOR EXAM 0 IS: int_x_0
	++ P1 GRADE FOR EXAM 1 IS: int_x_1
	...
	++ P1 GRADE FOR EXAM p IS: int_x_p-1
	++ P1 END ++

where integer p is the number of projects.

If there is no student with id x, the output will be:

	++ P1 START ++
	++ P1 OUTPUT FROM LIST_GRADE METHOD:
	++ P1 NO SUCH STUDENT
	++ P1 END ++

If x value is illegal, the output will be:

	++ P1 START ++
	++ P1 OUTPUT FROM LIST_GRADE METHOD:
	++ P1 INPUT ERROR
	++ P1 END ++

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

The definition of FIND_RANGE method is as follows:

	C.FIND_RANGE(x);

where C is a object of class STUDENT_GRADE and x is the exam number. This
method computes the range for exam x as the difference between the minimum
and maximum grades.
	
	range = max - min

The output into out.1.txt file is with the following format:

	++ P1 START ++
	++ P1 OUTPUT FROM LIST_RANGE METHOD:
	++ P1 RANGE FOR EXAM x IS z.
	++ P1 END ++

If x value is illegal, the output will be:

	++ P1 START ++
	++ P1 OUTPUT FROM LIST_RANGE METHOD:
	++ P1 INPUT ERROR
	++ P1 END ++

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

:::::::::::::: EXAMPLE 1 ::::::::::::::::::::: 
---------CONTENTS OF main1_1.cc FILE:-----------
#include "p1.h"
// example program: main1_1.cc
int main ()
{
        STUDENT_GRADE G(5, 4); // instantiate an object C of class STUDENT_GRADE
			// with 5 student ids each with 4 exams

	G.LIST_IDS();
	
	return 0;
}
---------CONTENTS OF studentId.txt FILE:---------------
1111
3333
2222
5555
4444
---------CONTENTS OF studentGrade.txt FILE:---------------
81 91 61 71 
83 93 63 73
82 92 62 72
85 95 65 75
84 94 64 74
---------EXPECTED CONTENTS OF out.1.txt FILE:-----
+ P0 START +
+ P0 OUTPUT FROM STUDENT_ID CONSTRUCTOR:
+ P0 INSTANTIATED AN OBJECT OF CLASS STUDENT_ID WITH 5 STUDENT IDS.
+ P0 END +
++ P1 START ++
++ P1 OUTPUT FROM STUDENT_GRADE CONSTRUCTOR
++ P1 AN OBJECT OF STUDENT_GRADE IS CREATED WITH 5 STUDENTS AND 4 EXAMS EACH.
++ P1 END ++
++ P1 START ++
++ P1 OUTPUT FROM LIST_IDS
+ P0 START +
+ P0 OUTPUT FROM LIST_ID METHOD:
+ P0 STUDENT IDS FOR 5 STUDENTS:
+ P0 1111
+ P0 3333
+ P0 2222
+ P0 5555
+ P0 4444
+ P0 END +
++ P1 END ++
:::::::::::::: EXAMPLE 2 ::::::::::::::::::::: 
---------CONTENTS OF main2.cc FILE:-----------
#include "p1.h"
// example program: main1_2.cc
int main ()
{
        STUDENT_GRADE G(5, 4); // instantiate an object C of class STUDENT_GRADE
			// with 5 student ids each with 4 exams

	G.LIST_GRADE(3333); // list the grades of student with id 3333

	G.LIST_GRADE(8888); // no such student
	
	return 0;
}
---------CONTENTS OF studentId.txt FILE:---------------
1111
3333
2222
5555
4444
---------CONTENTS OF studentGrade.txt FILE:---------------
81 91 61 71 
83 93 63 73
82 92 62 72
85 95 65 75
84 94 64 74
--------EXPECTED CONTENTS OF out.1.txt FILE:-----
+ P0 START +
+ P0 OUTPUT FROM STUDENT_ID CONSTRUCTOR:
+ P0 INSTANTIATED AN OBJECT OF CLASS STUDENT_ID WITH 5 STUDENT IDS.
+ P0 END +
++ P1 START ++
++ P1 OUTPUT FROM STUDENT_GRADE CONSTRUCTOR
++ P1 AN OBJECT OF STUDENT_GRADE IS CREATED WITH 5 STUDENTS AND 4 EXAMS EACH.
++ P1 END ++
++ P1 START ++
++ P1 OUTPUT FROM LIST_GRADE METHOD:
++ P1 GRADES FOR STUDENT 3333:
++ P1 GRADE FOR EXAM 0 IS: 83
++ P1 GRADE FOR EXAM 1 IS: 93
++ P1 GRADE FOR EXAM 2 IS: 63
++ P1 GRADE FOR EXAM 3 IS: 73
++ P1 END ++
++ P1 START ++
++ P1 OUTPUT FROM LIST_GRADE METHOD:
++ P1 NO SUCH STUDENT
++ P1 END ++
:::::::::::::: EXAMPLE 3 ::::::::::::::::::::: 
---------CONTENTS OF main3.cc FILE:-----------
#include "p1.h"
// example program: main1_3.cc
int main ()
{
        STUDENT_GRADE G(5, 4); // instantiate an object C of class STUDENT_GRADE
			// with 5 student ids each with 4 exams

	G.LIST_RANGE(3); // find the range for exam 3
	G.LIST_RANGE(5); // input error
	
	return 0;
}
---------CONTENTS OF studentId.txt FILE:---------------
1111
3333
2222
5555
4444
---------CONTENTS OF studentGrade.txt FILE:---------------
81 91 61 71 
83 93 63 73
82 92 62 72
85 95 65 75
84 94 64 74
---------CONTENTS OF out.1.txt FILE:---------------
+ P0 START +
+ P0 OUTPUT FROM STUDENT_ID CONSTRUCTOR:
+ P0 INSTANTIATED AN OBJECT OF CLASS STUDENT_ID WITH 5 STUDENT IDS.
+ P0 END +
++ P1 START ++
++ P1 OUTPUT FROM STUDENT_GRADE CONSTRUCTOR
++ P1 AN OBJECT OF STUDENT_GRADE IS CREATED WITH 5 STUDENTS AND 4 EXAMS EACH.
++ P1 END ++
++ P1 START ++
++ P1 OUTPUT FROM LIST_RANGE METHOD:
++ P1 RANGE FOR EXAM 3 IS 4.
++ P1 END ++
++ P1 START ++
++ P1 OUTPUT FROM LIST_RANGE METHOD:
++ P1 INPUT ERROR
i++ P1 END ++
