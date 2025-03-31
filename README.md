<h1 align="center">
🎸MyGO: Minimizing Your Generative Overheads – A Retrieval-Augmented and Prefix-Caching Approach for Efficient Inference
</h1>
<p align="center">
  <a> 
    <img
      src="https://img.shields.io/badge/arXiv-b5212f.svg?style=for-the-badge&logo=arxiv&logoWidth=20">
  </a>
  <a href="https://xxx/LICENSE">
  <img alt="License MIT" src="https://img.shields.io/badge/LICENSE-MIT-green.svg?style=for-the-badge&labelColor=000000&logoWidth=20">
  </a>
  <a>
  <img alt="Language" src="https://img.shields.io/badge/Language-Python-blue.svg?style=for-the-badge&logo=python&logoColor=white&labelColor=000000&logoWidth=20">
  </a>
<a>
  <img alt="Deployment" src="https://img.shields.io/badge/Deployment-Docker-blue.svg?style=for-the-badge&logo=docker&logoColor=white&labelColor=000000&logoWidth=20">
  </a>
</p>

## 🔎 MyGO

Retrieval-Augmented Generation (RAG) has demonstrated substantial advancements across various natural language processing tasks by effectively integrating large language models (LLMs) with external knowledge databases. However, RAG systems inherently produce long sequence generations, incurring significant computational and memory overheads. To address this challenge, we propose **MyGO**(Minimizing Your Generative Overheads), a novel multi-level dynamic caching system specifically tailored for RAG.

Through a detailed benchmark analysis of existing RAG frameworks, we identify key performance bottlenecks, notably the generation of extended sequences caused by knowledge injection, and highlight optimization opportunities, particularly caching intermediate states of knowledge retrieval and generation. Leveraging these insights, **MyGO** systematically organizes intermediate retrieval states into a hierarchical knowledge tree structure and adopts a **prefix caching mechanism** to effectively reuse previously computed token-level generation states, thereby reducing redundant computations. The cached data is strategically managed across both GPU and host memory hierarchies. Additionally, **MyGO** introduces a specialized cache replacement algorithm optimized for the inference characteristics of LLMs and the access patterns typical of RAG retrieval. It also dynamically overlaps retrieval and inference processes to further minimize end-to-end latency.

We implement **MyGO** and rigorously evaluate its performance using [vLLM](https://github.com/vllm-project/vllm) & [SGLang](https://github.com/sgl-project/sglang), two state-of-the-art LLM inference frameworks, alongside [FAISS](https://github.com/facebookresearch/faiss), a leading vector database. Experimental results demonstrate that MyGO significantly reduces the time to first token (TTFT) by up to ?× and increases throughput by up to ?× compared to the integration of vLLM & SGLang with FAISS.

For further details, please refer to the paper
