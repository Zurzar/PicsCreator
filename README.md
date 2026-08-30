# 🖼️ PicsCreator — Local Stable Diffusion Image Generator

**PicsCreator** is a desktop WPF application (.NET 6+) that allows you to generate images using **Stable Diffusion** entirely offline on your own computer.  
It supports **SDXL**, **LoRA**, **Image‑to‑Image**, **batch generation**, and includes a built‑in **AI prompt enhancer** (based on a local LLM) to create high‑quality prompts without manual effort.

This project is designed for those who value privacy, speed, and full control over generation — everything runs locally, without cloud services.

---

## 🚀 Key Features

- **Model Loading**  
  Supports `.safetensors` (SDXL) and `.gguf` (quantized) models via `StableDiffusion.NET`.

- **Text‑to‑Image Generation**  
  Adjustable width, height, steps, CFG scale, seed, and negative prompt.

- **Image‑to‑Image**  
  Load a source image and modify it with a configurable strength slider. Dimensions are auto‑filled.

- **Multiple LoRA Support (up to 4)**  
  Each LoRA block has its own path and weight. The program automatically adds them to the generation parameters.

- **Batch Generation**  
  Set the number of images (e.g., 20) — the program will generate them sequentially, save them to the `Images` folder, and show progress.

- **AI Prompt Enhancement (local)**  
  Using the **prompt‑fungineer‑v2** (GGUF) model, you can:
  - **Enhance** a short prompt (Enhance button).
  - **Generate a random** prompt (Roulette button).
  - **Generate an adult (18+)** prompt (🔞 18+ button).
  - All completions happen locally, without internet.

- **Preset Management**  
  Save frequently used positive and negative prompts in XML files and load them via dropdown lists.

- **Watermark**  
  The free version adds a subtle watermark with a link to the author's site; the Pro version removes it.

- **Pro Activation**  
  A built‑in activation window with HWID and license key (using VMProtect SDK).

---

## 🖼️ Screenshots

*(Place screenshots in the `Screenshots` folder and link them here)*

![Main Window](2026-08-10_231752.png)
![Activation Window](Screenshots/activation.png)
![Generation Example](Screenshots/generation_example.png)

---

## 🧰 Technology Stack

| Component | Technology |
|-----------|------------|
| Language & Platform | C#, .NET 8, WPF |
| Image Generation | [StableDiffusion.NET](https://github.com/DarthAffe/StableDiffusion.NET) (wrapper around stable‑diffusion.cpp) |
| Image Manipulation | HPPH |
| Local LLM for Prompts | LLamaSharp (wrapper around llama.cpp) + GGUF models |
| Presets | XML serialization |

---

## ⚙️ System Requirements

- OS: Windows 10 / 11 (64‑bit)
- .NET Runtime 6.0 or higher
- GPU with CUDA support (recommended) or CPU (slower but works)
- RAM: at least 8 GB (12+ GB recommended for SDXL)
- Free disk space: ~5–10 GB for models and LoRAs

---

## 📥 Installation & Build

1. **Clone the repository**  
   ```bash
   git clone https://github.com/your-username/PicsCreator.git
   cd PicsCreator
   ```

2. **Restore NuGet packages** (they are already listed in the `.csproj`):  
   - `StableDiffusion.NET`  
   - `LLamaSharp`  
   - `LLamaSharp.Backend.Cpu` or `LLamaSharp.Backend.Cuda12`  
   - `HPPH`  

   Run `dotnet restore` if needed.

3. **Download model files**  
   - Place model files (e.g., `juggernautXL_ragnarok.safetensors`) into the `Models/` folder.  
   - For the AI prompt enhancer, download a GGUF model (e.g., [prompt-fungineer-v2.Q4_K_M.gguf](https://huggingface.co/mradermacher/prompt-fungineer-v2-GGUF)) and place it in the same `Models/` folder.

4. **Configure licensing (optional)**  
   If using VMProtect, create a `key/license.key` file with your license key (or a developer key). For the free version, you can skip activation.

5. **Build the solution**  
   Open `PicsCreator.sln` in Visual Studio and build (Release configuration).

---

## 🖥️ Usage

### Launch & Activation
- On first startup, the program checks for a license key in `key/license.key`.  
- If the key is missing or invalid, the activation window will appear, where you can copy your HWID and send it to the developer to obtain a key.

### Loading a Model
- Click **«Browse»** and select a model file (`.safetensors` or `.gguf`).  
- Click **«Load Model»** and wait for loading (progress is shown in the status text).

### Adjusting Parameters
- Set width, height, steps, CFG scale.  
- Optionally set a seed (leave empty for random).  
- Select up to 4 LoRAs by providing their paths and weights.  
- For Image‑to‑Image, load an initial image and adjust the **Strength** slider.

### Generation
- Enter a prompt in the **Positive** field (you can use presets or AI buttons).  
- Optionally fill the **Negative** field.  
- Press **«Gen Text to Image»** or **«Gen Image‑to‑Image»**.  
- Progress is shown on the image panel.

### Batch Generation
- In the **Count** field, enter the number of images (e.g., 5).  
- Click generate — the program will create all images, display the first one, and notify you about the saved files in the `Images` folder.

### AI Prompt Enhancement (local)
- **Enhance** — expands a short description into a detailed prompt (preserving the original style).  
- **Roulette** — generates a completely random prompt for inspiration.  
- **18+** — generates a romantic/artistic sensual prompt.

### Saving
- Click **«Save Image»** to save the current image (with watermark in the free version).  
- All images are automatically saved to the `Images` folder during batch generation.

---

## 🔒 Licensing

- **Free version**  
  - Watermark on images.  
  - Limited to 1 LoRA at a time.  
  - No batch generation.  

- **Pro version** (Premium)  
  - No watermark.  
  - Up to 4 simultaneous LoRAs.  
  - Unlimited batch generation.  
  - All AI features (Enhance, Roulette, 18+).  
  - Priority support.

To purchase a Pro key, visit [shoppy.gg/@ZugZang](https://shoppy.gg/@ZugZang).

---

## 🤝 Acknowledgments

This project uses the following libraries and tools:

- [StableDiffusion.NET](https://github.com/DarthAffe/StableDiffusion.NET) — core generation library.
- [LLamaSharp](https://github.com/SciSharp/LLamaSharp) — GGUF model integration.
- [HPPH](https://github.com/Helzburger/HPPH) — image manipulation.
- [Prompt Fungineer v2](https://huggingface.co/treadon/prompt-fungineer-v2) — prompt enhancement model (GGUF conversion by mradermacher).

Thanks to the community for these excellent tools!

---

## 📄 License

This project is distributed under a **proprietary license**.  
The source code is provided for review purposes only.  
Commercial use, modification, and redistribution without explicit permission from the author are prohibited.

See the `LICENSE` file for details.

---

## 📬 Contact

- Author: **ZugZang**  
- Website: [shoppy.gg/@ZugZang](https://shoppy.gg/@ZugZang)  
