### ENTER YOUR NAME:M Sowmya
### ENTER YOUR REGISTER NO. 212221230107
### EX. NO.6
### DATE:
## Implementation of Semantic ANalysis
## Aim: 
To perform Parts of speech identification and Synonym using Natural Language Processing (NLP) techniques. 
 
## Algorithm:
### Step 1:
Import the nltk library.<br>
### Step 2: 
Download the 'punkt', 'wordnet', and 'averaged_perceptron_tagger' resources.<br>
### Step 3:
Accept user input for the text.<br>
### Step 4:
Tokenize the input text into words using the word_tokenize function.<br>
### Step 5:
Iterate through each word in the tokenized text.<br>
•	Perform part-of-speech tagging on the tokenized words using nltk.pos_tag.<br>
•	Print each word along with its corresponding part-of-speech tag.<br>
•	For each verb , iterate through its synsets (sets of synonyms) using wordnet.synsets(word).<br>
•	Extract synonyms and antonyms using lemma.name() and lemma.antonyms()[0].name() respectively.<br>
•	Print the unique sets of synonyms and antonyms.
## Program:
```
import nltk
from nltk.corpus import wordnet

nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')
nltk.download('wordnet')

def get_synonyms(word):
    synonyms = set()
    for syn in wordnet.synsets(word):
        for lemma in syn.lemmas():
            synonyms.add(lemma.name())
    return synonyms

def process_text_file(file_path):
    with open(file_path, 'r') as file:
        text = file.read()
    return text  # Return the processed text

text = process_text_file('ml.txt')

# Tokenize the text into sentences
sentences = nltk.sent_tokenize(text)

for sentence in sentences:
    # Tokenize each sentence into words
    words = nltk.word_tokenize(sentence)

    # Perform part-of-speech tagging
    pos_tags = nltk.pos_tag(words)
    for word, tag in pos_tags:
       print(word,tag)
    synonyms = []
    antonyms = []
    for word in words:
       for syn in wordnet.synsets(word):
         for lemma in syn.lemmas():
            synonyms.append(lemma.name())
              if lemma.antonyms():
                 antonyms.append(lemma.antonyms()[0].name())
    print("Synonyms:",set(synonyms))
    print("Antonyms:",set(antonyms))

    # Extract verbs
    verbs = [word for word, pos in pos_tags if pos.startswith('V')]

    # Get synonyms for each verb
    for verb in verbs:
        synonyms = get_synonyms(verb)
        print(f"Verb: {verb}")
        print(f"Synonyms: {', '.join(synonyms)}\n")
```

## Output:
![AAI ex6 3](https://github.com/MSowmya28/Ex-6--AAI/assets/94154791/2240ad50-bdd3-43cd-9503-fa47df72a1e1)
![AAI ex6 1](https://github.com/MSowmya28/Ex-6--AAI/assets/94154791/26bd2e40-550e-4938-9e6d-d384fd395bb0)
![AAI ex6 2](https://github.com/MSowmya28/Ex-6--AAI/assets/94154791/4e8719d9-82a6-41c9-995e-51e32ef78139)


## Result:
Thus ,the program to perform the Parts of Speech identification and Synonymis executed sucessfully.
