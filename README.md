# LLM Data Engineer
This repository is dedicated to research and education of evaluating and leveraging Large Language Models (LLMs) in the discipline of data engineering.

Data engineering serves as the foundation for all data science initiatives, including projects involving LLMs. It encompasses the design and implementation of systems to collect, store, and process data through ETL pipelines, ensuring accessibility and integrity throughout the analytical lifecycle (Jain). 

Data engineering is complex and time-consuming, involving the meticulous design, deployment and maintenance of data pipelines, ETL processes, and storage solutions. It requires expertise in handling vast datasets, ensuring data quality, and integrating tools, all while addressing scalability, security, and performance challenges to support efficient data science workflows. 

Transforming industries through their advanced capabilities, LLMs are reshaping fields such as healthcare, finance, and education. From powering personalized tutoring systems to enhancing diagnostic tools with natural language understanding, LLMs streamline workflows, improve accessibility, and generate innovative solutions. Their adaptability continues to redefine the potential of AI applications. 

This momentum has also driven transformative research aimed at redefining data science, the field from which LLMs emerged. Researchers are investigating how LLMs can not only enhance traditional data analysis and predictive modeling but also address practical challenges associated with integrating LLMs into data science workflows. 

The limited research on data engineering has inspired this study, which seeks to evaluate how well LLMs, without fine-tuning, understand data engineering concepts and perform practical tasks in real-world scenarios. In a rapidly evolving field, this work aims to provide valuable insights for data engineering professionals—typically early adopters of new technologies —on the impact of LLMs on their careers and future development. 

In the Internet Technology and the newly emerging data field, oftentimes the actual application of workload toils in the cloud. Although it is optional, recognition with the pertaining certificate by the cloud providers is compelling proof for professionalism. Therefore, in this section we test LLMs with publicly available data engineering exam questions. Being agnostic with cloud providers, we collected exam questions for the three prevalent cloud providers: Azure, Google Cloud Platform (GCP), and Amazon Web Services (AWS). Our rule is that if the cloud providers offer official sample questions with solutions (like Azure and GCP) we implement them. Otherwise for AWS we resort to freely available sample questions and solutions from the third parties, where we combined sample questions and solutions from two sources. 

These certificate exams are steppingstones into this profession. Professionals are tested for their knowledge and skills in engineering ETL pipelines using cloud resources. LLMs have passed numerous professional examinations, for example the Law School Admission Test and the Uniform Bar Examination in law, the United States Medical Licensing Exam in medicine, the Scholastic Aptitude Test and the Graduate Record Examination in colleges, the Advanced Placement in literature. This study tested the major foundation LLMs with publicly available exams to analyze their strengths and weaknesses on this topic without fine-tuning. 

Specifically, this study evaluates the performance of four language models—gpt-4o-mini, gpt-4o, llama3.1-8b, and llama3.1-405b—on four certification exams: AWS, GCP, Azure DP-900, and Azure DP-203. Each exam consists of a specific number of questions. 

For this experiment, we purchased credit from OpenAI for the usage of API for model gpt-4o and gpt-4o-mini. In the API calls, the system message as in the prompt notifies what the model should do with the user input that follows the system message in the prompt. 

Exam questions can be found in the folder [examQuestions](examQuestions/).

As you would see in the later section that this experiment runs against 190 questions, the framework library Langchain is employed to prompt the model by programmatically hitting the API looping through all the questions. 

It is well known that LLMs output unstructured texts, occasionally even specifically informed about the format. For this reason, we use the method with_structured_output with predefined schema for the output. As supported by Langchain, this works very well with OpenAI GPT models. 

However, unfortunately, Langchain does not integrate with Llama models. We use the SDK offered by llamaapi.com for llama models. At signup, the website offers free credit, which is adequate for the running of this experiment. In this framework, functions calls are used as the structuring tools. However, it does not work with confidence. The expected results can appear in various locations of the returned object. We had to manually pick the answer from the returned objects where the extraction or formatting failed.

In Table 1, the models' performance is presented as both percentages and the number of correct answers. The results highlight the comparative strengths and weaknesses of the models in handling domain-specific challenges.

