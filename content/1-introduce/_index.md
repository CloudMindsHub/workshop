+++
title = "Introduce"
date = 2025
weight = 1
chapter = false
pre = "<b>1. </b>"
+++


In this section, we will explore three main methods for personalizing and optimizing the Amazon Nova language model:

- **Fine-tuning**: Retraining on a labeled dataset tailored for a specific task.
- **Distillation**: Transferring knowledge from a large model (teacher) to a smaller model (student).
- **Continued Pre-training**: Further training the model on a large-scale, unlabeled dataset focused on a specialized domain before fine-tuning.

Each method has distinct characteristics and is suitable for different real-world application requirements.

### Amazon Bedrock

![Fine-tuning illustration](/images/1-introduce/amazon-bedrock.jpg)

To efficiently and quickly implement customization methods such as **Fine-tuning**, **Distillation**, and **Continued Pre-training**, **Amazon Bedrock** is the ideal service.

Amazon Bedrock is a powerful platform that enables you to build and deploy generative AI applications **without managing complex infrastructure**. With Bedrock, you can easily access leading large language models (LLMs) from providers like AI21 Labs, Anthropic, Cohere, Meta, Stability AI, and Amazon, while performing **fine-tuning** directly on your proprietary data.

Through Bedrock, model customization becomes remarkably straightforward:
- No need to build expensive GPU infrastructure.
- Supports model customization with internal data in just a few configuration steps.
- Ensures high security, as training and inference data are protected on AWS.
- Easily integrates into existing applications via simple and robust APIs.

As a result, **Amazon Bedrock** reduces development time, lowers operational costs, and increases flexibility when deploying specialized AI solutions tailored to specific business needs.

#### Fine-tuning

**Concept:**
Fine-tuning is the process of retraining a pre-trained language model on a specialized, labeled dataset. This process adjusts the model’s parameters to optimize performance for a specific task or domain, enabling the model to adapt to the context and nuances of the application domain.

**Advantages:**
- Significantly improves performance on specialized tasks compared to the original model.
- Saves computational resources as it does not require training from scratch.
- Requires less data than pre-training (typically thousands to hundreds of thousands of samples).
- Shorter training time, ranging from a few hours to a few days, depending on model scale.
- Flexible for adapting to various tasks.

**Disadvantages:**
- High risk of overfitting if the dataset is too small or lacks diversity.
- Catastrophic forgetting: May lose general knowledge from the original model.
- Imbalanced performance across different tasks.

**Real-world Use Cases:**
1. Customer service chatbots: Fine-tune to understand company policies, products, and communication style, improving accuracy in responses aligned with internal processes.
2. Specialized text classification systems: For example, classifying organization-specific spam emails or categorizing legal documents into specific categories.
3. Healthcare: Fine-tune the model for Medical Named Entity Recognition (NER) in patient records, enhancing the extraction of information about diseases, medications, and diagnoses.

#### Distillation

**Concept:**
Distillation (model distillation) is a technique for transferring knowledge from a large, complex model (teacher model) to a smaller, lighter model (student model). This method uses the probability distribution outputs from the teacher model to train the student model, enabling the smaller model to mimic the capabilities of the larger one.

**Advantages:**
- Significantly reduces model size (by 50-90% of parameters).
- Increases inference speed and reduces latency.
- Lowers memory and energy requirements during deployment.
- Preserves much of the original model’s capabilities in a more compact architecture.
- Enables deployment on resource-constrained devices like smartphones or IoT devices.

**Disadvantages:**
- Reduced performance compared to the original teacher model, especially on complex tasks.
- Requires a more complex training process, needing optimization of multiple hyperparameters.
- Requires balancing size and performance for optimal results.
- Depends on the quality of the teacher model and transfer data.

**Real-world Use Cases:**
1. Virtual assistants on mobile devices: Create a lightweight version of a chat model to run directly on smartphones, reducing latency and enhancing privacy.
2. Smart home systems: Deploy compact models on IoT devices for natural language processing and decision-making without cloud connectivity.

#### Continued Pre-training

**Concept:**
Continued Pre-training is the process of further training a pre-trained large language model on a new, unlabeled dataset, typically specialized for a specific domain. This method helps the model absorb additional domain-specific knowledge before fine-tuning for specific tasks.

**Advantages:**
- Expands the model’s domain-specific knowledge.
- Significantly improves performance when combined with subsequent fine-tuning.
- Enhances generalization when processing new data.
- Reduces catastrophic forgetting compared to fine-tuning alone.
- Highly effective for specialized domains like healthcare, law, or finance.

**Disadvantages:**
- Requires significant computational resources, often needing powerful GPUs/TPUs and extended time.
- Demands large, high-quality datasets from the target domain.
- Complex training process, difficult to optimize and monitor.
- Risk of bias in training data if not carefully filtered.
- High costs for both data and computational resources.

**Real-world Use Cases:**
1. Healthcare: Continue pre-training on medical datasets (e.g., millions of PUBMED articles, patient records) before fine-tuning for diagnosis or treatment consultation.
2. Finance: Train on financial reports, economic news, and market data before fine-tuning for investment analysis or market forecasting.
3. Legal: Pre-train on legal texts, case law, and documents before fine-tuning for contract drafting or analysis systems.
4. Scientific research: Continue training on a corpus of scientific papers in a specific field before fine-tuning for information extraction or research summarization.

### Comparison of Model Customization Techniques

| Criteria | Fine-tuning | Distillation | Continued Pre-training |
|----------|-------------|--------------|------------------------|
| **Input Data Type** | Labeled, task-specific | Labeled and teacher model predictions | Unlabeled, domain-specific |
| **Data Volume Required** | Thousands to hundreds of thousands of samples | Moderate, task-dependent | Large (millions of texts) |
| **Training Time** | Hours to days | Moderate | Days to weeks |
| **Primary Goal** | Optimize for specific tasks | Reduce size, speed up inference | Add domain-specific knowledge |
| **Computational Resource Needs** | Moderate | Low to moderate | Very high |
| **Implementation Complexity** | Simple | Moderate | Complex |
| **Scalability** | Limited to trained tasks | Good for large-scale deployment | Flexible for subsequent tasks |
| **Overfitting Risk** | High with limited data | Low to moderate | Low |
| **Impact on Original Knowledge** | May lose general knowledge | Preserves much of it | Expands and supplements |
| **Operational Cost** | Low to moderate | Very low | High |
| **Suitable For** | Specific tasks with labeled data | Resource-constrained environments | Specialized, complex domains |
| **Evaluation Method** | Task-specific metrics | Comparison with teacher model | Perplexity and downstream **downstream evaluation** |

Each method for customizing the Amazon Nova model plays a unique role in adapting large language models to real-world applications:

- **Fine-tuning**: Ideal when precise responses are needed for a specific task, especially with high-quality labeled data.
- **Distillation**: Efficient for deploying models on resource-constrained devices, prioritizing response speed and cost-efficiency.
- **Continued Pre-training**: Suitable for achieving deep understanding of a specific domain, particularly in fields like healthcare, law, or finance.

The choice and combination of these methods depend on specific performance requirements, available resources, and application characteristics.

{{% notice info %}}
Since **Distillation** on AWS Bedrock is in preview, and **Continued Pre-training** is complex and costly, **Fine-tuning** is a more popular choice for real-world business use cases. After testing the Nova Lite model, we found that it underperforms on Vietnamese image-based question-answering tasks. Therefore, within the scope of this workshop, we will fine-tune the model using a Vietnamese image-based question-answering dataset.
{{% /notice %}}