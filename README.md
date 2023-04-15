# Detection-of-Persuasion-Techniques-in-Texts-and-Images

Project developed for the [Deep Learning](https://corsidilaurea.uniroma1.it/en/view-course-details/2021/30430/20210916103754/d0d41e8f-68d0-47e4-8ec2-1179259a2a30/dd154448-c5aa-4ef0-a78c-b2cc47ae5898/268eb50b-2dc5-4e5b-81b6-1eb69c3d142b/e1606431-a5e0-4435-aa06-4ff4b4e33b28?guid_cv=dd154448-c5aa-4ef0-a78c-b2cc47ae5898&current_erogata=d0d41e8f-68d0-47e4-8ec2-1179259a2a30) course (Winter 2021). The goal was to deal with the three tasks described in [SemEval 2021 task 6](https://arxiv.org/pdf/2105.09284.pdf) ([here the site](https://propaganda.math.unipd.it/semeval2021task6/)).

If the notebook is not rendered here on GitHub, open it in [Colab](https://drive.google.com/file/d/1L3uekv_FCCyKVtHRUY6NTJ5LZuRM5gc2/view?usp=sharing).

The Detection of Persuasion Techniques in Memes workshop, or SemEval 2021 Task 6, was a challenge aimed at developing NLP models to detect persuasion techniques used in memes. The goal of the workshop was to explore the challenges of detecting these techniques in multimodal content, such as images and text, and to improve the understanding of how persuasive communication is carried out in the digital age. Propaganda uses psychological and rhetorical techniques to reach its purpose. Such techniques include the use of logical fallacies and appealing to the emotions of the audience. Participants were provided with a dataset of annotated memes and were tasked with building NLP models that could detect various persuasion techniques, including rhetorical questions, appeals to authority, and appeals to emotion, among others.

The workshop is divided into three subtasks:
- Subtask 1: The goal is to identify which of the 20 techniques are used in the textual content of a meme, using multilabel classification.
- Subtask 2: The aim is to identify which of the 20 techniques are used in the textual content of a meme, along with the corresponding spans of text, using multilabel sequence tagging. This task combines subtasks 1 and 2 of the SemEval 2020 task 11 on detecting propaganda techniques in news articlesNote that subtask 1 is a simplified version of subtask 2 in which the spans covered by each technique is not supposed to be provided.
- Subtask 3: The objective is to identify which of the 22 techniques are used in both the textual and visual content of a meme, using multilabel classification in a multimodal task.

Subtask 1 and 3 are evaluated using Micro and Macro f1 Score (with Micro f1 considered as the official measure). For Subtask 2, the evaluation requires
matching the text spans. Hence, the organizers of the workshop designed an evaluation function that gives credit to partial matches between gold and predicted spans. A description is given below.
<details>
  <summary>Metric used in subtask 2 </summary>
  (This section is taken directly from the paper)
Let document _d_ be represented as a sequence of characters. The _i-th_ propagandistic text fragment is then represented as a sequence of contiguous characters t ⊆ d. A document includes a set of (possibly overlapping) fragments _T_. Similarly, a learning algorithm produces a set _S_ with fragments s ⊆ d, predicted on _d_. A labeling function l(x) ∈ {1, . . . , 20} associates t ∈ T, s ∈ S with one of the techniques.
We define the following function to handle partial overlaps of fragments with the same labels: $C(s, t, h) = \frac{|(s ∩ t)|}{h} δ (l(s), l(t))$, where _h_ is a normalizing factor and δ(a, b) = 1 if a = b, and 0, otherwise.  Given the previous equation, we now define variants of precision and recall that can account for the imbalance in the corpus: $P(S, T) = \frac{1}{|S|} \sum_{s ∈ S, t ∈ T} C(s, t, |s|)$ (2), and $R(S, T) = \frac{1}{|T|} \sum_{s ∈ S, t ∈ T} C(s, t, |t|)$ (3), where (2) is zero if |S| = 0, and Eq. (3) is zero if |T| = 0.
</details>

During the development of this project, all the rules (submission, evaluation, etc) were followed.

Most of the SOTA techniques submitted for the workshop are implemented in this project, with some variants and also some new approaches.

A more detailed explaination on what was tried during this work is in the Jupyter notebook.
