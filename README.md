## intro2 : 
Error : We need an argument in println whose value will be printed instead of {}
Fix : declare a string and add it as an argument to println

## var6 : 
Error : No type was giving to const. consts must always have types when declared
Fix : add a valid type for example ":i32" after NUMBER

## function5 : 
Error : the function square isnt returning anything since the last line is a statement.
Fix : In rust we can return a value by removing ";" at the end or explicitly typing return. No ; is cool so we will use that

## if3 : 
Error : the problem here is that the ifs have different return value types. They should be the same.
Fix : Since to get the habitat we use int (1,2,3) we will set all ifs to return an int so we change the second if from 2.0 (float) to 2 and the last else statement from "Unknown" (string) to just any number other than 1 2 or 3 and it will return "Unknown as the habitat"

## quiz1.rs :
We need to make a function that takes as an argument the number of apples and calculates the price. In the exercise instructions, it says that the price of an apple is 2 but if the number of apples is more than 40 the price of each apple becomes 1. We also see in test that if the number is exactly 40 the price for each apple is still 2 so we need to take that into account in our price calculation.

## primitive_types6 : 
Error : we need to get the second element of the tuple numbers in the var second by destructuring the tuple
Fix : we will use numbers.index_that_we_want so here we want the second number so we will use the index 1

## vecs2 :
in the first function we need to take ownership of element and then change its value (dereference using *) the second function just needs the result and it will be returned as a new member

## move_semantics6 : 
First error : the problem here is that we have a string in data, when we pass it to get_char function, data will be moved and wont be able to be used in string_uppercase. But since the instructions limit us to only adding or removing references we will use & instead
Fix : we need to give get_char a reference to data so that we keep ownership of data and then we can use it in string_uppercase. we will also need to add referencing in fn get_char
Second error : to_uppercase() creates a temporary value, the function returns a new string that we then reference. Which means the new string isnt stored anywhere.
fix : remove referencing in the string_uppercase function

## structs3: 
Error : we need to code the is_international and get_fees functions.
Fix : is_internation will compare the Package.sender_country and Package.recipient_country. If they are different then it will return true. So we edit the return value to be a bool and we do a comparison. 
For get_fees it takes as a parameter self and cents_per_gram. So first, obviously the return value will be a number so we will go with u32 as the return type and then for the logic we will just return the multiplication of the cents_per_gram that we passed with Package.weight_in_grams.

## enums3 : 
Errors : We need to fill Message enum based on the values used in the test so : changecolor, Echo, Move and Quit. Once that is done we need to fix the state.process of Message::ChangeColor there is a pair of () missing and finally as the code says we need to do a match in the process fn
Fix : First fill Message enum with the correct types, add the () in the test and do the match that will call the other functions defined just before 

## strings4 : 
Error : we need to put either string_slice() or string() before each line in the code. The goal here is to known if the line is of type &str then we need string_slice() or of type String then we will put string()
Fix : We need to read the documentation for the functions used here or wecan just hack through it thanks to the compiler. It will tell us if the line is of type &str or String. If everything is correct, the code will compile with no problems.

## modules3 : 
Error : we are missing a module that has SystemTime and UNIX_EPOCH const so we need to import them in use
Fix : after a simple google search, SystemTime is in std::time so we will just add it in the use.

## hasmaps3: 
So we have a hashmap scores that has team names as a keys and Team struct as values for those keys. We will use the Entry API and its methods to populate "scores".

first we will pass a team name clone (to not loose ownership) to the entry() method. This can go 2 ways : 

If there is an entry with the team name that we passed as a key,we will use and_modify() to modify the value associated to the key in our case here it will be the Team structure for "team_name" which consists of goals scored and goals conceded. The modification in itself is : we will add the team_X_score that we got from results to the existing goals scored of team X and the goals of team Y to team X's goals conceded. 

If there is no entry with the team name, we will just insert it in scores and create the Team score with goals scored and goals conceded (based from results just like in and_modify) as a value for that team name in scores.

Tahts for the first team, we just need to do it the other way around for the second team. 

In other words, we will add team_Y_score as goals scored and team_X_score as as goals conceded for team Y.



## quiz2.rs : 
from the test, we see that transformer() function takes a Vec of tuples as an argument so that will be the type of input in transformer().
The tuples are a string and the enum Command that is declared at the top.
again from the tests, we can see that the output will be a Vec of String so that will be the type of output.
for the use needed to import transformer we will need to reach to the top of the file out of test so we will use super. transformer is in my_mlodule so we will access it from there and the end use looks like this : 
use super::my_module::transformer;

now for the for loop in transformer, it destructures the input into string and command. We will do just like what we did previously in the exercices where will match command and go through the elements we declared in enum Command.

So for Uppercase, we will just use to_uppercase() on the string. This will indeed return a type String. Then we will just push the value to the output vec.

for Trim, same thing , we will use .trim() on the string but since the return type is &str and we need a String, we will add the .to_string() before we push it to output.

for Append,it takes num as an argument which is the number of "bar" that we will append to the string. We saw it in the exercises as well so we will use format! macro to append bar to the string and use .repeat() for the num bars we will need to add.


## options3 :
as the compiler says, we use y after a partial move and p doesnt implement Copy so we need to use a ref instead of plain p. Thats why we add ref.

## errors6:
--

## genereic2:
here we can only store u32 in the wrapper. If we try to store another type it won't work. That is what the exercise wants us to change.To be able to store any type, we will edit the struct Wrapper ti have a generic type, the value in the struct will also be of a generic type. we need to also specify this in the impl.

## traits5 : 
the exercise wants us to replace ?? with whats needed and only change that line. The goal here is to make sure that "item" implements both SomeTrait and OtherTrait so that we can use the some_function and other_function on item. We will do the same as we saw in the exercises and make sure item implements both traits.

## quiz3:
we need to set the grade in ReportCard struct to be a generic type so that for Gary Plotter we can print A+ as his grade.
We change the type of grade to a generic. Declare that the struct takes a generic and edit the impl to have the generic as well. Problem is the compiler will hit with an error where we cant print format strings with the generic type so we need to restrict the generic type in the implementation to implement std::fmt::Display.

## lifetime3 :
we need to add lifetime just like what we did in the previous exercices to the Book struct

## tests4 : 
we replace ??? with the correct value rect.width and rect.height to have the test check if the program panics in those cases we add #[should_panic]

## iterators5 :
for count_iterator() we iterate through the hashmap, we filter to get only the values that we want and we use .count() to count the result
for count_collection_iterator() we iterate through the collection. We use map() to get each hashmap in the collection. We use a closure and call count_iterator to count for each hashmap and sum the total.



