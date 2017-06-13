# qsr-tools
Tools for Quran Speech Recognition

## About
This is still work in progress.

## Plan
[CMUSphinx](https://cmusphinx.github.io/) provides a great way to do language independant speech recognition. All needed are a phonetic dictionary, a language model, and an acoustic model.
### Phoentic Dictionary
This describes how a word sounds in terms of 'phones' (think  smallest unit of sound in speech). CMUSphinx docs provide examples like this:
    hello H EH L OW
    world W ER L D
    
However, fortunately, Arabic words are mostly pronounced just as they are written. So, a direct decmposition of words [to letters] is all is needed to build the dictionary. Example:
    قال ق ا ل
    عَمَلَ عَ مَ لَ
    
As shown, the dictionary can use Arabic alphabet, even with diacritics. I was introduced to this fact by [H. Hiyassat](https://sourceforge.net/u/hiyassat/) on SourceForge back in 2013 while working on my graduation project. Other members on
