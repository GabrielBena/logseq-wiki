title:: wiki/refs/ba-2016-layer-normalization
category:: reference
type:: external-ref
tags:: normalisation, transformers, deep-learning
authors:: Ba, Jimmy Lei; Kiros, Jamie Ryan; Hinton, Geoffrey E.
year:: 2016
venue:: arXiv preprint
arxiv:: 1607.06450
citation-count:: 12417
summary:: Proposes layer normalisation — computing mean/variance per sample across features rather than across a batch — enabling stable training of RNNs and Transformers.
confidence:: 0.47
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Layer Normalization** — Ba, Kiros & Hinton (2016), arXiv.

- ## Abstract (extracted)
  - Training state-of-the-art, deep neural networks is computationally expensive. One way to reduce the training time is to normalize the activities of the neurons. A recently introduced technique called batch normalization uses the distribution of the summed input to a neuron over a mini-batch of training cases to compute a mean and variance which are then used to normalize the summed input to that neuron on each training case. This significantly reduces the training time in feed-forward neural networks. However, the effect of batch normalization is dependent on the mini-batch size and it is not obvious how to apply it to recurrent neural networks. In this paper, we transpose batch normalization into layer normalization by computing the mean and variance used for normalization from all of the summed inputs to the neurons in a layer on a single training case. Like batch normalization, we also give each neuron its own adaptive bias and gain which are applied after the normalization but before the non-linearity. Unlike batch normalization, layer normalization performs exactly the same computation at training and test times. It is also straightforward to apply to recurrent neural networks by computing the normalization statistics separately at each time step. Layer normalization is very effective at stabilizing the hidden state dynamics in recurrent networks.

- ## Key Ideas
  - Normalise across features (not batch) so each sample is independent — removes batch-size dependency. ^[inferred]
  - Same computation at train and test time; directly applicable to RNNs and Transformers. ^[inferred]
  - Standard component in virtually all modern Transformer architectures. ^[inferred]

- ## Connections to Wiki
  - [[wiki/concepts/topology-masked-transformer]] — layer norm is a standard ingredient in the TMT block used in SODC.
  - [[wiki/research/self-organising-digital-circuits]] — cited as architectural component.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
