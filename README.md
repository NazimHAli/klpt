# Kurdish Language Processing Toolkit

<p align="center" width="100%">
    <img width="33%" src="https://raw.githubusercontent.com/sinaahmadi/klpt/master/docs/img/KLPT_logo.png"> 
</p>

### Welcome / *Hûn bi xêr hatin* / بە خێر بێن! 🙂

Kurdish Language Processing Toolkit--KLPT is a [natural language processing](https://en.wikipedia.org/wiki/Natural_language_processing) (NLP) toolkit in Python for the [Kurdish language](https://en.wikipedia.org/wiki/Kurdish_languages). The current version comes with four core modules, namely `preprocess`, `stem`, `transliterate` and `tokenize` and addresses basic language processing tasks such as text preprocessing, stemming, tokenization, spell-checking and morphological analysis for the [Sorani](https://en.wikipedia.org/wiki/Sorani) and the [Kurmanji](https://en.wikipedia.org/wiki/Kurmanji) dialects of Kurdish.

## Install

```bash
pip install klpt
```

## Usage

Examples using a combination of scripts with target and source languages.

#### Preprocess

[Usage reference](https://sinaahmadi.github.io/klpt/user-guide/preprocess/)

```python
from klpt.preprocess import Preprocess

preprocessor_ckb = Preprocess("Sorani", "Arabic", numeral="Latin")
preprocessor_ckb.normalize("لە ســـاڵەکانی ١٩٥٠دا")
'لە ساڵەکانی 1950دا'
preprocessor_ckb.standardize("راستە لەو ووڵاتەدا")
'ڕاستە لەو وڵاتەدا'
preprocessor_ckb.unify_numerals("٢٠٢٠")
'2020'
preprocessor_ckb.preprocess("راستە لە ووڵاتەی ٢٣هەمدا")
'ڕاستە لە وڵاتەی 23هەمدا'
```

#### Tokenize

[Usage reference](https://sinaahmadi.github.io/klpt/user-guide/tokenize/)

```python
from klpt.tokenize import Tokenize

tokenizer = Tokenize("Kurmanji", "Latin")
tokenizer.word_tokenize("ji bo fortê xwe avêtin")
['▁ji▁', 'bo', '▁▁fortê‒xwe‒avêtin▁▁']
tokenizer.mwe_tokenize("bi serokê hukûmeta herêma Kurdistanê Prof. Salih re saz kir.")
'bi serokê hukûmeta herêma Kurdistanê Prof . Salih re saz kir .'
```

#### Transliteration

[Usage reference](https://sinaahmadi.github.io/klpt/user-guide/transliterate/)

```python
from klpt.transliterate import Transliterate
transliterate = Transliterate("Kurmanji", "Latin", target_script="Arabic")
transliterate.transliterate("rojhilata navîn")
'رۆژهلاتا ناڤین'
```

#### Stem

[Usage reference](https://sinaahmadi.github.io/klpt/user-guide/stem/)

Spelling

```python
from klpt.stem import Stem

stemmer = Stem("Sorani", "Arabic")
stemmer.check_spelling("سوتاندبووت")
False
stemmer.correct_spelling("سوتاندبووت")
(False, ['ستاندبووت', 'سووتاندبووت', 'سووڕاندبووت', 'ڕووتاندبووت', 'فەوتاندبووت', 'بووژاندبووت'])
```

Analyze

```python
from klpt.stem import Stem

stemmer = Stem("Sorani", "Arabic")
stemmer.analyze("دیتبامن")
[{'pos': ['verb'], 'description': 'past_stem_transitive_active', 'stem': 'دی', 'lemma': ['دیتن'], 'base': 'دیت', 'prefixes': '', 'suffixes': 'بامن'}]
```

Stem

```python
from klpt.stem import Stem

stemmer = Stem("Sorani", "Arabic")
stemmer.stem("دەچینەوە")
['چ']
stemmer.stem("گورەکە", mark_unknown=True) # گوڵەکە in Hewlêrî dialect
['_گور_']
```

Lemmatize

```python
from klpt.stem import Stem

stemmer = Stem("Sorani", "Arabic")
stemmer.lemmatize("گوڵەکانم")
['گوڵ', 'گوڵە']
```

## Become a sponsor 

Please consider donating to the project. Data annotation and resource creation requires tremendous amount of time and linguistic expertise. Even a trivial donation will make a difference. You can do so by [becoming a sponsor](https://github.com/sponsors/sinaahmadi) to accompany me in this journey and help the Kurdish language have a better place within other natural languages on the Web. Depending on your support,

- You can be an official sponsor
- You will get a GitHub sponsor badge on your profile
- If you have any questions, I will focus on it
- If you want, I will add your name or company logo on the front page of your preferred project
- Your contribution will be acknowledged in one of my future papers in a field of your choice

*And, thanks for those who have already sponsored this project. More significant achievements will be made thanks to you!*

## Contribute

Are you interested in this project? Each task is addressed individually. Please check the following repositories to find which one you are more interested in:

- [Kurdish tokenization](https://github.com/sinaahmadi/KurdishTokenization)
- [Kurdish Hunspell](https://github.com/sinaahmadi/KurdishHunspell)
- [Kurdish transliteration](https://github.com/sinaahmadi/wergor)

In addition, our main objective is to extend the current toolkit to include more tasks, particularly part-of-speech tagging, named-entity recognition and syntactic analysis. Further instructions are provided at [https://sinaahmadi.github.io/klpt/about/contributing/](https://sinaahmadi.github.io/klpt/about/contributing/). You can also join us on [Gitter](https://gitter.im/KurdishNLP/community).

Don't forget, **open-source is fun!** 😊

## Cite this project
Please consider citing [this paper](https://sinaahmadi.github.io/docs/articles/ahmadi2020klpt.pdf), if you use any part of the data or the tool ([`bib` file](https://sinaahmadi.github.io/bibliography/ahmadi2020klpt.txt)):

    @inproceedings{ahmadi2020klpt,
        title = "{KLPT--Kurdish Language Processing Toolkit}",
        author = "Ahmadi, Sina",
        booktitle = "Proceedings of the second Workshop for {NLP} Open Source Software ({NLP}-{OSS})",
        month = nov,
        year = "2020",
        publisher = "Association for Computational Linguistics"
    }
