# Session 14 assignment of EPAi4.0

##Context Managers  

#### Problem definition

This assignment's problem statement is formulated as follows:



For this project you have 4 files containing information about persons.

The files are:

    personal_info.csv - personal information such as name, gender, etc. (one row per person)
    vehicles.csv - what vehicle people own (one row per person)
    employment.csv - where a person is employed (one row per person)
    update_status.csv - when the person's data was created and last updated

Each file contains a key, SSN, which uniquely identifies a person.

This key is present in all four files.

You are guaranteed that the same SSN value is present in every file, and that it only appears once per file.

In addition, the files are all sorted by SSN, i.e. the SSN values appear in the same order in each file.

**Goal 1**

Your first task is to create iterators for each of the four files that contained cleaned up data, of the correct type (e.g. string, int, date, etc), and represented by a named tuple.

For now these four iterators are just separate, independent iterators.

**Goal 2**

Create a single iterable that combines all the columns from all the iterators.

The iterable should yield named tuples containing all the columns. Make sure that the SSN's across the files match!

All the files are guaranteed to be in SSN sort order, and every SSN is unique, and every SSN appears in every file.

Make sure the SSN is not repeated 4 times - one time per row is enough!

**Goal 3**

Next, you want to identify any stale records, where stale simply means the record has not been updated since 3/1/2017 (e.g. last update date < 3/1/2017). Create an iterator that only contains current records (i.e. not stale) based on the last_updated field from the status_update file.

**Goal 4**

Find the largest group of car makes for each gender.

Possibly more than one such group per gender exists (equal sizes).




**In sess 14 assignment.ipynb:**
### Helper functions and CSV file readers as functions
_**cast()**_ : function is a helper function to cast a given value to given data type.

_**personal_info_iterator()**_ : a lazy csv file reader that extracts the personal info corresponding to each SSN and 
converts into named tuple.

_**update_status_iterator()**_ : a lazy csv file reader that extracts the update status corresponding to each SSN  
and converts into named tuple.

_**emp_status_iterator()**_ : a lazy csv file reader that extracts the employment status corresponding to each SSN 
and converts into named tuple.

_**vehicles_iterator()**_ : a lazy csv file reader that extracts the vehicle details owned by each SSN and converts 
into named tuple.

### SSN Details Iterable, aggregates the named tuples into single one

 - SSNDetails class implements function init, iter and has a subclass SSNIterator that implements required functions 
   init, iter, next and helper function merge is implemented.
   

### SSNLatestDetails Iterable, filter the old entries and aggregates the named tuples into single one

 - SSNLatestDetails class implements function init, iter and has a subclass SSNIterator that implements required functions 
   init, iter, next and helper function merge is implemented. The next function iterates and only selects entries 
   that are updated on or after 1st March 2017.
   
### Analysis 
 - Last section fulfills the Goal 4 of finding the vehicle makes owned the most by Males and Females.