
## Team Members:

1. Amit Adate 
2. Omkar Satpute 
3. Mayank Malik
4. Jaieu Sheil

# Overview

### Directions :

Load the attached fact and rule files into the KB.


Run the queries from the below

## Knowledge Represented

We have created a lot of user models (entire MSAI cohort, Omkar and a few professors). However, not all of them are represented with the same level of detail. The queries below mention which user models work for which query. For details on all the knowledge represented, please refer to the 'FactsFinal_mt3.krf' file.


## Event Recommender

Event Recommender recommends events for the next few days from the current date. It takes into consideration the user interest and provides recommendation based on the user interest. Also, user has flexibility to choose the number of days he/she wants to check the recommendation for.

### Scale :
It works for two professors now:

WillieWilson

AggelosKKatsaggelos


### Query syntax :
(talkrecommender ?talk1 ?person ?noofdays)

### Example :


(talkrecommender ?talk1 WillieWilson 1)


(talkrecommender ?talk1 WillieWilson 5)


(talkrecommender ?talk1 AggelosKKatsaggelos 2)



### Future work for Event Recommender:

As we had limited time, we made the Recommender that works for only two professors now. However, we would like to expand this to all the professors. Similarly, we have events for the month of March only. We would like to add add more facts going forward.


## Group Recommender

The group recommender recommends a group of size 2, 3 or 4 to a student for a particular course. The group is formed such that each member of the group has at least one unique skill.

### Scale:

It works for the following user models right now:

Omkar

Amit

Mayank

Jaieu

### Query Syntax:
(group_suggestion ?person1 ?course ?groupsize ?group)

Note: It takes a while to run since we have a lot of students in the kb. Ideally it should run within a minute.

### Examples:

(group_suggestion Amit NLP-Winter2019 4 ?group)

(group_suggestion Amit NLP-Winter2019 2 ?group)

### Future work for Group Recommender:


Right now, the query takes a while to run. If we had more time, we would have tried to write the query in a different way such that it runs faster. Also, while it checks all the students in the kb, the expertise are not defined for all of them. So, we would have liked to flesh out all the student in the kb instead of a few.



## Help on Assignment

The Help_on_Assignment returns the names of the people who can assist an individual on that assignment. It essentially matches with the expertise required for the completing said assignment

### Scale:

It works for the following user models right now:

Amit

Omkar

Mayank

Jaieu

And it works for the following homeworks:


DL-HW4

NLP-HW4

HCI-HW4


### Query Syntax:
(help_on_assignment ?person1 ?assignment ?person2)

#person1 needs help on assignment, and person 2 is the right match which we find


### Example:

(help_on_assignment Omkar DL-HW4 ?person2)

(help_on_assignment Mayank NLP-HW4 ?person2)

(help_on_assignment Amit KRR-HW4 ?person2)



## Course recommender

The courseRecommender returns the names of the courses that the student could take in the given quarter which also belong to the field of study he is interested in. It essentially matches the academic interest of the student with the field of study of the courses available in the given quarter.


### Scale:

It works for the following user models right now:
Mayank, Amit, Jaieu, Omkar

All the fellow students in the MSAI cohort - Subrat, Harper, Quincia, Lukas, Michael, Rhett, Keith, Jack, Vamsi, Noah, Brandon, Albert, Souvik, Eric, Nicolas, Ikhlas

And it works for the following quarters:
(WinterQuarterFn(AcademicYearFn NorthwesternUniversity (YearFn 2019)))
(SpringQuarterFn(AcademicYearFn NorthwesternUniversity (YearFn 2019)))


### Query Syntax:
(courseRecommender ?student ?quarter ?course)

#?student is looking for course suggestions in ?quarter, and ?course is the right match which we find


### Example:

(courseRecommender Mayank
 (SpringQuarterFn(AcademicYearFn NorthwesternUniversity (YearFn 2019)))
 ?course)

 (courseRecommender Quincia
  (SpringQuarterFn(AcademicYearFn NorthwesternUniversity (YearFn 2019)))
  ?course)

### Future work for Course Recommender:

We would have liked to add more academic details of the student and courses in coming quarters in the kb. Some scheduling aspects could also be added to make better decision about choosing courses.


## Extra: Commoncourse_bet

The Commoncouse_bet returns the names of the people who have the same course. It was an extra function that we generated for trial and is the least complex of our queries.

### Scale:

It works for the following user models right now:

Amit

Omkar

Mayank

Jaieu

Anybody from MSAI - For this query we encapsulated the complete MSAI cohort.


### Query Syntax:

(commomcourse_bet ?person1 ?person2  ?subject)

#This returns a subject that is common to both person1 and person2

### Example:

(commomcourse_bet Amit Mayank  ?subject)

(commomcourse_bet Omkar Jaieu  ?subject)

(commomcourse_bet Amit  ?x  ?subject)

#The previous example produces all the person-subject pair that Amit has, Essentially the entire MSAI cohort.
