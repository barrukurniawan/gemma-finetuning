## 📘 Fine-Tuning Gemma + Unsloth + LoRA + Export GGUF

Repository ini berisi kode untuk melakukan fine-tuning model Gemma 3 1B dari unsloth (mengurangi kebutuhan memori GPU (VRAM)) dan menggunakan LoRA (parameter efficient tuning), kemudian mengekspor hasilnya ke format GGUF agar bisa dijalankan di local melalui LM Studio / llama.cpp / Ollama.

## 📦 Requirements

- OS yang didukung
Linux (recommended)
macOS
Windows WSL2

- Hardware
GPU NVIDIA minimal 8GB VRAM
(Lebih ideal 16–24GB)

- Python version
minimum 3.8 atau versi diatasnya

## 🚀 Features

Fine-tuning Gemma menggunakan SFTTrainer
Dataset format prompt + completion
Chat template inference
Export model ke GGUF

- Bisa dijalankan offline di laptop/PC menggunakan:
LM Studio
llama.cpp
Ollama

## ⚙️ Installation

- Clone repo:
git clone https://github.com/barrukurniawan/gemma-finetuning.git
cd gemma-finetuning

- Buat Virtual Environment (.env):
python -m venv venv
source venv/bin/activate    # Linux Bash/macOS zsh
.\venv\Scripts\activate.bat # Windows Command Prompt (CMD)
.\venv\Scripts\Activate.ps1 # Windows PowerShell

- Install dependencies (libraries):
pip install -r requirements.txt

Install PyTorch GPU (tidak include di requirements karena spek setiap komputer user berbeda-beda):
OS	        GPU?	            CUDA Version	Perlu versi PyTorch yang berbeda?
Windows	    GPU                 CUDA 12.1	        ✔ YA
Linux	    GPU                 CUDA 11.8	        ✔ YA
Mac M1/M2	Tidak pakai CUDA	Metal backend	    ✔ YA
CPU-only	Tidak pakai CUDA	-	                ✔ YA

- Example:
CUDA 12.1
pip install torch --index-url https://download.pytorch.org/whl/cu121

CUDA 11.8
pip install torch --index-url https://download.pytorch.org/whl/cu118

CPU-only
pip install torch --index-url https://download.pytorch.org/whl/cpu

Mac M1/M2
pip install torch torchvision torchaudio


## Dataset Format

Sumber data yang akan di training, format yang dibuat berupa promp (pertanyaan) dan completion (jawaban)

qa_dataset_question = [
    {
        "prompt": "Apa bedanya Test Case dan Test Scenario?",
        "completion": "Test Scenario adalah gambaran besar mengenai apa yang harus diuji, sementara Test Case adalah langkah-langkah rinci untuk melakukan pengujian tersebut. Satu Test Scenario dapat memiliki banyak Test Case."
    },
    {
        "prompt": "Apa itu SDLC?",
        "completion": "SDLC (Software Development Life Cycle) adalah proses lengkap yang digunakan untuk mengembangkan perangkat lunak dari awal hingga selesai, termasuk perencanaan, analisis, desain, pengembangan, testing, deployment, dan maintenance."
    },
    {
        "prompt": "Apa itu STLC?",
        "completion": "STLC (Software Testing Life Cycle) adalah tahapan-tahapan dalam proses testing, mulai dari requirement analysis, test planning, test case development, environment setup, test execution, hingga test closure."
    }
]


## Jalankan Fine Tuning Gemma

python train.py

