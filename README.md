# 🎥 Open Video Understanding

This project evaluates the **video understanding capabilities** of open-access multimodal AI models across a variety of real-world video clips.  
The goal is to explore how well models can interpret **human actions, emotions, and mental reasoning** from diverse visual and conversational contexts.

---

## 1️⃣ Project Overview

This repository provides a lightweight, reproducible workflow for:
- Extracting and preparing short video clips from various sources (TV series, vlogs, movies, interviews, etc.)
- Designing and iterating prompts for multimodal reasoning
- Evaluating the outputs of different AI models
- Comparing models on their ability to infer **who, what, and why** in a scene

This project can serve as an **open benchmark** for multimodal reasoning and psychological inference in video understanding tasks.

---

## 2️⃣ Data & Video Samples

| Field | Description |
|-------|-------------|
| Source | Publicly available video clips (TV scenes, documentaries, vlogs, etc.) |
| Extraction Tool | [Mebox](https://www.mebox.app) |
| Format | MP4, typically 720p / 24fps |
| Typical Clip Length | 10–60 seconds |
| Metadata | title, source URL, timestamp, characters involved, main action summary |

Example Entry (in `/data/clips_info.csv`):
| id | title | source | duration | main_action |
|----|--------|---------|-----------|--------------|
| 001 | “Dinner argument” | *The Big Bang Theory S3E5* | 28s | Sheldon argues with Leonard |
| 002 | “Street interview” | YouTube vlog | 32s | Two friends discuss career plans |

> ⚠️ **Copyright Notice:** All video materials remain the property of their respective owners and are used **solely for non-commercial research and commentary**.

---

## 3️⃣ Models Evaluated

Recommended open or accessible multimodal models for analysis:

| Model | Access | Type | Link |
|-------|---------|------|------|
| **Gemini 2.5 Pro** | Web (Google Labs) | Text + Video | [Gemini](https://gemini.google.com/) |
| **memories.ai** | Web | Text + Video | [Memories](https://memories.ai/) |
| **GPT-4o** | Web/API (OpenAI) | Text + Image + Video | [ChatGPT](https://chat.openai.com) |
| **Claude 3.5 Sonnet** | Web/API (Anthropic) | Text + Image | [Claude.ai](https://claude.ai) |
| **Yi-VL 1.6** | Open Source | Text + Vision | [Yi-VL on HuggingFace](https://huggingface.co/models) |
| **InternVL 2.0** | Open Source | Text + Video | [InternVL](https://github.com/OpenGVLab/InternVL) |

> 💡 *You may expand the benchmark by testing other models such as Qwen-VL-Max, PaliGemma, or Kosmos-2.5.*

---

## 4️⃣ Prompt Design & Iteration Record

Prompts are used to elicit detailed understanding of **events, actions, and characters’ inner reasoning**.  
They are continuously refined to improve clarity and coverage.

### 🧠 Current Prompt (as of Oct 2025)

> **Prompt v1.0 (2025-10-12)**  
> 1. Summarize in one sentence what happens in this video.  
> 2. Who are the people in the video?  
> 3. What are they doing / what is happening?  
> 4. Exhaustively infer all characters’ mental activities:  
>    - Character A: motivation, perception of surroundings, reasoning about others, and next intended reaction.  
>    - Character B: motivation, perception of surroundings, reasoning about others, and next intended reaction.

### 🧩 Prompt Version Log
| Version | Date | Change Summary |
|----------|------|----------------|
| v1.0 | 2025-10-12 | Initial version with explicit psychological reasoning |
| v1.1 | _TBD_ | Add group interaction reasoning |
| v1.2 | _TBD_ | Include temporal prediction and emotion calibration |

---

## 5️⃣ Workflow

1. **Video Extraction**  
   - Use `Mebox` to download the video clips.  
   - Record metadata: title, timestamp, and main action description.

2. **Model Evaluation**  
   - Upload or describe each clip to the target model.  
   - Use the latest prompt version.  
   - Save responses (in Chinese or English) under `/results/`.

3. **Accuracy Evaluation**  
   - Evaluate model outputs manually using four core metrics:  
     - Scene Summary  
     - Character Recognition  
     - Action/Event Description  
     - Psychological Inference  

4. **Result Storage**  
   - Save each response as `{model_name}_{clip_id}_{date}.txt`  
   - Optionally compute average accuracy across clips.

---

## 6️⃣ Example Result Format

| Clip ID | Model | Output Summary (Chinese) | Ground Truth | Accuracy (%) | Notes |
|----------|--------|--------------------------|---------------|---------------|-------|
| 001 | Gemini 2.5 Pro | “两个男生在餐厅聊天” | 3 people, living room scene | 70 | Missed one character |
| 002 | GPT-4o | “采访中两位女生讨论未来” | Correct | 100 | ✅ |
| 003 | Claude 3.5 | “他们在讨论科学项目” | Actually joking about dating | 50 | Misinterpreted context |
| 004 | InternVL 2.0 | “两人坐着说话” | Correct scene, lacks reasoning | 60 | No emotion inference |

---

## 7️⃣ Analysis & Discussion

Key observations from initial testing:
- Models perform well on **basic visual and linguistic comprehension**.  
- **Emotional and motivational reasoning** remains inconsistent.  
- **Video-native models** often lack fine-grained dialogue comprehension.  
- **Closed commercial models** demonstrate better context integration but still struggle with sarcasm and implicit cues.

---

## 8️⃣ Limitations & Ethics

- The dataset includes heterogeneous clips and small sample sizes.  
- Outputs reflect model interpretations, **not factual truth**.  
- All videos are used under **fair use** for academic analysis.  
- No private or sensitive content is included.  

---

## 9️⃣ Future Directions

- Introduce quantitative scoring and inter-rater agreement.  
- Expand dataset to include cultural and genre diversity.  
- Compare text-only vs multimodal reasoning chains.  
- Develop automatic evaluation scripts for large-scale analysis.

---

## 📁 Repository Structure

