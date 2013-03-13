Apriori_Algorithm_Implementation
================================

Implementation of the Apriori algorithm.


A description of each method in this program:

readLines(): reads the file into a two dimensional array and then performs data reduction. It excludes two columns, education number because it's merely a continuous representation of the education category, and fnlwgt, which doesn't seem to have much to do with anything. 
-Apriori(): Contains the main loop that ends when no new item sets above the support count can be found. It combines the prune and join steps.
-generateInitC(): Generates the first generation of Ck. Does so by checking if an item is a hash table, adds it to the hash table and final array list if it's not in the hash table. It outputs an array representation of the array list.
-generateInitL(): Takes the array generated by the above method and runs a membershiptest on it. Prunes andy items not approved of by membershiptest.
-CrossAll(): My join method. Calls Crossing() on 2d array on triangular representation of single array. It's hard to explain, see code. I've left a mark.
-Crossing(): Takes two arrays, checks if they are the same up until array.length-1, and adds their contents together if so. 
-Prune(): Runs membershiptest() on 2d array. if tested itemset is found to be in enough transactions in the database, membershiptest() will add it to the final arraylist.
-membershiptest(): This is my magnum opus. Originally, it required a triple loop, but I replaced it with a double loop and a hashtable. This is also my required efficiency edit. Seeing as data types (gender, nation, age, etc…) will always be in the same position regardless of the transaction number, I made a hashtable of positions for each possible item in set Ck. The hashtable is referenced inside the second for loop, so each item must only be compared to a single item database length times, rather than (database length) x (number of items in a transaction) times. This is a significant time reduction (from 30 minutes, or until heap space fills up, to under one minute).
-main(): calls Apriori(), which runs through loop, then prints contents of resulting aboveSupport arraylist.

Problems encountered:

-There were problems with the results that could have been solved by correctly sampling the data. For example, there were three times as many male 'transactions' as female ones. This led to an overrepresentation of male associations in the results, because the support count had to be higher to accommodate them.
-The same is true of nationality. Most associations include 'United States', very few if any include any other nation.

Results: Associations found greater than k=2 for both algorithms. Test input was census data found on "http://archive.ics.uci.edu/ml/datasets/Census+Income"

