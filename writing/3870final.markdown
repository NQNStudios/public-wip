# Return to the Heartitorium

[TODO APA format]

## Introduction

According to the best available records, "The Heartitorium" first appeared in
the Salt Lake Telegram on February 26, 1917. It was a newspaper column which
advertised "ADVICE TO WOMEN AND MEN WHO ARE TROUBLED" from a woman named
Kathleen Kaye. The usual format of the column was an alternation of letters
from readers as transcribed by Kaye, and Kaye's thoughtful responses to them,
both being of highly variable length. It was common for readers to express
profound gratitude towards Kaye, crediting her with brightening their lives and
informing their important decisions.

Despite the column's depth and enduring value to its community of readers,
remnants of the Heartitorium are very scarce online&mdash;neither the column
nor Kaye is documented on Wikipedia, for instance. The most readily available
(and perhaps, only) external documentation of its existence is in a thesis from
Utah State University in 2014: "Sinners in the City of Saints: Flappers in Salt
Lake City." Analyzing it alongside the LDS church-affiliated *Young Woman's
Journal*, Bree Ann Romero wrote that the Heartitorium "reflected a secular map
of progressive expectations[...] in the nineteen twenties" (Romero, 2014, p.
14).

Romero's interest in the Heartitorium no doubt stems from its stellar
exemplification of an important concept in Rhetoric studies: That "Writing
enacts and creates identities and ideologies," as described by Tony Scott in
a section of *Naming What We Know.* The primary identity categories invoked in
the Heartitorium community were those of gender, specifically boys, girls, men,
and women, as such were commonly defined in the early 20th century. Romero's
analysis is primarily concerned with the flapper identity iconic to the '20s,
but many more identities and intersections thereof permeate the column's active
readership. During World War I, Kaye maintained supportive correspondence with
young male soldiers, one of whom she happily put into contact with a female
reader upon request (10188093).

While Romero gives many compelling observations on identity-producing rhetoric
in the Heartitorium and several other print publications of the time concerning
personal life advice, one must imagine that comprehensive research on such
written materials would be a herculean task. Romero believes (not unfoundedly)
that the Heartitorium was more progressive than its counterparts with more
direct roots in the LDS church. Still, one might ask, how do we *really* know?
Could we produce convincing evidence to compare the social impacts of these
community-driven publications? Could corpus linguistics trace the creation of
an identity? The goal of this research is to test these waters and suggest
further avenues for digital inquiry that may further the infusion of Writing
studies with computational linguistic techniques. It should also demonstrate
that with current technology and the prevalence of digital archives, meaningful
corpus linguistics research could be attainable even in undergraduate
classrooms.

## Research Methods

