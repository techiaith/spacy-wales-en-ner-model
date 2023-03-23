[English Below](#an-english-named-entity-recognition-model-further-trained-on-entities-specific-to-wales)

# Model adnabod enwau endidau Saesneg a hyfforddwyd ar endidau Cymreig

Mae'r model hwn yn seiliedig ar fodel mawr Saesneg spaCy, ond cafodd ei hyfforddi ymhellach ar frawddegau Saesneg o destunau cyhoeddus Cymreig sy'n cynnwys enwau pobl ac enwau lleoedd sy'n benodol i'r cyd-destun Cymreig.

Yn ein arbrofion cychwynnol, gwelwyd gwelliant o hyd at 10% yng nghywirdeb y model gyda thestunau cyhoeddus Cymreig yn yr iaith Saesneg.

## Gosod
Dilynwch y cyfarwyddiadau yn https://spacy.io/usage er mwyn gosod llyfrgell spaCy.

Llwythwch y fersiwn diweddaraf o'r model o https://github.com/techiaith/spacy-wales-en-ner-model/releases/latest.

Pan fydd wedi lawrlwytho, gosodwch y pecyn drwy ddefnyddio:

`pip install -m enw-ffeil-y-pecyn`

o fewn eich amgylchedd Python.

Gallwch gadarnhau fod y model wedi'i osod drwy deipio:

`python -m spacy info`

## Defnyddio
I ddefnyddio'r model o fewn spaCy:

```
import spacy

nlp = spacy.load("en_core_web_wales_ner_lg")

doc = nlp("The minister, David Jones the member for South Wales East, spoke on behalf of the Welsh Government today in Llandudno.")
for item in [(t, t.lemma_, t.pos_, t.morph, t.ent_type_, t.vector_norm) for t in doc]:
    print (item)
```

Dylai hynny roi'r allbwn canlynol:

```
(The, 'the', 'DET', Definite=Def|PronType=Art, '', 76.91735)
(minister, 'minister', 'NOUN', Number=Sing, '', 54.020626)
(,, ',', 'PUNCT', PunctType=Comm, '', 64.72698)
(David, 'David', 'PROPN', Number=Sing, 'PERSON', 52.474808)
(Jones, 'Jones', 'PROPN', Number=Sing, 'PERSON', 41.571342)
(the, 'the', 'DET', Definite=Def|PronType=Art, '', 72.329216)
(member, 'member', 'NOUN', Number=Sing, '', 58.182625)
(for, 'for', 'ADP', , '', 69.12914)
(South, 'South', 'PROPN', Number=Sing, 'GPE', 66.215164)
(Wales, 'Wales', 'PROPN', Number=Sing, 'GPE', 56.88456)
(East, 'East', 'PROPN', Number=Sing, 'GPE', 73.92659)
(,, ',', 'PUNCT', PunctType=Comm, '', 64.72698)
(spoke, 'speak', 'VERB', Tense=Past|VerbForm=Fin, '', 50.09421)
(on, 'on', 'ADP', , '', 117.34823)
(behalf, 'behalf', 'NOUN', Number=Sing, '', 45.919327)
(of, 'of', 'ADP', , '', 120.9016)
(the, 'the', 'DET', Definite=Def|PronType=Art, 'ORG', 72.329216)
(Welsh, 'Welsh', 'PROPN', Number=Sing, 'ORG', 44.090954)
(Government, 'Government', 'PROPN', Number=Sing, 'ORG', 50.923264)
(today, 'today', 'NOUN', Number=Sing, '', 38.61011)
(in, 'in', 'ADP', , '', 110.41568)
(Llandudno, 'Llandudno', 'PROPN', Number=Sing, 'GPE', 22.266478)
(., '.', 'PUNCT', PunctType=Peri, '', 59.90988)
```

Gallwch hefyd ddefnyddio:

```
from spacy import displacy
displacy.serve(doc, style="ent")
```

i weld delweddiad o'r canlyniadau yn eich porwr yn `localhost:5000`

![image](https://user-images.githubusercontent.com/10194573/227287969-6fb2c9dd-b2aa-421f-ab62-ce87078caa10.png)




# An English named entity recognition model further trained on entities specific to Wales

This model is based on spaCy's large English model, but has been further trained on English sentences from the public sector in Wales which contain names and place-names particular to the Welsh context.

In our initial experiments, we have seen an improvement of up to 10% in the accuracy of the model with English texts from the plubic sector in Wales.

## Installation
Follow the instructions at https://spacy.io/usage to install the spaCy library.

Download the latest version of our model from https://github.com/techiaith/spacy-wales-en-ner-model/releases/latest.

When the download is complete, install the package using:

`pip install -m the-name-of-the-package`

within your Python environment.

You can confirm that the model has been succesfully installed using:

`python -m spacy info`

## Usage
To use the model within spaCy:

```
import spacy

nlp = spacy.load("en_core_web_wales_ner_lg")

doc = nlp("The minister, David Jones the member for South Wales East, spoke on behalf of the Welsh Government today in Llandudno.")
for item in [(t, t.lemma_, t.pos_, t.morph, t.ent_type_, t.vector_norm) for t in doc]:
    print (item)
```

That should produce the following output:

```
(The, 'the', 'DET', Definite=Def|PronType=Art, '', 76.91735)
(minister, 'minister', 'NOUN', Number=Sing, '', 54.020626)
(,, ',', 'PUNCT', PunctType=Comm, '', 64.72698)
(David, 'David', 'PROPN', Number=Sing, 'PERSON', 52.474808)
(Jones, 'Jones', 'PROPN', Number=Sing, 'PERSON', 41.571342)
(the, 'the', 'DET', Definite=Def|PronType=Art, '', 72.329216)
(member, 'member', 'NOUN', Number=Sing, '', 58.182625)
(for, 'for', 'ADP', , '', 69.12914)
(South, 'South', 'PROPN', Number=Sing, 'GPE', 66.215164)
(Wales, 'Wales', 'PROPN', Number=Sing, 'GPE', 56.88456)
(East, 'East', 'PROPN', Number=Sing, 'GPE', 73.92659)
(,, ',', 'PUNCT', PunctType=Comm, '', 64.72698)
(spoke, 'speak', 'VERB', Tense=Past|VerbForm=Fin, '', 50.09421)
(on, 'on', 'ADP', , '', 117.34823)
(behalf, 'behalf', 'NOUN', Number=Sing, '', 45.919327)
(of, 'of', 'ADP', , '', 120.9016)
(the, 'the', 'DET', Definite=Def|PronType=Art, 'ORG', 72.329216)
(Welsh, 'Welsh', 'PROPN', Number=Sing, 'ORG', 44.090954)
(Government, 'Government', 'PROPN', Number=Sing, 'ORG', 50.923264)
(today, 'today', 'NOUN', Number=Sing, '', 38.61011)
(in, 'in', 'ADP', , '', 110.41568)
(Llandudno, 'Llandudno', 'PROPN', Number=Sing, 'GPE', 22.266478)
(., '.', 'PUNCT', PunctType=Peri, '', 59.90988)
```

You can also use:

```
from spacy import displacy
displacy.serve(doc, style="ent")
```

to see a visualization of the entities in your browser at `localhost:5000`

![image](https://user-images.githubusercontent.com/10194573/227287969-6fb2c9dd-b2aa-421f-ab62-ce87078caa10.png)
