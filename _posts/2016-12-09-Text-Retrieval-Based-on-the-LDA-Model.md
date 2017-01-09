---
layout: post
title: Text Retrieval Based on the LDA Model
#tags: [Project]
---

Topic models like Latent Dirichlet Allocation have been widely applied
to different fields. However, even text retrieval is naturally related
to latent topics of a corpus, the application of the LDA model in this
field is still novel. In this paper, I try to study how to use the LDA
model to retrieve relevant documents for a given query. I propose a text
retrieval system based on the LDA model, and test the accuracy and
efficiency of the system on TREC Ad Hoc 8 collection. The experiment
shows that text retrieval based on the LDA model is helpful and doable.\
\
*Keywords:* latent dirichlet allocation, text retrieval, topic modeling

 Introduction
==============

Text retrieval is a branch of information retrieval but the information
is stored primarily in the form of text. It has become increasingly
critical today, since it is the fundamental basis of all internet search
engines. In previous researches, documents are typically represented by
the “bag-of-words” model, which assumes the order of every word in a
document is exchangeable. This model enables researchers to reduce each
document to a vector of counts of words, and process a corpus as a large
sparse matrix[@lda].\
\
Modeling large corpus has been studied since the introduction of
*tf-idf* scheme [@tfidf]. After that, information retrieval (IR)
researchers have proposed several notable techniques like Latent
Semantic Indexing probabilistic Latent Semantic Indexing(pLSI). These
models aim to reduce dimensions of corpus and represent documents by
latent “topics". Recently, Latent Dirichlet Allocation (LDA)[@lda] has
become the most popular model in machine learning community. LDA is
similar to pLSI, but it is basically a Bayesian version of pLSI because
it assumes the topic has a Dirichlet prior distribution. Thus topics
inferred by LDA are more interpretable than pLSI. Since the LDA model is
highly extendable, many LDA-based models such as *supervised topic
modeling*[@slda] and *correlated topic models*[@ctm] have been proposed
to the present.\
\
The LDA model has been cited and applied extendedly in text-based fields
including bioinformatics, document clustering, web mining and spam
detection. However, application of LDA in IR field is still novel.
Therefore, I propose a LDA-based model to retrieval text in this paper.
Section 2 introduces related work of the LDA-based model, and the Ad Hoc
test collection 8 from Text REtrieval Conference (TREC). I explain the
LDA-based retrieval model in Section 3. Section 4 shows the experiments
and results of the LDA-based retrieval model on TREC Ad Hoc test
collection 8. Conclusion and further work are given and discussed in
Section 5.

 Related Work
==============

Latent Dirichlet Allocation
---------------------------

Blei, Ng and Jordan (2003) proposed a widely used topic model in natural
language processing, latent dirichlet allocation (LDA). LDA is a
three-level hierarchical Bayesian model capable of automatically
discovering latent topics of documents in a corpus. LDA uses a
generative model to explain how the observed words in documents of a
corpus are generated from the topic (latent variables). The following
graph shows the graphical model representation of LDA:\

![The graphic model of LDA[]{data-label="Figure1"}](LDA.png)

The Figure 2.1 is “plates” representing LDA. The outer plate represents
documents, while the inner plate represents the repeated choices of
topics and words within a document. M denotes the number of documents of
the corpus, N is the number of words in a document, and V indicates the
vocabulary size of the corpus. Blei and Ng define the following terms:

-   $\alpha$ is the parameter of the Dirichlet prior of the per-document
    topic distribution.

-   $\beta_i$ is the word distribution for topic $z$.

-   $\theta_m$ is the topic distribution for document $m$.

-   $z_{mw}$ is the topic of word w in document $m$.

LDA assumes the following generative process for each document $m$ in a
corpus:

-   Choose $N\sim Poisson\left( \xi  \right)$.

-   Choose $\theta \sim Dir\left( \alpha  \right)$.

-   For each word $w_n$ : Choose a topic
    $z_n \sim Multinomial \left( \theta  \right)$. Choose a word
    $w_n \sim Multinomial \left( z_n  \right)$.

Based on variation inference or Gibbs sampling, the LDA model is widely
implemented for information retrieval, classification and summarization.
In addition, Blei has proposed correlated topic models[@ctm] and
supervised topic models[@slda], which are direct extensions of the
original LDA model.

 Text REtrieval Conference: Ad Hoc Test Collection
