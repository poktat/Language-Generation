# How is a proper language generated?
This is a blog based on the paper Language Generation with Limit :)
![NLG](https://phrazor.ai/assets/img/nlg/NLG-workflow.png "NLG")
Sometimes in the theorical exploration,  we can transfer the defination "language" to a more simple way of operation, a set of potential strings. 
This is as well the motivation of Gold - Angluin model.  
**Identification:** if there is a after $𝑡^∗$, such that $𝑡^∗$, the guess of $𝐾=𝐿_𝑖$is correct.

**Generation:** if there is a $𝑡^∗$, such that after $𝑡^∗$, where 𝑆_𝑡 denotes the sequence presented by the adversary until 𝑡, the output of the algorithm always belongs to $𝐾−𝑆_𝑡$.

## The Gold-Angluin model: An negative intuition
They have a initial idea which is we a universal set $U$ that contains all the possible elelments. And the collections $C$ contains the countable subsets of $U$, ${L_1,L_2,L_3,...}$
They proved that the task of identification is impossible. We can give a quick example of this conclusion:
### The framework
A countable infinite collection of possible language candidates $𝐿_1,𝐿_2,𝐿_3,…$

𝑈 denotes the set of all possible elements.

Each 𝐿_𝑖 contains infinite elements from 𝑈.

𝐾 = 𝐿_𝑖 is the true language.

The framework allows us to do membership query for 𝐿_𝑖 but not for 𝐾.

### Example of arithmetic progression on integers:
Example of  arithmetic progression on integers:

	  𝑃_(𝑎,𝑏) defined as all integers in the form of :
		{𝑎+𝑏𝑖:𝑖=0, 1, 2,…} 
	  𝑄_(𝑎,𝑏) defined as all integers in the “bidirectional” form of :
		{𝑎+𝑏𝑖:𝑖= …,−2 ,−1, 0, 1, 2, …} 
	  𝐶 should be the collection of them all.
Example of  arithmetic progression:
	𝐼[𝑎,𝑏] denotes every integer of the interval [𝑎,𝑏].
	We enumerate 𝑈 by stages of positive integer counter 𝑠 with increment step 1:
		Begin with 𝐼[−𝑠, 𝑗(𝑠)] where 𝑗(𝑠) denotes some increasing positive integer.
		Each time the algorithm guesses 𝐾=𝑃_(−𝑠,1) switch to the next stage of 𝑠+1
Actually, we choose 𝐾=𝑄_0,1, but the algorithm would never guess correctly.



## The idea of "Closure" by analogy.                                                                                                                                        
We can easily tell that the if we can reach the intersection of all L_i that contains the strings that has been presented by the adeversary. It is safe to keep generating in this 
kind of "Closure". But it can also be seen that we can constructed an example where the closure is strictly finite so that we might not be able to generate nay new strings from the "Closure". 
This may leads to a final failure.
### The illustration of generation assisted by the concept of closure:
An illustration of generation assisted by the concept of closure:
	𝐿_𝑖∈𝐶 is call consistent with 𝑆_𝑡 if 𝑆_𝑡 is the subset of 𝐿_𝑖, ⟨𝑆_𝑡 ⟩ 	denotes the intersection of all 𝐿_𝑖 that is consistent with 𝑆_𝑡 which 	we call it the closure by analogy.
By intuition, it is safe to generate new strings from ⟨𝑆_𝑡 ⟩−𝑆.
![image](https://github.com/user-attachments/assets/235a3a10-fa9b-4ca2-b258-0992af4ec260)
Denote 𝐿(𝑎, 𝑏, 𝑉)=𝑃_(𝑎,𝑏)∪𝑉 where 𝑉 is a finite set of integers. 𝐶 is the collection of all possible 𝐿 with this form.
We claim that ⟨𝑆_𝑡 ⟩=𝑆_𝑡, because 𝑆_𝑡 might completely from the 𝑉. 
This might cause a failure because the strings can not be generated from empty set.
![image](https://github.com/user-attachments/assets/b4024fe2-cd18-4d60-95b4-9ba518cb4d5c)



## Direct Hypothesis	
![image](https://github.com/user-attachments/assets/62ffe52d-3a84-41d3-9916-7445d25da013)

## The main result from the paper
Firstly, define the concept of critical language:
	A language 𝐿_𝑛  is critical at step 𝑡 if 𝐿_𝑛 is consistent with 𝑆_𝑡, and 	for every language 𝐿_𝑖∈𝐶_𝑛 that is consistent with 𝑆_𝑡, we have 
	𝐿_𝑛 ⊆ 𝐿_𝑖.
Here 𝐶_𝑛 denotes a finite collection of 𝐿_𝑖:{𝐿_1,𝐿_2,…, 𝐿_𝑛}
𝐿_𝑧 = 𝐾
An important fact that can be proved:
	 There exists a time step 𝑡^+  such that for all 𝑡 ≥ 𝑡^+, the 
	 language 𝐿_𝑧 is critical at step 𝑡.
![image](https://github.com/user-attachments/assets/f08e3f7f-ced6-4254-889a-a860c0f30fa1)
𝑈 denotes the set of all possible string set 𝑈 = {𝑢_1,𝑢_2,𝑢_3,…}, for simplicity, we sometimes treat 𝑢_𝑖 as 𝑖.
Set 𝐿_𝑧 = 𝐾.
Enumerated strings by step: 𝑤_1,𝑤_2,…
𝐿_(𝑖 ) [𝑚] denotes 𝐿_𝑖∩{𝑢_1,𝑢_2,𝑢_3,…𝑢_𝑚}
An extention definition: A language 𝐿_𝑛 is (𝑡, 𝑚)− critical if 𝐿_𝑛 is consistent with 𝑆_𝑡, and for every language 𝐿_𝑖 ∈ 𝐶_𝑛 such that 𝐿_𝑖 is consistent with St, we have $𝐿_𝑛 [𝑚] ⊆ 𝐿_𝑖 [𝑚]$.
$𝑚_𝑡^((0))  =max⁡(𝑚_(𝑡−1), 𝑤_𝑡 )$
![image](https://github.com/poktat/Language-Generation/blob/master/images/alg2.png "Algorithm Part I")
![image](https://github.com/poktat/Language-Generation/blob/master/images/alg1.png "Algorithm Part II")

Algorithm got illustrated by the previous concept closure.
	Two cases:
		Infinite Closure: With our sample of arithmetic progression, it is safe and easy.
		Finite Closure: After the card of $⟨𝑆⟩$,this must be a string that can delete at least 1 potential candidate $𝐿_𝑖$













