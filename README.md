# quotation-detection
Detection of quotations in a text from RIQUA corpus

We use the RiQuA dataset, which consists of:
• Percentage of quotation labelled words in the entire text: 33.94 % • Percentage of entity labelled words in the entire text: 1.67 %
• Percentage of cue labelled words in the entire text: 0.89 %

To tokenize using BERT tokenizer we need to convert our text in BERT supported input - CONLL for- mat :
• Assigned each token a tag denoting whether it is the beginning of a span, inside a span, or outside to get the supported format. Like shown in Figure 1, we formatted our data such that the beginning and intermediate quotation words are marked with prefix B- and I- respectively. Similarly the cue and entity words are also converted. The unlabelled words are annotated as O.
<br/>
• Text is passed into a pretrained BERT model sentence by sentence, and the hidden states of the final layers are summed and saved as a contextualized embedding for each token.
<br/>
• These embeddings, paired with the labels, are then used for supervised learning methods such as K Nearest Neighbors and Logistic Regression, and Naive Bayes. We also fine-tuned the pre-trained BERT model designed for token classification on our data directly to utilize the model for classification.

<br/>
• One example of Annotation can be seen below:

<img width="826" alt="Screen Shot 2023-03-07 at 10 10 03 PM" src="https://user-images.githubusercontent.com/114776023/223610033-87df400d-ed5a-472e-8771-c78213d7e5c3.png" title="hello">

<img width="774" alt="Screen Shot 2023-03-07 at 10 32 43 PM" src="https://user-images.githubusercontent.com/114776023/223612930-0462963d-e16f-4856-b375-ebad2640433f.png">

<img width="804" alt="Screen Shot 2023-03-07 at 10 33 39 PM" src="https://user-images.githubusercontent.com/114776023/223613006-f6bf8727-7a2b-4f16-b3b1-0ab766955c48.png">

<img width="954" alt="Screen Shot 2023-03-07 at 10 34 26 PM" src="https://user-images.githubusercontent.com/114776023/223613094-8f312dd7-5945-4e60-bd82-31a18bc8255d.png">


## Conclusion and Discussion:
<br/>
Overall, our results are in line with expectations, with the baseline performing the worst by far, and the finetuned model performing the best. The vast gap in performance between the baseline and even simple models like KNN illustrates the need for context in a task like quotation detection. Logistic Regression is able to perform fairly well, which makes sense since it is similar to adding a fully-connected layer on top of a pretrained BERT model with frozen weights. Still, this is an encouraging result, showing that it is possible to achieve markedly increased performance over the baselines without changing any weights in the BERT model, requiring fewer computational resources than a full finetune.

## References
<br/>
[1] Tom B. Brown, Benjamin Mann, Nick Ryder, Melanie Subbiah, Jared Kaplan, Prafulla Dhariwal, Arvind Neelakantan, Pranav Shyam, Girish Sastry, Amanda Askell, Sandhini Agarwal, Ariel Herbert-Voss, Gretchen Krueger, Tom Henighan, Rewon Child, Aditya Ramesh, Daniel M. Ziegler, Jeffrey Wu, Clemens Winter, Christopher Hesse, Mark Chen, Eric Sigler, Mateusz Litwin, Scott Gray, Benjamin Chess, Jack Clark, Christopher Berner, Sam McCandlish, Alec Radford, Ilya Sutskever, and Dario Amodei. Language models are few-shot learners, 2020.
<br/>
<br/>
[2] Yue Chen, Zhen-Hua Ling, and Qing-Feng Liu. A Neural-Network-Based Approach to Identifying Speak- ers in Novels. In Interspeech 2021, pages 4114–4118. ISCA, August 2021.





