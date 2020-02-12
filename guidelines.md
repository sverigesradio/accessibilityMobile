These guidelines focus on what we need to do technically to make our apps accessible. Considerations for the design of the product like navigation/flow, copy, color, contrast, font choices etc. hasn't been included. Maybe those should be seperate if this is more of a checklist for developers?

**Suggested accessibility checkboxes for pull requests:**  
- [ ] Fungerar bra med voiceOver/talkBack.
- [ ] Text skalar utan att trunkeras, ingen begränsning på antal rader.
- [ ] Träffytor är minst 44x44 pt/dp.
  
# 👁 Vision 

## VoiceOver/TalkBack

**Interactable**  
Add custom actions where relevant, for clearing a search text field for example.

**Navigable**  
Group relevant content to speed up navigation.

    iOS:
    Add accessibility header trait to group related functions and speed up navigation. The user can use the voiceover rotors to navigate between headers. Using modifier .accessibility(addTraists: .isHeader)

    Order ZStack objects logically using modifier .accessibility(sortPriority: 1)

    Combine accessibility elements of a related functions/elements using modifier .accessibilityElement(children: .combine)

**Element type/trait descriptions**  
Make sure elements have the correct element type/trait description like "Button", "Static text" etc.

    iOS:
    Use UIAccessibilityTrait , like "Button", "Static text" etc.

**Ignore decorative images**  
If images are decorative (there is other information that conveys the meaning). Then mark the image as decorative to have it not be read out loud.  

    iOS:
    Image(decorative: "CheckmarkGlyph").

**Correct language**  
Make sure text in different languages is spoken in the correct language. 

    iOS:
    .accessibilitySpeechLanguage: "fr-FR"

**Support dismiss gesture**  
Support shortcut for dismissing a modal

    iOS: 
    Drawing a Z gesture should dismiss the modal.
    
**Accessibility labels for all elements**  
Add labels for images, icons, buttons etc.

**Accessibility label writing guidelines**  
Add labels to icons/buttons (A plus "+" icon isn't "plus" but "Add to queue").  
Don't include element type in label ("Add", not "Add button"). The OS ads element type automatically.  
Include context when relevant ("Add to queue", not "Add". To differentiate from possible meaning of "Add to favourites").  
Update labels when UI changes ("Download episode" -> "Remove episode").  
Avoid redundancy, if we're in an audio player the context is clear ("Next" not "Next episode").  
When using repetitive elements like a heart button in a list of items, specify context ("Add Creepypodden to favourites" not "Add to favourites").  
Add labels to animation like loading spinners ("Loading").  
Keep it short ("Delete" not "Delete episode from the local storage and remove from downloaded list").  


## Larger text

**Display the same amount of text as default UI.**   
No truncation. No line limit. Only exception is if it's already truncated at normal text size.

**Support "Accessibility bold"**   
All text should become 2 weights heavier when accessibility bold is enabled

**Scale icons/glyps with text**  
Scale icons/glyphs proportionally when text size increases.

**Use scaleable vector graphics**  
Use vector file formats when possible to avoid blurry images when icons/glyphs are scaled up.


# 🖐 Physical and motor 

**Sufficiently large hit area**  
Minimum hit area of 44pt/dp for both width and height.


# 🧠 Cognitive 

**Reduce motion**  
Animations should be turned off/exchanged for cross fade if the user has activated reduced motion.

**Don't autoplay audio/video**   
Don't autoplay or provide an option for turning it on/off.


# 👂 Hearing

**Provide transcripts**  
Provide transcripts of audio and video where possible. 