---------------------------------------------------

While LDA has been utilized and extended to different fields, its
application in text retrieval is still novel. The Text REtrieval
Conference (TREC) provides large test collections to promote progress on
text retrieval[@trec].\
\
The Text REtrieval Conference is co-sponsored by the National Institute
of Standards and Technology (NIST) and the U.S. Department of Defense,
and was started in 1992. The basic goal of TREC is to help researchers
develop better text retrieval systems and encourage communication among
text retrieval researchers \[4\]. During the last 25 years, the number
of participants has increased, and the retrieval tasks and data
collection have been optimized.\
\
Every TREC conference has two tasks: the routing task and the ad hoc
task. The ad hoc task provides roughly 2 Gigabytes of documents, 50 new
topics (queries) and relevant judgments that either are relevant or not
for each topic-document pair. Documents are tagged by different sections
and researchers can easily parse them by programming. Fig.1 shows a
document in TREC Ad Hoc 8 collection. A typical topic (See Fig.2)
contains 3 parts: topic title, description and narrative. Its length is
usually longer than a real query. However, the length maintains the
clarity of topics.\

![A document extracted from TREC Ad Hoc 8
collection[]{data-label="Figure2"}](trecdoc.png){width="100.00000%"}

![A sample topic extracted from TREC Ad Hoc 8
collection[]{data-label="Figure3"}](trectopic.png){width="100.00000%"}

Different retrieval systems can be trained on the corpus and topics
(queries), and evaluated on the relevant judgments. 8 TREC Ad Hoc
collections have been used and archived to the present, and TREC Ad Hoc
collection 8 might be the best subcollection to use in text retrieval
evaluation because it is the largest test collection and the topics are
more consistent \[5\]. The documents in TREC Ad Hoc 8 are collected from
4 different sources: The Federal Register, The Financial Times, The LA
Times and The Foreign Broadcast Information Service, and the relevant
judgment of each topic-document pair is assumed to be complete. My task
is to retrieve relevent documents for any given query.

LDA based Text Retrieval
========================

A text retrieval system has two main tasks: finding relevant documents
for users by matching their queries and evaluating and sorting the
matching results according to relevance. This section mainly illustrates
how to retrieve documents relevant to a given query. To simplify the
retrieval process, I assume given a query I would know several relevent
and non-relevent documents before I retrieve more documents from the
whole corpus.\
\
To effectively apply topic modeling to corpus, the first step is to
clean corpus and represent documents by vector of words. Naturally,
there are punctuations, capitalized letters, numbers, and commons words
such as *the*, *a*, *and* in an English article, but we commonly remove
them, because they are basically nosies in natural language processing
techniques. Meanwhile, a word might be in different forms in a document.
For instance, *math*, *mathematics*, *mathematical* share similar
meaning, and treating them as a single token *math* would be more
informative and useful in topic modeling. *Stemming* process reduces
words to their root. Moreover, using n-gram model on corpus would
increase accuracy of topic modeling because n-gram is more likely to
capture more topic-related phrases than single word.\
\
The process of retrieve relevant documents is as follows:

-   Tokenize, remove stop words and stem every document in the corpus.

-   Process bi-gramming on every document, and remain bi-grams which are
    statistically significant in the corpus.

-   Perform the LDA model to detect latent topics of documents.

-   Predict if a document is relevent to the given query based on the
    similarity of distribution of latent topics between the document and
    the known relevant and non-relevent documents.

-   Return predicted relevent documents.

 Experiments and Results
========================

Data
----

I conducted text retrieval experiment on 3000 sample documents from TREC
Ad Hoc 8 collection with 10 queries from topic 401-450 , because
bigramming and fit the LDA model on a sample corpus are considerably
less time consuming than the whole TREC Ad Hoc 8 collection. The whole
corpus, queries and relevent judgements are same as participants used in
TREC. Therefore, I can easily extend the experiment on the whole TREC Ad
Hoc 8 collection, and compare the result with other participants’ in the
next step.\
\
Since relevent judgment for each query-document pair is available, each
time I tried to experiment on a query, I randomly split the relevent
documents into training set and test set, and training set accounts 10%
of all relevent documents.

Retrieval
---------

