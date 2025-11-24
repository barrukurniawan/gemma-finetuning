## 📘 Fine-Tuning Gemma + Unsloth + LoRA + Export GGUF

Repository ini berisi kode untuk melakukan fine-tuning model Gemma 3 1B menggunakan Unsloth (optimasi penggunaan VRAM) dan LoRA sebagai metode parameter-efficient tuning.
Hasil fine-tuning juga dapat diekspor ke format GGUF sehingga model bisa dijalankan secara lokal menggunakan runtime seperti llama.cpp, Ollama, atau aplikasi serupa.

#### Bisa dijalankan offline di laptop/PC menggunakan:
- LM Studio
- llama.cpp
- Ollama

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

- Fine-tuning Gemma menggunakan SFTTrainer, karena dataset yang sedikit
- Dataset format prompt + completion
- Chat template inference
- Export model ke GGUF (.gguf adalah format untuk model / LLM)

## ⚙️ Installation

Berikut versi dengan kolom khusus untuk **copy-paste** setiap langkah.

### 1. Clone repo

```bash
git clone https://github.com/barrukurniawan/gemma-finetuning.git
```

```bash
cd gemma-finetuning
```

### 2. Buat Virtual Environment (.env)

**Linux / macOS (zsh / bash):**

```bash
python -m venv venv
```

```bash
source venv/bin/activate
```

**Windows CMD:**

```bash
python -m venv venv
```

```cmd
venv\Scripts\activate.bat
```

**Windows PowerShell:**

```bash
python -m venv venv
```

```powershell
venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

Install PyTorch GPU (tidak include di requirements karena spek setiap komputer user berbeda-beda):

| OS          | GPU Support      | Backend / CUDA Version | Perlu instal PyTorch versi khusus? |
| ----------- | ---------------- | ---------------------- | ---------------------------------- |
| Windows     | GPU              | CUDA 12.1              | ✔️ Ya                              |
| Linux       | GPU              | CUDA 11.8              | ✔️ Ya                              |
| macOS M1/M2 | Tidak pakai CUDA | Metal Backend          | ✔️ Ya                              |
| CPU-only    | Tidak pakai CUDA | –                      | ✔️ Ya                              |

- Example:
CUDA 12.1
```bash
pip install torch --index-url https://download.pytorch.org/whl/cu121
```

CUDA 11.8
```bash
pip install torch --index-url https://download.pytorch.org/whl/cu118
```

CPU-only
```bash
pip install torch --index-url https://download.pytorch.org/whl/cpu
```

Mac M1/M2
```bash
pip install torch torchvision torchaudio
```

## Dataset Format

Sumber data yang akan di training, format yang dibuat berupa promp (pertanyaan) dan completion (jawaban)

```bash
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
```

## Jalankan Fine Tuning Gemma
```bash
python train.py
```
