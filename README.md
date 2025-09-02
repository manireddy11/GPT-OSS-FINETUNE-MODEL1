<p align="center">
  <img src="https://img.shields.io/badge/🚀%20Fine--Tuning%20GPT--OSS%2020B%20with%20Unsloth-FFFFF0?style=for-the-badge&logoColor=white&labelColor=FFFFF0&color=FFFFF0" width="700"/>
</p>

“Not just running models — I optimized and fine-tuned a 20B parameter LLM within the limits of Google Colab T4.”

<p align="left">
  <img src="https://img.shields.io/badge/🌟%20Why%20This%20Project-808080?style=for-the-badge&logoColor=white&labelColor=808080&color=808080" />
</p>

<p align="center">
  <img src="https://github.com/manireddy11/GPT-OSS-FINETUNE-MODEL1/blob/68da56e4ce8bee30cfcf10d3b7741bd478d8fb98/Screenshot%202025-08-26%20162620.png?raw=true" alt="GPT-OSS Fine-Tune Screenshot" width="1000"/>
</p>


This screenshot shows how the fine-tuned model is queried for inference using Hugging Face’s transformers.

The chat template is applied to format user prompts.

The model.generate() function runs inference with up to 2048 tokens output.

Example prompt:

"I buy a book for $15 and a coffee for $4.50. The sales tax is 8%. What is the total cost?"



Most people give up when compute runs out. I didn’t.
Fine-tuning a 20B model on Colab’s limited T4 GPU sounds impossible — until you bring in Unsloth optimizations and some careful engineering.

This project is my proof-of-work: persistence + problem solving + practical ML engineering.



<p align="center">
  <img src="https://github.com/manireddy11/GPT-OSS-FINETUNE-MODEL1/blob/68da56e4ce8bee30cfcf10d3b7741bd478d8fb98/Screenshot%202025-08-26%20162644.png?raw=true" alt="GPT-OSS Fine-Tune Screenshot" width="800"/>
</p>

TOKEN LENGTH DISTRIBUTION :
Before fine-tuning, we analyzed the dataset’s token length distribution to ensure compatibility with the GPT-OSS-20B model. Token length is critical because exceeding the model’s maximum context window leads to truncation, inefficiency, or higher computational cost.

🔍 Dataset Statistics

Dataset size: 1000 examples

Average length: ~1153 tokens

Median length: 1030 tokens

Maximum length: 32,975 tokens (outliers present)

📈 Token Distribution Breakdown

≤ 512 tokens → 16.0% of examples

≤ 1024 tokens → 49.3% of examples

≤ 2048 tokens → 95.3% of examples

≤ 4096 tokens → 99.8% of examples

📌 Visualization

The histogram below shows the token length distribution across the dataset:

The x-axis represents token counts per example.

The y-axis represents the number of examples within each token length range.

The red dashed line marks the model’s context limit (1024 tokens).

From the plot, we observe:

A large portion of data is clustered below the 1024-token limit.

Nearly half of the dataset fits within the optimal 1024 context window (ideal for fine-tuning efficiency on Google Colab T4 GPU).

A small number of outliers (up to ~32k tokens) exist, which need truncation or special handling during preprocessing to avoid excessive memory usage.

⚡ Why This Matters

Efficient fine-tuning requires balancing sequence length and GPU constraints:

Shorter sequences (≤1024) → Faster training, lower memory usage.

Longer sequences (>1024) → Higher training cost, potential GPU OOM errors.

To optimize performance, we chunked the dataset at 1020 tokens, aligning with the model’s context size and ensuring stable fine-tuning using Unsloth.


<p align="left">
  <img src="https://img.shields.io/badge/📖%20Project%20Highlights-A52A2A?style=for-the-badge&logoColor=white&labelColor=A52A2A&color=A52A2A" />
</p>


<p align="left">
  <img src="https://img.shields.io/badge/🔹%20Model%20&%20Framework-FFD700?style=for-the-badge&logoColor=white&labelColor=FFD700&color=FFD700" width="15%"/>