After mixing all relevent documents with sample documents, cleaning and
bigramming the corpus, I fit the LDA model on the corpus. In this
experiment, the *correlated topic model* (CTM) generally preformed
better than the original LDA model, because the query usually contains
several related topics, and CTM is capable of capturing correlated
latent topics. Tuning the number of latent topics by cross validation, I
found setting $k=30$ would be the best choice here.\
\
CTM model returned the topic distribution for each document in the
corpus. Given the training set, I could measure which document in the
rest documents is similar to the training set, which means the document
is relevent to the query. To measure the similarity, I used *Support
Vector Machine* (SVM) to classify the documents in the test set. SVM is
a powerful algorithm to classify linear or non-linear data [@svm].

Result
------

For each query, I ran 10 folds cross validation on relevant documents,
and recorded the average *precision* and *recall* rate as in Table 4.1.
The retrieval results of different queries are generally stable and
consistent. Most average precisions are around 0.3 to 0.4, and the best
average precision is 0.4144. recalls are around 0.4 to 0.5. With regard
to recall, the average recalls basically range from 0.4 to 0.5, and the
best average recall is 0.5337.\

                precision   recall
  ----------- ----------- --------
    query 434      0.4144   0.3335
    query 401      0.3209   0.5244
    query 450      0.3597   0.4155
    query 439      0.3040   0.5337
    query 426      0.3581   0.4873
    query 436      0.3353   0.5060
    query 438      0.2985   0.5091
    query 424      0.3562   0.5300
    query 425      0.3814   0.4824
    query 446      0.3307   0.5120

  : Average Precision and Recall rate of the 10 queries

 Conclusion and Future Work
============================

Comparing with previous TREC results[@trec] (shown in Figure 4.1), the
LDA based retrieval model is acceptable and doable. Obviously, the LDA
model is a feasible and promising algorithm to improve text retrieval
system. Topic modeling can help retrieval system better identify
relevant documents based on inference of latent topic within a corpus.

![Recall-precision graph for ad hoc
retrieval[]{data-label="Figure1"}](trecresult.png)

The LDA model has many attractive features; however, applying it in a
large corpus like the whole TREC Ad Hoc 8 collections seems challenging.
In my experiment, I merely bigrammed and fit CTM model on 3000
documents, because as corpus size increases, bigramming and fitting CTM
model on larger corpus become essentially time comsuming. Using a cloud
server and parallelizing the process might be necessary to apply the LDA
model to real-world dataset. Moreover, I assumed that I knew part of
relevent documents given the query, and tried to find other relevent
documents based on the known relevent documents. In real text retrieval
system, given a new query, I might not know any relevent document.
Identifying the most relevent documents would be the first problem for
this test retrieval system.\
\
For future work, I would enlarge the size of corpus in my retrieval
experiment; meanwhile, expedite bigramming and LDA fitting process by
using Spark[@ldaspark] on cloud. In addition, query likelihood
model[@ldabased] might be a possible way to identify most relevent
documents as training set for LDA-based text retrieval system.

[9]{}

Blei, David M., Andrew Y. Ng, and Michael I. Jordan. “Latent dirichlet
allocation.” *Journal of machine Learning research* 3.Jan (2003):
993-1022.

Salton, Gerard, and Michael J. McGill. “Introduction to modern
information retrieval.” (1986).

Mcauliffe, Jon D., and David M. Blei. “Supervised topic models.”
*Advances in neural information processing systems*. 2008.

Blei, David, and John Lafferty. “Correlated topic models.” *Advances in
neural information processing systems* 18 (2006): 147.

Voorhees, Ellen M., and Donna Harman. “Overview of the sixth text
retrieval conference (TREC-6).”  *Information Processing &
Management* 36.1 (2000): 3-35.

Blair, David C., and Melvin E. Maron. “An evaluation of retrieval
effectiveness for a full-text document-retrieval system.”
*Communications of the ACM* 28.3 (1985): 289-299.

Latent Dirichlet allocation on Spark:\
*http://spark.apache.org/docs/latest/mllib-clustering.html\#latent-dirichlet-allocation-lda*

Wei, Xing, and W. Bruce Croft. “LDA-based document models for ad-hoc
retrieval.” Proceedings of the 29th annual international ACM SIGIR
conference on Research and development in information retrieval. ACM,
2006.

Manning, Christopher, et al. *Introduction to Information Retrieval,
Cambridge University Press*. 2008.

Tong, Simon, and Daphne Koller. “Support vector machine active learning
with applications to text classification.” *Journal of machine learning
research* 2.Nov (2001): 45-66.
