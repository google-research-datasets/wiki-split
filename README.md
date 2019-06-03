# WikiSplit Dataset

One million English sentences, each split into two sentences that together
preserve the original meaning, extracted from Wikipedia edits.

http://goo.gl/language/wiki-split

**Update** (3 June 2019): The source code for the evaluations in our paper has been released into a separate repository:
https://github.com/google-research/google-research/tree/master/wiki_split_bleu_eval.

## Description

Google's WikiSplit dataset was constructed automatically from the publicly
available Wikipedia revision history. Although the dataset contains some
inherent noise, it can serve as valuable training data for models that split or
merge sentences.

For further details about the construction of the dataset and its use for model
training, see the accompanying paper:
**[Learning to Split and Rephrase From Wikipedia Edit History](https://arxiv.org/abs/1808.09468)**

If you use or discuss this dataset in your work, please cite our paper:

```
@InProceedings{BothaEtAl2018,
  title = {{Learning To Split and Rephrase From Wikipedia Edit History}},
  author = {Botha, Jan A and Faruqui, Manaal and Alex, John and Baldridge, Jason and Das, Dipanjan},
  booktitle = {Proceedings of the 2018 Conference on Empirical Methods in Natural Language Processing},
  pages = {to appear},
  note = {arXiv preprint arXiv:1808.09468},
  year = {2018}
}
```

## Examples

*   *Due to the hurricane , Lobsterfest has been canceled , making Bob very
    happy about it and he decides to open Bob 's Burgers for customers who were
    planning on going to Lobsterfest .*

    *   *Due to the hurricane , Lobsterfest has been canceled , making Bob
        ecstatic .*
    *   *He decides to open Bob 's Burgers for customers who were planning on
        going to Lobsterfest .*

*   *Her family is rumored to be a large financial clique which controls the
    underworld of Japan , but rarely people know the unhappiness which she
    suffered for being born in such a troublesome family .*

    *   *Her family is rumored to be a large financial clique which controls the
        underworld of Japan .*
    *   *People are unaware of the unhappiness which she suffered for being born
        in such a troublesome family .*

## Data format

The dataset is released as text files formatted as tab-separated values (TSV)
according to the following schema:

Column | Meaning
:-----:| ----------------------------------------------------
1      | unsplit single sentence
2      | split-up sentences, delimited by the string `<::::>`

The sentences have already been tokenized on punctuation.

#### Example data item

```
Due to the hurricane , Lobsterfest has been canceled , making Bob very happy about it and he decides to open Bob 's Burgers for customers who were planning on going to Lobsterfest .	Due to the hurricane , Lobsterfest has been canceled , making Bob ecstatic . <::::> He decides to open Bob 's Burgers for customers who were planning on going to Lobsterfest .
```

## Dataset statistics

Part           | Instances | Tokens*    | Vocabulary*
-------------- | ---------:| ----------:| ----------:
train.tsv      | 989,944   | 33,084,465 | 632,588
tune.tsv       | 5,000     | 167,456    | 25,871
validation.tsv | 5,000     | 166,628    | 25,251
test.tsv       | 5,000     | 167,853    | 25,386

\*counted over the unsplit sentences

## Result on WebSplit 1.0 Benchmark

Our paper introducing the WikiSplit dataset applied it to the split-and-rephrase
task. The main result is that including WikiSplit during model training leads to
improved generalization and dramatically better output on the
[WebSplit](https://github.com/shashiongithub/Split-and-Rephrase) 1.0 test set.

|                                               | Corpus BLEU |
| --------------------------------------------- | -----------:|
| Source (i.e. just echoing the input sentence  | 58.7        |
| Model trained on...                           |             |
| &nbsp;&nbsp;&nbsp;&nbsp; WebSplit only ([Aharoni & Goldberg, 2017](http\://aclweb.org/anthology/P18-2114))   | 30.5
| &nbsp;&nbsp;&nbsp;&nbsp; WebSplit + WikiSplit ([Botha et al., 2018](https\://arxiv.org/pdf/1808.09468.pdf))* | 62.4

See [paper](https://arxiv.org/pdf/1808.09468.pdf) for details.

For the sake of direct comparisons to this work, the evaluation source code is available at:
https://github.com/google-research/google-research/tree/master/wiki_split_bleu_eval.

## License

The WikiSplit dataset is a verbatim copy of certain content from the publicly
available Wikipedia revision history. The dataset is therefore licensed under
[CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/). Any third party
content or data is provided "As Is" without any warranty, express or implied.

## Contact

If you have a technical question regarding the dataset or publication, please
create an issue in this repository.