|| AWS (71) | GCP (19) | Azure 900 (50) | Azure 203 (50) |
|---|---|---|---|---|
|gpt-4o-mini|76% (54)|84.2% (16)|82% (41)|72% (36)|
|gpt-4o|84.5% (60)|89.5% (17)|86% (43)|80% (40)|
|llama3.1-8b|49.3% (35)|78.9% (15)|80% (40)|56% (28)|
|llama3.1-405b|71.8% (51)|78.9% (15)|82% (41)|70% (35)|

Exam-wise, gpt-4o consistently outperforms the other models, achieving the highest scores across all exams. For example, it leads with 84.5% accuracy on the AWS exam, where the performance gap between models is most pronounced, and secures the top position in the GCP and Azure 900 and 203 exams. 

In contrast, llama3.1-8b records the lowest performance in three out of four exams, particularly struggling on the AWS and Azure 203 tests. Meanwhile, gpt-4o-mini and llama3.1-405b exhibit more moderate performance, often achieving comparable results, though they remain consistently behind gpt-4o. 

A model-wise analysis reveals that gpt-4o demonstrates a clear advantage in versatility and domain adaptability, with scores ranging from 80% to 89.5%. Although gpt-4o-mini occasionally approaches its performance, its variability is more pronounced, particularly with a drop to 72% on the Azure 203 exam. llama3.1-405b shows less consistent results but is competitive with gpt-4o-mini in certain scenarios. The relatively poor performance of llama3.1-8b suggests that smaller model sizes may struggle with the complexity or domain specificity of these tasks. 

These findings suggest that larger, more robust models like gpt-4o are better equipped to handle diverse certification domains, reflecting greater generalization and adaptability. The significant performance gaps on certain exams, such as AWS, indicate potential challenges in domain-specific knowledge representation and reasoning for smaller models like llama3.1-8b. This analysis underscores the importance of scale and specialized tuning in achieving state-of-the-art results in domain-specific applications. 

The Azure exams provide a means to compare how the model performs at two different difficulty levels. Azure DP-900 focuses on data engineering concepts, which is more factual. Whereas Azure DP-203 involves more challenges in real life data engineering tasks, which involves more reasoning. All models demonstrate that they perform better in the factual questions than questions involving reasoning. Between the models, the performance differs more greatly in simple models gpt-4o-mini and gpt-4o than in advanced models llama3.1-8b and llama3.1-405b. Between model families, GPT models are more stable than Llama models. 

Exam Details 

While LLMs succeed in many scenarios, patterns can be observed where LLMs are inherently struggling with the challenges. This section summarizes these patterns identified from the mistakes made by the LLMs in the exam. 

There are many perspectives to analyze how the mistakes are distributed. 

From the models 

As statistical models, LLMs generate results by their ability to assign probabilities to possible outcomes. Due to many factors during the training process, LLMs may reflect incapabilities collectively or differently by model families. 

All models are wrong in the same way or in different ways 

Mistakes made by all models probably emphasize that LLMs must be applied with caution. 

Although four models differ in complexity between simpler and more advanced models and in architecture between model families, they can still be prone to err in the same way. 

The cases with different wrong answers not only expose the type of problem that surpasses LLMs’ capabilities in general but also reveal the subtle differences between LLMs, even if they are in the same family. 

Interestingly, the latter case does not happen to Azure 900, which is a simpler test. 

Half correct half wrong 

GPT are correct and Llama are wrong or vice versa 

This case arguably demonstrates the difference between LLM families. The difference can originate from any aspects that define the different model creators. Within each family, although there are many aspects that can characterise the models differently, there is common ground which might not be obvious to the model creators themselves. Interestingly the former happens more often than the latter. 

Simple are wrong and complex are correct or vice versa 

This is probably the most challenging case. Normally more advanced models prevail, which has been observed from Table 1. What causes them to be outperformed by their simpler peers is interesting and deserves more in-depth investigation. The finding will benefit model algorithm designs ensuring that scaling has positive effect. This also provides another warning sign that LLMs should be used with caution, which is also the ground that in the proposed benchmark creation mechanism we insist that human supervisor be in each step. Unsurprisingly the former happens more often than the latter. However, the latter can still happen more often in the advanced Azure 203 than Azure 900. 
