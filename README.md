# Ottoman-Turkish-Compound-Parser

## Objective
This simple and longish algorithm has a simple objective: It parses the compounds in a given Ottoman Turkish text.

## Compunds
In Ottoman Turkish, compounds are generally formed by connecting two words by one of the ı,i,u,ü sounds, which can be called compound markers. 
For instance: 'adl ü kerem

Depending on the final segment of a word, those compund markers can be preceeded by a buffer "y" sound. 
For instance: kabâ-yı zıyâ-yı şevket-i risâlet

-Some compunds do not include a compund marker but they simply include two nominals tied together. In texts, they are written with a hyphen inside the word.
For instance: hâtır-nişân

-Some compunds are written only with a compound marker, such as: kevn ü mekân

-Some compunds are written with a hyphen followed by a compund marker, such as rûh-ı mukaddesine

-Some compunds do not include a compund marker as mentioned, however, they are written with a hyphen in the middle and they must be discriminated from the compounds that include hyphens, such as the pair: kabâ-yı zıyâ-yı şevket-i risâlet and hâtır-nişân

### Regex Codes:
re.findall(r'‘?\w+‘?-y?[ıiuü]', word) for compunds such as rûh-ı mukaddesine

re.findall(r"‘?\w+‘?-[^yıiuü-]+", word) for compunds such as hâtır-nişân


### Procedure
The algorithm takes a text and tokenizes it. 

Then, it starts the index from zero: if the token with that index number follows a rule to be a compound part, then it checks the following 6 words and constitutes the compund(terkip) until the terkip ends. 

Finally, it increments the index by the length of the constituted compound and loops over the rest of the tokens.
