## 📘 Fine-Tuning Gemma + Unsloth + LoRA + Export GGUF

Repository ini berisi notebook untuk melakukan **fine-tuning Gemma 3 (1B / 2B / 3B)** menggunakan:

- **Dataset** (format prompt + completion)
- **Unsloth** (optimasi penggunaan VRAM, lebih cepat dari HuggingFace)
- **LoRA** (parameter-efficient tuning)
- **SFTTrainer** (cocok untuk dataset kecil–menengah)
- **Export Model ke GGUF** (agar model bisa dijalankan secara lokal via llama.cpp, LM Studio, Ollama, dll)

Notebook ini 100% bisa dijalankan di:

- **Google Colab (recommended — GPU gratis)**
- **Laptop/PC lokal menggunakan Jupyter Notebook / VSCode**

## 🚀 Output dari Fine-Tuning

Dari notebook ini, kamu akan mendapatkan:

✔ Model hasil fine-tuning (folder HuggingFace)  
✔ File **.gguf** siap dipakai di local runtime  
✔ Contoh dataset QA (prompt → completion)  
✔ Template inference chat Gemma 3 + tokenizer 

## 📦 Requirements (Jika ingin training dataset di local, tidak melalui Google Colab)

### **OS yang didukung**
- Linux (recommended)
- Windows (WSL2 disarankan)
- macOS (Intel/M1/M2/M3)

### **Hardware**
- NVIDIA GPU minimal **8GB VRAM**  
  (16–24GB lebih ideal)
- CPU-only juga bisa, tapi lambat

### **Python**
- Minimal **Python 3.9** atau lebih baru

## ⚙️ Installation

> Jika hanya ingin menjalankan di **Google Colab**, lewati bagian ini.
Silakan **copy-paste** setiap langkah.

### 1. Clone repo

```bash
git clone https://github.com/barrukurniawan/gemma-finetuning.git
```

```bash
cd gemma-finetuning
```

### 2. Buat Virtual Environment (.env) -> Install -> Activate

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

### 3. Install Library Jupyter Notebook

```bash
pip install notebook
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
jupyter notebook
```
