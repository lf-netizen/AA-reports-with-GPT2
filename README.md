# Experimenting with GPT-2
A brief attempt to train the Polish version of GPT-2 to generalize and rephrase short fragments of text in a specialized domain.

The goal was to complete the summary of a report given a handful of them, each of them corresponding to the same exercise. It is worth noting that the output of any of the summary models is of very low quality at best. They usually  fail completely.
There are 10 exercises numbered 0-9. Each report contains the following sections: introduction, the description of workstation, the course of excercise and summary. In the dataset there are 35 different documents, which means for one exercise there are 2-5 training samples. Given the limited amount of data, the idea was to slightly overfit during training and make the model creatively combine memorized fragments of text while being able to separate it between excercises.
In order to add the information about excercise number I tried two methods:
* adding a prefix "C{task_number}; "
* replacing each space with task's number. With only a single number occurence with this sample size it is likely for the model to miss the information. I've came up with this technique hoping to establish some sort of  'entanglement' between the text and number in this way.

After training the model for various numbers of epochs and using different decoding methods (beam search, top k, top p, contrastive search), it still couldn't produce satisfactory outputs in terms of both coherence between sentences and coherence with the exercise theme.

This attempt took place shortly before the public release of ChatGPT, which made this experiments obsolete.


### References:
* https://huggingface.co/sdadas/polish-gpt2-medium
* https://huggingface.co/course/chapter7/6?fw=pt
* https://huggingface.co/blog/how-to-generate
* https://huggingface.co/blog/constrained-beam-search