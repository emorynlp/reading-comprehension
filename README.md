# Reading Comprehension

Reading Comprehension challenges the machine's ability of understanding human conversations.
This is a part of the [Character Mining](../../../character-mining) project led by the [Emory NLP](http://nlp.mathcs.emory.edu) research group.
The following shows a multiparty dialogue where all personal proper nouns are encoded by their entity IDs such as `@ent01`: Joey, `@ent02`: Rachel, `@ent03`: Ross, `@ent04`: Neuman, `@ent05`: Paul, and a plot summary describing this dialogue.

| Speaker | Utterance |
|:-------:|-----------|
| - | [Scene: Central Perk, `@ent01` and `@ent02` are there as `@ent03` enters.] || `@ent03` | Hey! Oh, I’m so glad you guys are here. I’ve been dying to tell someone what happened in the Paleontology department today. 
| `@ent01` | (To `@ent02`) Do you think he saw us or can we still sneak out? || `@ent03` | Professor `@ent04`, the head of the department, so ... || `@ent02` | They made you head of the department! || `@ent03` | No, I get to teach one of his advanced classes! Why didn’t I get head of the department? || `@ent01` | Oh! Hey `@ent02`, listen umm ... || `@ent02` | Yeah. || `@ent01` | I got a big date coming up, do you know a good restaurant? || `@ent02` | Uh, `@ent05`’s Cafe. They got great food and it’s really romantic. || `@ent01` | Ooh, great! Thanks! || `@ent02` | Yeah! Oh, and then afterwards you can take her to the Four Seasons for drinks. Or you go downtown and listen to some jazz. Or dancing - Oh! Take her dancing! || `@ent01` | You sure are naming a lot of ways to postpone xxx, I’ll tell ya ... || `@ent02` | Ooh, I miss dating. Gettin’ all dressed up and going to a fancy restaurant. I’m not gonna be able to do that for so long, and it’s so much fun! I mean not that sitting at home worrying about giving birth to a sixteen pound baby is not fun. || `@ent01` | Hey, y’know what? || `@ent02` | Huh? || `@ent01` | Why don’t I take you out? || `@ent02` | What?! `@ent01`, you don’t want to go on a date with a pregnant lady. || `@ent01` | Yes I do! And we’re gonna go out, we’re gonna have a good time, and take your mind off of childbirth and c-sections and-and giant baby heads stretching out ... || `@ent02` | (interrupting) Okay! I’ll go with ya! I’ll go! I’ll go with ya. || `@ent01` | It’ll be fun. || `@ent02` | All right? |

<p align="center"><code>@placeholder</code> misses dressing up for romantic dates so <code>@ent01</code> promises to take <code>@ent02</code> out.
</p>

Your task is to identify the `@placeholder` in the plot summary by inferring the meaning of the dialogue.
This task is challenging because it needs to match contexts between colloquial (dialog) and formal (summary) writings. 


## Dataset

Personal proper nouns in both dialogues and plot summaries are encoded by their entity IDs.
Note that the entity IDs are consistent within each dialogue but not across different dialogues.
Each query contains exactly one `@placeholder` such that multiple queries can be generated from a plot summary.

* Latest release: [v1.0](https://github.com/emorynlp/reading-comprehension/archive/reading-comprehension-1.0.tar.gz).
* [Release notes](https://github.com/emorynlp/reading-comprehension/releases).

## Statistics

Queries are randomly distributed to the training (TRN), development (DEV), evaluation (TST) sets.

* U / Q: the average number of utterances per query.
* {E} / Q: the average number of entity types per query.
* [E] / Q: the average number of entities per query.
* {E} / U: the average number of entity types per utterance.
* [E] / U: the average number of entities per utterance.

| Dataset | Queries | U / Q | {E} / Q | [E] / Q | {E} / U | [E] / U |
|:-------:|--------:|------:|--------:|--------:|--------:|--------:|
| TRN     | 10,785  | 16.71 | 2.57    | 3.99    | 5.67    | 26.64   |
| DEV     | 1,349   | 16.77 | 2.56    | 3.94    | 5.68    | 26.73   |
| TST     | 1,353   | 16.53 | 2.58    | 4.03    | 5.70    | 26.31   |
| Total   | 13,487  | 16.70 | 2.57    | 3.99    | 5.68    | 26.62   |


## Annotation

Every instance consists of a query and its answer along with the utterances that the query is based on.

```json
{
  "scene_id": "s01_e01_c10",
  "query": "After @ent02 leaves to go out on on a date with a woman whose name he has trouble remembering , @ent00 asks @placeholder ,",
  "answer": "@ent05",
  "utterances": [
    {
      "speakers": "@ent00",
      "tokens": "( scornful ) Grab a spoon . Do you know how long it 's been since I 've grabbed a spoon ? Do the words ' @ent01 , do n't be a hero ' mean anything to you ?"
    },
    {
      "speakers": "@ent02",
      "tokens": "Great story ! But , I uh , I got ta go , I got a date with @ent03 -- @ent04 -- @ent03 ... Oh man , ( looks to @ent05 )"
    },
    {
      "speakers": "@ent05",
      "tokens": "@ent04 's the screamer , @ent03 has cats ."
    },
    {
      "speakers": "@ent02",
      "tokens": "Right . Thanks . It 's June . I 'm outta here . ( Exits . )"
    },
    {
      "speakers": "@ent00",
      "tokens": "Y'know , here 's the thing . Even if I could get it together enough to - to ask a woman out , ... who am I gon na ask ? ( He gazes out of the window . )"
    },
    {
      "speakers": "",
      "tokens": "[ Cut to @ent06 staring out of her window . ]"
    }
  ]
}
```

## Citation

* [Challenging Reading Comprehension on Daily Conversation: Passage Completion on Multiparty Dialog](http://aclweb.org/anthology/N18-1185). Kaixin Ma, Tomasz Jurczyk, and Jinho D. Choi. In Proceedings of the 16th Annual Conference of the North American Chapter of the Association for Computational Linguistics, NAACL'18, 2018 ([poster](https://www.slideshare.net/jchoi7s/challenging-reading-comprehension-on-daily-conversation-passage-completion-on-multiparty-dialog), [source](https://github.com/Mayer123/Multiparty-Dialog-RC)). 


## Contact

* [Jinho D. Choi](http://www.mathcs.emory.edu/~choi).