I first discovered the archived Heartitorium columns in January 2018 while
working on the Utah Digital Newspapers project, and have ever since been
fascinated with it. As a genderqueer individual born in Utah at the end of the
20th century and living there ever since, much of my thoughts are already
occupied with the nature of gender and gendered communication in society. The
Heartitorium can be seen as an extremely high-density time capsule of gendered
communication of early 20th-century Utah: through Kaye's declared focus on
"Domestic Worries" (18862509) her readers (both "Women and Men Who Are
Troubled") clearly felt encouraged to speak directly about romance and gender
roles. Within a few minutes of randomly browsing Heartitorium columns, one can
easily stumble across confessions concerning body image (18874951), pep-talks
given in the face of hopelessly unrequited love (18864880), and queries as to
the proper age for girls to begin flirting (18862509). Because of this the
Heartitorium makes for entertaining, and sometimes shocking, reading. Because
it is only preserved within the much larger UDN archive, my experience working
with the digital archive's internal systems positions me to be uniquely able to
navigate the archive.

By virtue of its origin in the early 20th century, the Heartitorium community
is inherently protected against any number of privacy violations or other harm
caused by research. Although letters to Kaye and the Heartitorium were required
to feature a full name and address, they were only published with pseudonyms
chosen by their writers, and it is unlikely that original copies of letters to
the Heartitorium still exist. Thus, all participants in the community excepting
Kathleen Kaye herself will retain their anonymity. Since Kaye's personal life
is not the object of study, but rather her public interactions with her
readers, her privacy should remain reasonably well-protected as well (aside
from brief conjecture about her marital status).

This temporal buffer is a double-edged sword. Unfortunately, because the
Heartitorium community is no longer active and its members have all passed
away, it is impossible to obtain first-hand narratives or interviews about the
Heartitorium. The content of some interactions in the community, such as
a promised face-to-face meeting between Kaye and the reader identified as "M.
B. N" that was arranged over telephone (Kaye, 1917, 18874951), will never be
observed unless they were documented in personal journals and later archived.
While it's likely that "M. B. N" wrote in her journal about meeting Kaye,
having stated in her letter "I should adore to meet you," it would be difficult
to connect such a record directly with the "M. B. N." letter in the
Heartitorium, especially if the writer's full name did not really have the
initials M., B., and N. Such an endeavor is well beyond the scope of this
study.

The primary tool for research is the Utah Digital Newspapers archive, whose
website boasts "This site currently holds more than two million pages, and it
continues to grow." Along with high-resolution scans of a high volume of
historical Utah newspapers, the archive contains strings of Optical Character
Recognition text (OCR) for each document, opening the door to computational
study of Utah newspaper content.

The reliance on OCR comes with its own drawbacks. Despite best efforts at
physical preservation, many of the newspapers scanned by the Utah Digital
Newspapers project had suffered degradation in readability, owed to being
already more than one hundred years old before the first UDN papers were
scanned. It is unknown when exactly the OCR process was applied on the
documents in question, but OCR being a fragile and error-prone process,
especially prior to recent advances in machine learning technology, much of the
UDN OCR text is riddled with errors and illegible sections. This includes the
OCR of Heartitorium columns.

Despite this, I theorized that a subset of Natural Language Processing
techniques might still yield noteworthy results when applied to imperfect OCR
text, and set about collecting the text every known Heartitorium column into
a sizable corpus for use with the Natural Language Toolkit. I did this by
writing a program using the UDN API to extract every document responding to the
distinctive search query "Heartitorium," and store their OCR text in text files
also containing potentially useful metadata about the documents. "Heartitorium"
works as an adequate search query because in the UDN archive, the titles of
articles were transcribed by humans, not OCR, which is unlikely to properly
transcribe instances of complex wordplay. Despite being commonly invoked by
readers in their letters, the name "Heartitorium" seems not to appear in the
OCR, only document titles. Some relevant documents may have been omitted in the
search if the title was ever incorrectly transcribed.

After constructing the corpus of OCR text, errors in the text are identified by
searching a dictionary for each token (word) in the OCR text. Tokens that do
not exist in the dictionary searched were marked as errors with the bracket
syntax described above. This process has its limitations: mainly, that it does
not remove all errors (as in the case where OCR incorrectly identifies a word
as being a *different* but still *valid* word), and that it sometimes removes
valid proper nouns (such as "Heartitorium.")

Once this was done, three techniques were used for data analysis: Concordance generation, collocation generation, and random sampling.

### Concordance

Using the Natural Language ToolKit, it is trivial to produce what is known as a "concordance" of a specific word. That is, a list of occurrances of that word, given in context.
 
Here are two examples of such concordances displayed in a command-line terminal. The first displays contexts in which the word "boy" occurs, and the second displays the same for the word "girl."

![Figure 1](concordance-fig.png)

![Figure 2](concordance-fig2.png)

Where numbers occur within brackets, errors in the Heartitorium OCR text have been omitted. This process is not itself a feature of the Natural Language ToolKit, which is designed for working with fully validated strings. Rather, it was implemented to adapt NLTK for usage with highly error-filled bodies of text such as the UDN archive. Rather than remove errors completely, it was deemed necessary to leave an indication of where errors were found, in order to avoid wrongly believing certain words to have occurred adjacent to each other when they were in fact separated by other strings of text the OCR could not identify properly.

### Collocations

Documenting the location of identifiable errors to avoid false text adjacency reports is especially important when applying collocation searches on the Heartitorium corpus. A collocation list is the set of words in a corpus that are most often grouped together to form phrases. The collocations identified in the Heartitorium corpus are shown below.

![Figure 3](collocation-fig.png)

The Natural Language ToolKit can be used to discover collocations of any length (for instance, three-word phrases) and to filter them by frequency in the given corpus. In the case of Figure 3, the default behavior is used: the 20 most common 2-word collocations from the corpus are printed.

### Random sampling

Due to the infancy of attempts to apply Natural Language Processing to the
Heartitorium, many of the most interesting data points remain those found by
browsing the corpus directly without formal procedure. Several of these are shared below.

## Limitations

[1-2 pages]
[TODO] with the ability to zero in on topics and words, it is easier and more tempting to pursue a specific thesis and fall into confirmation bias. Possibly counteract this by concentrated search for counter-evidence as well.

[TODO] if initial research is conducted from nltk without first browsing the column organically, this is an even greater threat
 

## Findings

[4-6 pages]

[TODO] present the key points you are making in support of your overarching argument, and those points should be backed up with specific evidence (e.g. direct quotes, description, images, and/or narrative) from your observations and participation in the community.
* Kaye encouraged women to practice their autonomy, but still only within a set
  of narrow confines (age, heteronormativity, etc)
https://newspapers.lib.utah.edu/details?id=10188093
if you could get a boy, you'd be with a soldier boy
https://newspapers.lib.utah.edu/details?id=20023455
- girl asks if it's proper to refuse when a boy asks to dance.
Kaye says: as long as you've been properly introduced and he's your age, you're only justified in saying no if there's misconduct on his part
- her defense of movie-going women
-  

https://newspapers.lib.utah.edu/details?id=20023455
Kaye says don't make the mistake of seeming too eager for any man's love

https://newspapers.lib.utah.edu/details?id=10188093
Someone asking Kaye about patriotic movie production companies! Very WSP!
was this a woman?

**Specific Documents**

 
## Conclusion

[1-2 pages]
[TODO] remind the reader of your big argument and help them understand what that argument contributes to our understanding of writing as a social practice. An effective conclusion will answer the so what? question: why does your argument matter? What are the implications for the field? For society?

[TODO] what would heartitorium look like today?
    * maybe Savage Love or Modern Love
    * more woke, i.e. Would the modern version of Heartitorium put a lonely trans girl in touch with a lesbian soldier? Is there an example of a publication like that?
    * cite saga column

Readers and users of texts have as much to do with
a text becoming an instance of a genre as writers do (NWWK 40). This is so the case with Heartitorium

recognizing the intertextual nature of meaning
making is the vital first step toward developing theoretical perspectives
and methodological approaches for tracing the textual connections per-
sons and collectives employ in the continual making and remaking of
knowledge, selves, and societies. (NWWK 46). heartitorium = making and remaking of selves and societies!!


## Disorganized Notes/footnotes

* It's sad that we don't have the original hand-written reader letters. (Were they all hand-written?)
* Ran searches for 'boy' and 'girl'-- why not cars, sports, gambling, poker, alcohol (temperance!)
* Read Flower and Hayes 1981
* Letters are handwritten but they appear in the column typed. Is Kaye *editing* them? i.e. Does she remove mistakes or correct grammar?! That would be very significant to know. Also, how does she choose worthy letters? Is the community small enough to answer 100%?
* Sad footnote: the modern-day "woker" equivalent is probably the letter columns in Brian K Vaughan's comics. Exchanges have appeared about abortion, adultery, trans issues, etc. but I don't think anyone has ever been *set up* by Vaughan
* Did Heartitorium reflect/affect the journalistic practices at the Telegram? When it appeared in the Herald-Republican temporarily, what was that about?
* Some Heartitorium documents are so rich a paper could focus on just one of them.
* NWWK pg 42-43: Writing is multimodal. Talk about how Heartitorium mastheads, and diagrams (even of proper manners) show that
* NWWK pg 43-44: Writing is performative. Are the readers performing for Kaye when they write in? How do they want to come across?
* Has anyone ever written into the Heartitorium **severely** emotional? Mad at Kaye, or having suicidal thoughts? These things happen to modern online communities. Would sentiment analysis be possible on the corpus?
* The Journal of Open Research Software might publish something about the UDN OCR tools if I can open-source them.

* cute writer names like "A BUGLER"... will these be identifiable in the OCR at
  all?
    * A HUNGERING HEART
 
Salt Lake Herald-Republican | 1918-06-23 | The Heartitorium. (n.d.). Retrieved November 5, 2018, from https://newspapers.lib.utah.edu/details?id=10188093

## References


[TODO cite the Heartitorium columns consulted]
Bird, S., Klein, Ewan, & Loper, Edward. (2009). Natural Language Processing with Python (1st ed., Safari Books Online). Beijing; Cambridge [Mass.]: O'Reilly.
Romero, Bree Ann, "Sinners in the City of Saints: Flappers in Salt Lake City" (2014). All Graduate Theses and Dissertations. 3573. https://digitalcommons.usu.edu/etd/3573

[TODO cite UDN api]

