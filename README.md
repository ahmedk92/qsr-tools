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
    
As shown, the dictionary can use Arabic alphabet, even with diacritics. I was introduced to this fact by [H. Hiyassat](https://sourceforge.net/u/hiyassat/) on SourceForge back in 2013 while working on my graduation project. Other members on the SourceForge forum were helpful too.

For building the model, we can stop here. But for better results, differentation between multiple pronunciation may exist for a single word (even a diacrticized word). Example (taken from a [paper](http://www.sciencedirect.com/science/article/pii/S1110866516300123) on the same subject):

    الرَحْمَنِ
    
The word exists with the same diacritics in two locations. (1) In Basmalah `بسم الله الرحمن الرحيم`. (2) The second in the beginning of an Ayah like `الرحمن الرحيم` (Fatiha/2). Specifically, in the first location the A-sounding letter alef (or hamza) is not pronounced, while it's pronounced in example (2). This leads us to manually look for and add alternate pronunciation for every relevant word throughout the entire Quran text.

### Language Model
This describes the frequency by which a word is most likely to come after a given word. Thankfully, this step can be automatically done using the sphinx tools, provided we have the whole Quran text (with diacritics) in plain text format.

### Acoustic Model
This is like the language model, but for sounds. That is, the frequency by which a sound is more likely to come after a given sound. For example (a hypothetical example), the sound ع is the most likely to come after the sound ف. Such model is obtaining via feeding pairs of sound and transcription to the relevant sphinx tool. That is, every Aya in text against the Aya in sound. This is needed to be done for many reciters. In the paper linked above, they used 22 reciters. According to the sphinx docs, a similar use case (generic dictation) may need up to 50 different reciters. Thankfully, such audio data exist online Alhamdulillah. Attention must be paid for the technical requirements for this phase; such as the audio format (WAV), sample rate, ...etc. All is written in the sphinx docs.

### Footnote
The CMUSphinx docs are excellent. They dive into the finest detail to make all things work. [Check them](https://cmusphinx.github.io/wiki/tutorial/) to start.
