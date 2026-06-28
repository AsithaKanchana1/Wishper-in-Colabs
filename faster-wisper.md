# Faster Whisper Transcription Project

This project demonstrates how to use **faster-whisper** (a high-performance reimplementation of OpenAI's Whisper model using CTranslate2) to transcribe audio and video files blazing fast inside Google Colab.

---

## 🚀 Features

- **Blazing Fast Speed:** Up to 4x faster transcription compared to the standard OpenAI Whisper implementation.
- **Memory Efficient:** Uses less VRAM, allowing larger models to run easily on standard GPUs.
- **Multi-language Support:** Automatic language detection and high-quality translation/transcription.
- **Flexible Formats:** Automatically outputs clean transcriptions in both `.txt` and `.srt` (subtitle) formats.

---

## 📝 Instructions

### Step 1: Open Google Colab

Go to [Google Colab](https://colab.research.google.com/) and create a new notebook.

### Step 2: Change Runtime Type to GPU

1. Click on **Runtime** in the top menu.
2. Select **Change runtime type**.
3. Set Hardware accelerator to **T4 GPU** (or any available GPU) and click **Save**.

### Step 3: Install Faster-Whisper and Dependencies

In the first cell of your notebook, run the following commands to install the optimized transcription engine and media processing tools:

```bash
!pip install faster-whisper yt-dlp
!sudo apt update && sudo apt install ffmpeg

```

### Step 4: Upload Your Audio or Video File

You can upload your file by navigating to the **Files** folder icon on the left sidebar of Colab and clicking the **Upload** icon.

#### 📋 Option A: Access Files from Google Drive

If your files are stored in Google Drive, follow these steps to download them directly into Colab:

1. Go to your Google Drive.
2. Right-click the file, select **Share** -> **Get link**.
3. Change the general access from _Restricted_ to **Anyone with the link**.
4. Copy the file ID from the URL (the long string of characters between `/d/` and `/view`).
5. Run the following command in Colab (replace `YOUR_FILE_ID` with your actual ID):

```bash
!gdown --id YOUR_FILE_ID

```

#### 🔴 Option B: Download YouTube Videos Directly

To transcribe a video directly from YouTube, run the following code cell to download the audio stream:

```python
video_url = "https://www.youtube.com/watch?v=YOUR_VIDEO_ID"
!yt-dlp -f ba -x --audio-format mp3 -o "input_audio.mp3" {video_url}

```

_(This downloads only the audio track, making the process much faster!)_

---

### Step 5: Run Faster-Whisper for Transcription

Paste and run the following Python script in a new cell. This script handles the high-speed execution and automatically formats your output into standard text and subtitle files.

```python
import datetime
from faster_whisper import WhisperModel

# --- Configuration ---
# Replace with your file name (e.g., "input_audio.mp3" or "video.mp4")
FILE_NAME = "YOUR_FILE_NAME"
# Options: "tiny", "base", "small", "medium", "large-v3"
MODEL_SIZE = "medium"

print("Initializing Faster-Whisper model...")
# We use float16 precision to maximize performance on the GPU
model = WhisperModel(MODEL_SIZE, device="cuda", compute_type="float16")

print(f"Processing '{FILE_NAME}'... This will be quick!")
segments, info = model.transcribe(FILE_NAME, beam_size=5)

print(f"Detected language: '{info.language}' with a certainty of {info.language_probability:.2f}")

# Convert generator to list to allow writing to multiple files
segments = list(segments)

# Helper function to format SRT timestamps
def format_srt_time(seconds):
    td = datetime.timedelta(seconds=seconds)
    total_secs = int(seconds)
    millis = int((seconds - total_secs) * 1000)
    hours = total_secs // 3600
    minutes = (total_secs % 3600) // 60
    secs = total_secs % 60
    return f"{hours:02d}:{minutes:02d}:{secs:02d},{millis:03d}"

# 1. Save as plain text file (.txt)
with open("transcription.txt", "w", encoding="utf-8") as txt_file:
    for segment in segments:
        txt_file.write(segment.text.strip() + "\n")

# 2. Save as subtitle file (.srt)
with open("transcription.srt", "w", encoding="utf-8") as srt_file:
    for i, segment in enumerate(segments, start=1):
        srt_file.write(f"{i}\n")
        srt_file.write(f"{format_srt_time(segment.start)} --> {format_srt_time(segment.end)}\n")
        srt_file.write(f"{segment.text.strip()}\n\n")

print("\n🎉 Done! Your files 'transcription.txt' and 'transcription.srt' are ready to download.")

```

---

### Step 6: Download the Transcription Files

Once the script finishes:

1. Refresh the **Files** sidebar on the left.
2. Locate `transcription.txt` and `transcription.srt`.
3. Click the three dots next to the file and select **Download**.

---

## ⚠️ Warnings and Important Notes

- **Privacy:** Be cautious when uploading sensitive audio/video files to public cloud environments like Google Colab.
- **Model Choices:** If speed is your main goal, use `small` or `medium`. If extreme structural accuracy or translation is required, use `large-v3`.
- **GPU Timeout:** Google Colab's free tier limits consecutive GPU usage. For massive batches of long videos, consider processing them in smaller batches or upgrading to Colab Pro.

---

## 🛠️ Dependencies

- **Python 3.x**
- **faster-whisper:** Reimplementation of OpenAI's Whisper model using CTranslate2.
- **FFmpeg:** Backend framework for handling multi-format audio/video processing.
- **yt-dlp:** Modern, regularly updated tool for downloading media streams.

---

## 🤝 Contributing

Feel free to fork this repository, open issues, or submit pull requests to expand script capabilities (e.g., adding VTT outputs or speaker diarization).

---

## 🙏 Acknowledgements

- **OpenAI** for designing the robust, multilingual Whisper architecture.
- **Systran** for developing `faster-whisper` and the `CTranslate2` engine which makes high-speed inference accessible.
- **Google Colab** for providing the GPU runtime environments to accelerate these pipelines.

---

## 📞 Contact

For questions or feedback, open an issue in the repository or contact me via [asitha.contact.me@gmail.com].

---

## 🔗 Links

- [Faster-Whisper GitHub Repository](https://github.com/SYSTRAN/faster-whisper)
- [Google Colab](https://colab.research.google.com/)
- [LinkedIn](https://linkedin.com/asithakanchana)
- [GitHub](https://github.com/AsithaKanchana1)
- [WebSite](www.asitha.online)

---

## 📑 License

This project is licensed under the MIT License - see below for details.

### Copyright Notice

```text
Copyright (c) 2024 Asitha Kanchana Palliyaguru

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

```