Never-married, 0capitalLoss, United-States, 
Never-married, 0capitalLoss, <=50K, 
Never-married, 0capitalLoss, 0cG, 
Never-married, United-States, <=50K, 
Never-married, United-States, 0cG, 
Never-married, <=50K, 0cG, 
White, Male, 0capitalLoss, 
White, Male, 30hpw-40hpw, 
White, Male, United-States, 
White, Male, <=50K, 
White, Male, Married-civ-spouse, 
White, Male, Husband, 
White, Male, 0cG, 
White, Male, Private, 
White, 0capitalLoss, 30hpw-40hpw, 
White, 0capitalLoss, United-States, 
White, 0capitalLoss, <=50K, 
White, 0capitalLoss, Married-civ-spouse, 
White, 0capitalLoss, Husband, 
White, 0capitalLoss, 0cG, 
White, 0capitalLoss, Private, 
White, 30hpw-40hpw, United-States, 
White, 30hpw-40hpw, <=50K, 
White, 30hpw-40hpw, 0cG, 
White, 30hpw-40hpw, Private, 
White, United-States, <=50K, 
White, United-States, Married-civ-spouse, 
White, United-States, Husband, 
White, United-States, 0cG, 
White, United-States, Private, 
White, <=50K, 0cG, 
White, <=50K, Private, 
White, Married-civ-spouse, Husband, 
White, Married-civ-spouse, 0cG, 
White, Husband, 0cG, 
White, 0cG, Private, 
Male, 0capitalLoss, 30hpw-40hpw, 
Male, 0capitalLoss, United-States, 
Male, 0capitalLoss, <=50K, 
Male, 0capitalLoss, Married-civ-spouse, 
Male, 0capitalLoss, Husband, 
Male, 0capitalLoss, 0cG, 
Male, 0capitalLoss, Private, 
Male, 30hpw-40hpw, United-States, 
Male, 30hpw-40hpw, 0cG, 
Male, United-States, <=50K, 
Male, United-States, Married-civ-spouse, 
Male, United-States, Husband, 
Male, United-States, 0cG, 
Male, United-States, Private, 
Male, <=50K, 0cG, 
Male, <=50K, Private, 
Male, Married-civ-spouse, Husband, 
Male, Married-civ-spouse, 0cG, 
Male, Husband, 0cG, 
Male, 0cG, Private, 
0capitalLoss, 30hpw-40hpw, United-States, 
0capitalLoss, 30hpw-40hpw, <=50K, 
0capitalLoss, 30hpw-40hpw, 0cG, 
0capitalLoss, 30hpw-40hpw, Private, 
0capitalLoss, United-States, <=50K, 
0capitalLoss, United-States, Married-civ-spouse, 
0capitalLoss, United-States, Husband, 
0capitalLoss, United-States, 0cG, 
0capitalLoss, United-States, Private, 
0capitalLoss, United-States, HS-grad, 
0capitalLoss, United-States, Female, 
0capitalLoss, <=50K, 0cG, 
0capitalLoss, <=50K, Private, 
0capitalLoss, <=50K, Female, 
0capitalLoss, Married-civ-spouse, Husband, 
0capitalLoss, Married-civ-spouse, 0cG, 
0capitalLoss, Married-civ-spouse, Private, 
0capitalLoss, Husband, 0cG, 
0capitalLoss, 0cG, Private, 
0capitalLoss, 0cG, HS-grad, 
0capitalLoss, 0cG, Female, 
30hpw-40hpw, United-States, <=50K, 
30hpw-40hpw, United-States, 0cG, 
30hpw-40hpw, United-States, Private, 
30hpw-40hpw, <=50K, 0cG, 
30hpw-40hpw, <=50K, Private, 
30hpw-40hpw, 0cG, Private, 
United-States, <=50K, 0cG, 
United-States, <=50K, Private, 
United-States, Married-civ-spouse, Husband, 
United-States, Married-civ-spouse, 0cG, 
United-States, Husband, 0cG, 
United-States, 0cG, Private, 
United-States, 0cG, HS-grad, 
United-States, 0cG, Female, 
<=50K, 0cG, Private, 
<=50K, 0cG, Female, 
Married-civ-spouse, Husband, 0cG, 
Never-married, 0capitalLoss, <=50K, 0cG, 
White, Male, 0capitalLoss, 30hpw-40hpw, 
White, Male, 0capitalLoss, United-States, 
White, Male, 0capitalLoss, <=50K, 
White, Male, 0capitalLoss, Married-civ-spouse, 
White, Male, 0capitalLoss, Husband, 
White, Male, 0capitalLoss, 0cG, 
White, Male, 0capitalLoss, Private, 
White, Male, United-States, <=50K, 
White, Male, United-States, Married-civ-spouse, 
White, Male, United-States, Husband, 
White, Male, United-States, 0cG, 
White, Male, United-States, Private, 
White, Male, <=50K, 0cG, 
White, Male, <=50K, Private, 
White, Male, Married-civ-spouse, Husband, 
White, Male, Married-civ-spouse, 0cG, 
White, Male, Husband, 0cG, 
White, Male, 0cG, Private, 
White, 0capitalLoss, 30hpw-40hpw, United-States, 
White, 0capitalLoss, 30hpw-40hpw, <=50K, 
White, 0capitalLoss, 30hpw-40hpw, 0cG, 
White, 0capitalLoss, 30hpw-40hpw, Private, 
White, 0capitalLoss, United-States, <=50K, 
White, 0capitalLoss, United-States, Married-civ-spouse, 
White, 0capitalLoss, United-States, Husband, 
White, 0capitalLoss, United-States, 0cG, 
White, 0capitalLoss, United-States, Private, 
White, 0capitalLoss, <=50K, 0cG, 
White, 0capitalLoss, <=50K, Private, 
White, 0capitalLoss, Married-civ-spouse, Husband, 
White, 0capitalLoss, Married-civ-spouse, 0cG, 
White, 0capitalLoss, Husband, 0cG, 
White, 0capitalLoss, 0cG, Private, 
White, 30hpw-40hpw, United-States, <=50K, 
White, 30hpw-40hpw, United-States, 0cG, 
White, 30hpw-40hpw, United-States, Private, 
White, 30hpw-40hpw, <=50K, 0cG, 
White, 30hpw-40hpw, 0cG, Private, 
White, United-States, <=50K, 0cG, 
White, United-States, <=50K, Private, 
White, United-States, Married-civ-spouse, Husband, 
White, United-States, Married-civ-spouse, 0cG, 
White, United-States, Husband, 0cG, 
White, United-States, 0cG, Private, 
White, <=50K, 0cG, Private, 
White, Married-civ-spouse, Husband, 0cG, 
Male, 0capitalLoss, 30hpw-40hpw, United-States, 
Male, 0capitalLoss, 30hpw-40hpw, 0cG, 
Male, 0capitalLoss, United-States, <=50K, 
Male, 0capitalLoss, United-States, Married-civ-spouse, 
Male, 0capitalLoss, United-States, Husband, 
Male, 0capitalLoss, United-States, 0cG, 
Male, 0capitalLoss, United-States, Private, 
Male, 0capitalLoss, <=50K, 0cG, 
Male, 0capitalLoss, <=50K, Private, 
Male, 0capitalLoss, Married-civ-spouse, Husband, 
Male, 0capitalLoss, Married-civ-spouse, 0cG, 
Male, 0capitalLoss, Husband, 0cG, 
Male, 0capitalLoss, 0cG, Private, 
Male, 30hpw-40hpw, United-States, 0cG, 
Male, United-States, <=50K, 0cG, 
Male, United-States, <=50K, Private, 
Male, United-States, Married-civ-spouse, Husband, 
Male, United-States, Married-civ-spouse, 0cG, 
Male, United-States, Husband, 0cG, 
Male, United-States, 0cG, Private, 
Male, <=50K, 0cG, Private, 
Male, Married-civ-spouse, Husband, 0cG, 
0capitalLoss, 30hpw-40hpw, United-States, <=50K, 
0capitalLoss, 30hpw-40hpw, United-States, 0cG, 
0capitalLoss, 30hpw-40hpw, United-States, Private, 
0capitalLoss, 30hpw-40hpw, <=50K, 0cG, 
0capitalLoss, 30hpw-40hpw, <=50K, Private, 
0capitalLoss, 30hpw-40hpw, 0cG, Private, 
0capitalLoss, United-States, <=50K, 0cG, 
0capitalLoss, United-States, <=50K, Private, 
0capitalLoss, United-States, Married-civ-spouse, Husband, 
0capitalLoss, United-States, Married-civ-spouse, 0cG, 
0capitalLoss, United-States, Husband, 0cG, 
0capitalLoss, United-States, 0cG, Private, 
0capitalLoss, <=50K, 0cG, Private, 
0capitalLoss, Married-civ-spouse, Husband, 0cG, 
30hpw-40hpw, United-States, <=50K, 0cG, 
30hpw-40hpw, United-States, <=50K, Private, 
30hpw-40hpw, United-States, 0cG, Private, 
30hpw-40hpw, <=50K, 0cG, Private, 
United-States, <=50K, 0cG, Private, 
United-States, Married-civ-spouse, Husband, 0cG, 
White, Male, 0capitalLoss, United-States, <=50K, 
White, Male, 0capitalLoss, United-States, Married-civ-spouse, 
White, Male, 0capitalLoss, United-States, Husband, 
White, Male, 0capitalLoss, United-States, 0cG, 
White, Male, 0capitalLoss, United-States, Private, 
White, Male, 0capitalLoss, <=50K, 0cG, 
White, Male, 0capitalLoss, Married-civ-spouse, Husband, 
White, Male, 0capitalLoss, Married-civ-spouse, 0cG, 
White, Male, 0capitalLoss, Husband, 0cG, 
White, Male, 0capitalLoss, 0cG, Private, 
White, Male, United-States, <=50K, 0cG, 
White, Male, United-States, Married-civ-spouse, Husband, 
White, Male, United-States, Married-civ-spouse, 0cG, 
White, Male, United-States, Husband, 0cG, 
White, Male, United-States, 0cG, Private, 
White, Male, Married-civ-spouse, Husband, 0cG, 
White, 0capitalLoss, 30hpw-40hpw, United-States, <=50K, 
White, 0capitalLoss, 30hpw-40hpw, United-States, 0cG, 
White, 0capitalLoss, 30hpw-40hpw, United-States, Private, 
White, 0capitalLoss, 30hpw-40hpw, <=50K, 0cG, 
White, 0capitalLoss, 30hpw-40hpw, 0cG, Private, 
White, 0capitalLoss, United-States, <=50K, 0cG, 
White, 0capitalLoss, United-States, <=50K, Private, 
White, 0capitalLoss, United-States, Married-civ-spouse, Husband, 
White, 0capitalLoss, United-States, Married-civ-spouse, 0cG, 
White, 0capitalLoss, United-States, 0cG, Private, 
White, 0capitalLoss, <=50K, 0cG, Private, 
White, 0capitalLoss, Married-civ-spouse, Husband, 0cG, 
White, 30hpw-40hpw, United-States, <=50K, 0cG, 
White, United-States, <=50K, 0cG, Private, 
White, United-States, Married-civ-spouse, Husband, 0cG, 
Male, 0capitalLoss, United-States, <=50K, 0cG, 
Male, 0capitalLoss, United-States, <=50K, Private, 
Male, 0capitalLoss, United-States, Married-civ-spouse, Husband, 
Male, 0capitalLoss, United-States, Married-civ-spouse, 0cG, 
Male, 0capitalLoss, United-States, Husband, 0cG, 
Male, 0capitalLoss, United-States, 0cG, Private, 
Male, 0capitalLoss, <=50K, 0cG, Private, 
Male, 0capitalLoss, Married-civ-spouse, Husband, 0cG, 
Male, United-States, Married-civ-spouse, Husband, 0cG, 
0capitalLoss, 30hpw-40hpw, United-States, <=50K, 0cG, 
0capitalLoss, 30hpw-40hpw, United-States, 0cG, Private, 
0capitalLoss, 30hpw-40hpw, <=50K, 0cG, Private, 
0capitalLoss, United-States, <=50K, 0cG, Private, 
0capitalLoss, United-States, Married-civ-spouse, Husband, 0cG, 
White, Male, 0capitalLoss, United-States, <=50K, 0cG, 
White, Male, 0capitalLoss, United-States, Married-civ-spouse, Husband, 
White, Male, 0capitalLoss, United-States, Married-civ-spouse, 0cG, 
White, Male, 0capitalLoss, United-States, 0cG, Private, 
White, Male, 0capitalLoss, Married-civ-spouse, Husband, 0cG, 
White, Male, United-States, Married-civ-spouse, Husband, 0cG, 

