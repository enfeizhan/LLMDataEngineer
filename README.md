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