</p>
Base model: GPT-OSS 20B

Fine-tuning method: Parameter-efficient fine-tuning (PEFT) with Unsloth

Environment: Google Colab (T4 GPU, 16GB)





<p align="left">
  <img src="https://img.shields.io/badge/🔹%20Tokenization%20Challenge-FFD700?style=for-the-badge&logoColor=white&labelColor=FFD700&color=FFD700" width="15%"/>
</p>
Dataset chunked into 1020-token sequences (ideal for Colab T4 memory).

Found 9 outlier sequences exceeding the limit → caused instability & OOM.

Solution: Detect + truncate those outliers (without losing meaningful information).

<p align="left">
  <img src="https://img.shields.io/badge/🔹%20Why%20It%20Matters-FFD700?style=for-the-badge&logoColor=white&labelColor=FFD700&color=FFD700" width="12%"/>
</p>
Preserved information density by fitting all data into uniform sequence lengths.

Avoided wasted compute & reduced training instability.

Achieved smoother convergence and lower loss under resource limits.


<p align="left">
  <img src="https://img.shields.io/badge/📊%20Training%20Journey-006400?style=for-the-badge&logoColor=white&labelColor=006400&color=006400" width="20%"/>
</p>

Loss curves showed stable decline after handling outliers.

Green training bars (Colab widget) gave live progress feedback.

Model generated coherent text outputs from user queries post fine-tuning.
<p align="center">
  <img src="https://github.com/manireddy11/GPT-OSS-FINETUNE-MODEL1/blob/40ee59961307d7a19dd861414a28e1d0c538180c/Screenshot%202025-08-26%20162721.png?raw=true" alt="GPT-OSS Fine-Tune Screenshot" width="800"/>
</p>


<p align="left">
  <img src="https://img.shields.io/badge/⚡%20Skills%20Demonstrated-87CEEB?style=for-the-badge&logoColor=white&labelColor=87CEEB&color=87CEEB" width="20%"/>
</p>

✅ LLM Engineering: Fine-tuning a 20B model with PEFT.
✅ Optimization: Used Unsloth for memory & speed gains.
✅ Data Engineering: Outlier detection + adaptive chunking.
✅ Resource Adaptation: Trained a giant model on low-resource GPUs.
✅ Problem Solving: Avoided information loss while fitting memory limits.

🚀 Run It Yourself

Clone this repo and open the notebook:

git clone https://github.com/your-username/gptoss-20b-finetune-colab.git
cd gptoss-20b-finetune-colab
jupyter notebook gpt_oss_FIXED.ipynb


Or run on Colab (recommended for GPU).

🔮 Future Improvements

Scale beyond Colab T4 (A100, TPU).

Extend fine-tuning with instruction datasets.

Benchmark against Mistral-7B and other mid-size models.

Deploy lightweight chat API using the fine-tuned model.

<p align="center">
  <img src="https://github.com/manireddy11/GPT-OSS-FINETUNE-MODEL1/blob/67f51a870f564c467851afd98f5c9424b88e66db/Screenshot%202025-08-26%20162738%20-%20Copy.png?raw=true" alt="GPT-OSS Fine-Tune Screenshot" width="800"/>
</p>


This example shows the model being tested with a math word problem while reasoning in Japanese, even though Japanese wasn’t part of the training data. The output demonstrates that the model can still understand the question, break it down step by step, and respond in Japanese, successfully solving the problem.




<p align="left">
  <img src="https://img.shields.io/badge/❤️%20Personal%20Reflection-D3D3D3?style=for-the-badge&logoColor=white&labelColor=D3D3D3&color=D3D3D3" width="20%"/>
</p>

This wasn’t just about fine-tuning. It was about persistence.
Training took hours, GPU crashed more than once, and tokenization wasn’t kind — but I adapted.

In the end, I turned a 20B parameter model into something fine-tuned, optimized, and running on a laptop-accessible GPU.

✨ This is how I approach challenges — I don’t stop when resources say “no”. I engineer solutions.

