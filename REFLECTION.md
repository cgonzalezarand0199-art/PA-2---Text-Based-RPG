1. For every function you wrote (TODO 1 to 19), explain in your own words what it does and
   give its time complexity in terms of n, the number of scenes. One short paragraph each.
- TODO 1 would initialize scene data and would allocate an array of numChoices_ child pointer set to nullptr at O(1). TODO 2 deletes data_ from each child Scene in choices and frees the choices_ array at O(n). TODO 3 would return true when numChoices_ <= 0 which meant that scenes were a leaf that had no other choices O(1). TODO 4 Will check that index is valid and return the child O(1). TODO 5 Will check that the index is a valid and assigns next into choices O(n). TODO 6 Recursively counts 1 for current scene and the scene will count all of childs O(n). TODO 7 Returns 1 if the scene is an ending or sums the ending O(n). TODO 8 Finds the longest edge path from a node to a leaf O(n). TODO 9 Deletes root_ and resets O(n).
- TODO 10 Opens the story file and builds a tree O(n). TODO 11 I think it parses one scene's fields and builds all numChoice child scenes O(n). TODO 12 prompts users and validation of the input are between 1 and numChoices O(1).TODO 13 Runs playthrough from root to ending or hp = 0 updating all hp, loot, inventory O(n). TODO 14 Prints the total of scenes and endings plus longest playthrough O(n). TODO 15 printEndings is called starting at a root O(n). TODO 16 Traverses throughout the tree and prints a chosen path and text of leafs O(n). TODO 17 goes down the tree picking the child with the highest loot and prints the outcome O(n). TODO 18 Explores all surviving path to find maximum loot and records the path O(n). TODO 19 call bestLoot from root and prints path, loot, and result O(n).

2. Why does each scene allocate exactly numChoices slots instead of declaring Scene<T>*
   choices[3]? What does an ending hold in choices_, and why?
- Because scenes have different branching because of 1-3 answers possible and because we don't want to waste any memory using MAX_CHOICES helps us because it adapts
- Because a leaf node has no other possible choices so using nullptr helps us on not waste heap allocations 

3. Walk through your Scene destructor. What gets deleted, and in what order? What would
   go wrong if choices_ were deleted first?
- It first deletes data_, then it sometimes delete choices_[i] but data_ is always deleted first. If choices_ was deleted first pointers would lose childs scenes. 

4. Show the path greedy took and the path optimal took on your story, with the loot for each.
   Explain why greedy lost. If greedy did not lose, change your story until it does, and explain
   what you changed.
- Greedy: Path 3-1, showboat with rainbow flick -> cuts inside on your weak foot ends with loot 70 and HP 70.
- Optimal: Path 1-2-2-1-1, A wide pass -> holds up play -> passes a header -> sprints into space for a pass -> finesse shot ends with loot 155 and HP 60.

5. bestLoot tries every path, yet it runs in O(n) time. Explain why it is not exponential, using
   what you know about paths and leaves in a tree.
-  I believe it's because in a tree there is only one path from the root to each node. Since subtress don't overlap bestLoot is able to visit the scenes in n times

6. Which List methods does your game use, and why? What does one search cost as the bag
   grows?
- search as it checks for already carried items and not cause duplicates. addFront as new items to the front. size only displays the total of items exists in the inventory. print displays the collected items in the inventory.
- One search cost O(n)