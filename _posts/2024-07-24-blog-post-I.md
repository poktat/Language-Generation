
# How is a proper language generated?
This is a blog based on the paper Language Generation with Limit :)
![NLG](https://phrazor.ai/assets/img/nlg/NLG-workflow.png "NLG")
As we know that the most popular way of langauge generation nowadays is by using the LLMs. In this way, people actually developed a stochastics model under the neural network. With an increasing witness
of the actual strings from the adversary, the accurency of string predication increases as well. We need to emphasize that the generation needs to product distinct strings.
## The Gold-Angluin model: An negative intuition
Sometimes in the theorical exploration,  we can transfer the defination "language" to a more simple way of operation. We will formalize the definition of a language more precisely below, but for now we can think of a language
as simply any set of strings over a fixed alphabet; for example, the strings of the language could be the set of all grammatical sentences (or all well-formed expressions) according to a given grammar.
This is as well the motivation of Gold - Angluin model.  
**Identification:** after a time t, the guess of 𝐾 is correct.  
**Generation:** if there is a time t, such that after that time t, where S_t denotes the sequence presented by the adversary until t, the output of the algorithm always belongs to K-S_t.  
They have a initial idea which is we a universal set U that contains all the possible elelments. And the collections C contains the countable subsets of U, {L_1,L_2,L_3,...}
They proved that the task of identification is impossible. We can give a quick example of this conclusion:
### The framework
A countable infinite collection of possible language candidates 𝐿_1,𝐿_2,𝐿_3,…  
𝑈 denotes the set of all possible elements.  
Each 𝐿_𝑖 contains infinite elements from 𝑈.  
𝐾 = 𝐿_𝑖 is the true language.  
The framework allows us to do membership query for 𝐿_𝑖 but not for 𝐾. 
In another word, the research here is kind  of a set theory game.

### Example of arithmetic progression on integers:
Example of  arithmetic progression on integers：
𝑃_(𝑎,𝑏) defined as all integers in the form of :   
		{𝑎+𝑏𝑖:𝑖=0, 1, 2,…}   
𝑄_(𝑎,𝑏) defined as all integers in the “bidirectional” form of :    
		{𝑎+𝑏𝑖:𝑖= …,−2 ,−1, 0, 1, 2, …}    
𝐶 should be the collection of them all.
Example of  arithmetic progression:
𝐼[𝑎,𝑏] denotes every integer of the interval [𝑎,𝑏].
We enumerate 𝑈 by stages of positive integer counter 𝑠 with increment step 1:
Begin with 𝐼[−𝑠,𝑗(𝑠)] where 𝑗(𝑠) denotes some increasing positive integer.
Each time the algorithm guesses 𝐾=𝑃_(−𝑠,1) switch to the next stage of 𝑠+1
Actually, we choose 𝐾=𝑄_0,1, but the algorithm would never guess correctly.



## The idea of "Closure" by analogy.                                                                                                                                        
We can easily tell that the if we can reach the intersection of all L_i that contains the strings that has been presented by the adeversary. It is safe to keep generating in this 
kind of "Closure". But it can also be seen that we can constructed an example where the closure is strictly finite so that we might not be able to generate nay new strings from the "Closure". 
This may leads to a final failure.
### The illustration of generation assisted by the concept of closure:
An illustration of generation assisted by the concept of closure:
𝐿_𝑖∈𝐶 is call consistent with 𝑆_𝑡 if 𝑆_𝑡 is the subset of 𝐿_𝑖, ⟨𝑆_𝑡 ⟩ denotes the intersection of all 𝐿_𝑖 that is consistent with 𝑆_𝑡 which 	we call it the closure by analogy.
By intuition, it is safe to generate new strings from ⟨𝑆_𝑡⟩−𝑆.
Denote 𝐿(𝑎, 𝑏, 𝑉)=𝑃_(𝑎,𝑏)∪𝑉 where 𝑉 is a finite set of integers. 𝐶 is the collection of all possible 𝐿 with this form.
We claim that ⟨𝑆_𝑡 ⟩=𝑆_𝑡, because 𝑆_𝑡 might completely from the 𝑉. 
This might cause a failure because the strings can not be generated from empty set.




## Direct Hypothesis	
Direct Hypothesis Enumeration:
	The strategy here is to go through the collection C={𝐿_1,𝐿_2, 𝐿_3,..}, 
	and treat each of them as the hypothesis, unless there is a string from 𝑆_𝑡
	doesn’t belong to the present 𝐿_𝑖, move to the next.

The failure here is while 𝐾=𝐿_𝑧, if 𝑖<𝑧 and 𝐿_𝑧⊊𝐿_𝑖, while the adversary always presents elements from 𝐿_𝑧, the algorithm would never move on to the next 𝐿_(𝑖+1).


## The main result from the paper
Firstly, define the concept of critical language:
A language 𝐿_𝑛  is critical at step 𝑡 if 𝐿_𝑛 is consistent with 𝑆_𝑡, and for every language 𝐿_𝑖∈𝐶_𝑛 that is consistent with 𝑆_𝑡, we have 
𝐿_𝑛 ⊆ 𝐿_𝑖.
Here 𝐶_𝑛 denotes a finite collection of 𝐿_𝑖:{𝐿_1,𝐿_2,…, 𝐿_𝑛}
𝐿_𝑧 = 𝐾
An important fact that can be proved:
There exists a time step 𝑡^+  such that for all 𝑡 ≥ 𝑡^+, the 
language 𝐿_𝑧 is critical at step 𝑡.
𝑈 denotes the set of all possible string set 𝑈 = {𝑢_1,𝑢_2,𝑢_3,…}, for simplicity, we sometimes treat 𝑢_𝑖 as 𝑖.
Set 𝐿_𝑧 = 𝐾.
Enumerated strings by step: 𝑤_1,𝑤_2,…
𝐿_(𝑖 ) [𝑚] denotes 𝐿_𝑖∩{𝑢_1,𝑢_2,𝑢_3,…𝑢_𝑚}
An extention definition: A language 𝐿_𝑛 is (𝑡, 𝑚)− critical if 𝐿_𝑛 is consistent with 𝑆_𝑡, and for every language 𝐿_𝑖 ∈ 𝐶_𝑛 such that 𝐿_𝑖 is consistent with St, we have 𝐿_𝑛 [𝑚] ⊆ 𝐿_𝑖 [𝑚].
𝑚_𝑡^((0))  =max⁡(𝑚_(𝑡−1), 𝑤_𝑡 )   
**Algorithm:** Here’s a simplified description of the algorithm without using mathematical symbols:

1. **Initialize and Iterate**: Start with a counter, m, at its initial value and increase it step by step.
2. **Increment Counter**: In each iteration, increase m by 1.
3. **Check Membership**: For each language in the current set, check which strings up to the current m belong to each language.
4. **Identify Critical Languages**: Determine which languages are critical at this stage based on the membership results.
5. **Select String**: If there is a string among those checked that belongs to the critical language but hasn't been produced yet, output this string and update the counter to the current value of m. If not, repeat the iteration.
![image](https://github.com/poktat/Language-Generation/blob/master/images/alg2.png "Algorithm Part I")
![image](https://github.com/poktat/Language-Generation/blob/master/images/alg1.png "Algorithm Part II")

Figure demonstrates the first five steps of the algorithm from Section 5 with a sample input. Strings u2, u5, u8, u10, and u12 are produced sequentially by the adversary. Each step is shown as a vertical column, and each string considered at some step is displayed as a row. An "X" indicates that string uj belongs to language Li.

Shaded rows represent strings already produced (e.g., u8 is shaded only in Step 3). In each step, the algorithm examines languages in Ct = {L1, L2, ..., Lt}, considering a finite prefix from m(0)t to mt, defining the column heights.

Starting with m = m(0)t, the algorithm finds the highest-indexed (t, m)-critical language Lnt(m) in Ct and searches for a new string in Lnt(m), with the critical language possibly changing as m increases.

**In Step 1**, the algorithm generates an arbitrary string.   
**In Step 2**, starting with m(0)t = 5, it tests strings in L2 until finding u7 at m = 7.   
**In Step 3**, starting with m(0)t = 8, it searches in L3 and finds u10 at m = 10.   
**In Step 4**, starting with m(0)t = 10, L4 is consistent but not (t, 10)-critical (since L4[10] ⊄ L3[10]), so L3 remains the highest-indexed (t, 10)-critical language. The algorithm searches for the next um ∈ L3, finding u12 at m = 12.   
**In Step 5**, starting with m(0)t = 12, L5 is the highest-indexed (t, 12)-critical language (since L5[12] ⊆ L3[12] and L2[12]). The algorithm searches for the next um ∈ L5. At m = 14, L5 is no longer (t, 14)-critical (since L5[14] ⊄ L3[14]), so L3 becomes the highest-indexed (t, 14)-critical language. The search continues for the next um ∈ L3, finding u15 at m = 15.   

Algorithm got illustrated by the previous concept "Closure".   

Two cases:  
**Infinite Closure:** With our sample of arithmetic progression, it is safe and easy.  
**Finite Closure:** After the card of $⟨𝑆⟩$,this must be a string that can delete at least 1 potential candidate 𝐿_𝑖  
Above here is basically the content from the paper Language Generation with Limit.

## Further concern in practical concerning
### Countable?
The result form the paper was developed form very strong assumption which is they required the collection of subsets of universal set U to be countable. In the practical situation, it is better to remove this requirement,(under the condition of Areph 1 would be more practical)
### Application difference for different Natural Language System
In natural language case, is the algorithm still effective and powerful for analytic language (Like Chinese) as well as the common research object synthetic language (Like most Latin Languages) after semantics? What about LLMs?

In the exploration, we can easily think of that this way of generation in the more complex practicing situation you need to do a lot of previous work on the semantic understanding and prompt of all the string candidates to achieve a meaningful natural language generation. Hidden compute costs could be a risk.

However, for LLMs. We have this comparison of analytic languages and synthetic languages：

![image](https://github.com/poktat/Language-Generation/blob/master/images/77.png)



### Efficiency Discussion
For the efficiency discussion, I could quest the result from the paper by a counter example:

Here we use the example from regular number(both countable and infinite). We set the true set to be all the regular number in the interval [0,2],  while the collection of the blur sets by accident to be the sequence like this: 
[-1,1], [-2,1], [-3,1]... 
The adversary shell keep enumerating the regular number of [0,1] in some order, and the counter counts from 0 to the negative infinite direction, then after some step t the algorithm should keep generating new string from [-1,1] by the algorithm, which is a failure comparing to our goal. 

And the proof's from the paper is kind of not strong enough to make sure there is a finite stoping time to generate from the true language, but to generate from ite proper subset is useful. There comes another question, is the final practical result be able to produce enough meaningful words in the natural language processing.


## Basic Principle of what Transformers do
### Transformer Architecture Diagram

#### Components Explained:
**Input Embedding:**  
Converts input tokens (words or subwords) into dense vectors.  
**Positional Encoding:**  
Adds positional information to the embeddings to retain the order of tokens.  
**Encoder:**  
**Self-Attention Mechanism:** Computes attention scores to capture relationships between tokens.  
**Feed-Forward Neural Network:** Processes the output of the self-attention mechanism.  
Layer Normalization & Residual Connections: Applied after each sub-layer to stabilize training.  
**Decoder:**  
Masked Self-Attention Mechanism: Prevents attending to future tokens during training. 
Encoder-Decoder Attention: Allows the decoder to focus on relevant parts of the input sequence.  
Feed-Forward Neural Network: Processes the output from the attention mechanisms.  
Layer Normalization & Residual Connections: Applied similarly to the encoder.  
**Output Layer:**  

Produces the final prediction, often through a softmax layer to generate probabilities over the vocabulary.

### Track the probability model working
In the context of transformers, the probability model is typically associated with the final output layer of the model. Here’s a detailed explanation of where and how the probability model fits into the architecture:

#### Location of the Probability Model
**Output Layer:**
**Softmax Layer:** The probability model is implemented here. After the decoder generates logits (raw predictions), the softmax function converts these logits into probabilities. The softmax function ensures that the output values are in the range [0, 1] and sum up to 1, making them interpretable as probabilities.
#### Detailed Breakdown
**Decoder Output:**

After processing through multiple layers of self-attention and feed-forward networks in the decoder, the final representation is generated. This output can be seen as a high-dimensional vector for each token position in the sequence.
Linear Transformation:

The output vectors from the decoder are passed through a linear transformation (dense layer) to map them to the size of the vocabulary. This transformation produces logits, which are unnormalized scores for each token in the vocabulary.
Softmax Function:

The logits are then passed through a softmax function to convert them into probabilities. The softmax function computes the exponential of each logit, normalizes these values, and outputs a probability distribution over the vocabulary for each position in the sequence.

#### Explanation
**Linear Transformation:** The dense layer at the end of the decoder transforms the high-dimensional decoder output into logits corresponding to the vocabulary size.

**Softmax**: This function converts logits into a probability distribution. Each position in the output sequence has a vector of probabilities representing the likelihood of each token in the vocabulary being the next token.

#### Training and Generation
**Training:** During training, the model is optimized to minimize the difference between the predicted probability distribution and the actual target tokens using loss functions like cross-entropy loss.

**Generation:** During inference, the probabilities are used to generate tokens. Techniques like greedy decoding, beam search, or sampling can be employed to generate the final sequence from these probabilities.

This output layer with the softmax function is where the probability model resides, providing a probabilistic interpretation of the model's predictions.













