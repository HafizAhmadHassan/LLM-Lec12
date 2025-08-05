# Lec8  : Byte Pair Encoding

Recap :
    - Implement Simple Tokenisation:
        - every word is unique token

BPE :
    - used in chatgpt
    - we will learn this scheme from scratch

Tokenisation Algorithms:
    - word based : 
        - every word is one token
        - problem : 
            - words not present in vocab?
            - user inputs are not present so leads to error
            - OOV : out of vocab words
            - boy and boys will have different tokens
            - similarity not captured
            - English vocab : 170 thousands
    
    - character
        - instead of having words each character is considered as token
        - Vocab size would be equal to alphabets
            - every language has fixed number of characters
        - it has very small vocabloury size
        - Solve OOV problem
        - memory efficient
        - Problem : meaning with words completely lost
            - For example : boy vs boys 
        - Token sequence is much larger than word
        - Tokenisation and modernisation  meaning would be lost Root words lost

    - subword : best of both
        - Rule1: do not split frequently used words into smaller subwords
        - Rule 2 : split the rare words into smaller meaningful subwords
        - For Example :
            - boy should not be splits
            - boys should  be split into "boy" and "s"

        - because boy appear very frequently

Advantage:
    - The subword splitting helps the model learn that different words with same root word as "token" like "tokens" and tokenizing are similar in meaning

    -  helps model to understand that tokenization and medernisarion are made up of different root words but have the same suffix "ization" and are used in same syntactic situations

    - BPE is subword algorithm 1994 it was data compression algorithms : most common paitr of consecutive bytes of data is replated with a byte that does not occur in data
       - Research Paper: A new algorithm for data compression    

    - Example :
        original data: aaabdaaabac
        byte pair occurs the most : "aa" size should always 2
        replace with "z" because z does not occur
        compressed : zabdzabac

        Now we have "ab" will replace by y
        zydzyac
        
        ac remains it only appears once

        we can do with zy

    BPE Algorithm : exactly are rule1 and rule2