<p align="center">
  <img src="https://img.shields.io/badge/🚀%20Fine--Tuning%20GPT--OSS%2020B%20with%20Unsloth-000080?style=for-the-badge&logoColor=white&labelColor=000080&color=000080" width="700"/>
</p>

“Not just running models — I optimized and fine-tuned a 20B parameter LLM within the limits of Google Colab T4.”

<p align="left">
  <img src="https://img.shields.io/badge/🌟%20Why%20This%20Project-808080?style=for-the-badge&logoColor=white&labelColor=808080&color=808080" />
</p>


Most people give up when compute runs out. I didn’t.
Fine-tuning a 20B model on Colab’s limited T4 GPU sounds impossible — until you bring in Unsloth optimizations and some careful engineering.

This project is my proof-of-work: persistence + problem solving + practical ML engineering.


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
  <img src="https://img.shields.io/badge/🔹%20Why%20It%20Matters-FFD700?style=for-the-badge&logoColor=white&labelColor=FFD700&color=FFD700" width="15%"/>
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
📷 Screenshots from my runs::::::::::::::::::::::::::::::::::::::::::::

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

<p align="left">
  <img src="https://img.shields.io/badge/❤️%20Personal%20Reflection-90EE90?style=for-the-badge&logoColor=white&labelColor=90EE90&color=90EE90" width="20%"/>
</p>

This wasn’t just about fine-tuning. It was about persistence.
Training took hours, GPU crashed more than once, and tokenization wasn’t kind — but I adapted.

In the end, I turned a 20B parameter model into something fine-tuned, optimized, and running on a laptop-accessible GPU.

✨ This is how I approach challenges — I don’t stop when resources say “no”. I engineer solutions.

