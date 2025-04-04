# Whisper Transcription Project

This project demonstrates how to use **OpenAI's Whisper** model to transcribe audio and video files using **Google Colab**. Whisper provides accurate speech-to-text transcription for a wide range of audio formats and languages.

---

## 🚀 Features
- **Easy-to-use** transcription pipeline in Google Colab.
- **Support for multiple languages**.
- Transcribe **audio and video files** using Whisper models.
- Output transcriptions in `.txt` or `.srt` and other populer formats.

---

## 📝 Instructions

### Step 1: Open Google Colab
Go to [Google Colab](https://colab.research.google.com/) and create a new notebook.

### Step 2: Change Runtime Type to GPU
- Click on **Runtime** in the top menu.
- Select **Change runtime type**.
- Set **Hardware accelerator** to **GPU** and click **Save**. This allows Whisper to run faster.

### Step 3: Install Whisper and Dependencies
In the first cell of the notebook, run the following commands to install Whisper and the required dependencies:

```bash
!pip install git+https://github.com/openai/whisper.git
!sudo apt update && sudo apt install ffmpeg

```

### Step 4: Upload Your Audio or Video File
- Upload your file by navigating to the **Files** tab in Colab.
- Click on **Upload** to select your audio or video file from your local system.

## 📋 How to Upload and Access Files from Google Drive

If you want to upload and access your audio/video files from **Google Drive** in Google Colab, follow these steps:

### Step 1: Set File Permissions in Google Drive
1. Go to your **Google Drive**.
2. Right-click on the file you want to use.
3. Select **Get link**.
4. In the "Get Link" section, change the file's permissions to **Restricted** and make sure it is set to **Anyone with the link**.

### Step 2: Copy the File ID
- Copy the file ID from the URL. The file ID is the long string of characters that comes after `d/` in the URL. For example, in the following URL:

[Demo File URL](https://drive.google.com/file/d/xxxxxxxxxxxxxxxxxxxxxxx/view?usp=sharing)


The **file ID** is: `xxxxxxxxxxxxxxxxxxxxxxx`.

### Step 3: Download the File in Colab
1. Open your **Google Colab** notebook.
2. Run the following command to download the file using **gdown**:

  ```bash
  !gdown --id xxxxxxxxxxxxxxxxxxxxx
  ```

  Replace `xxxxxxxxxxxxxxxxxxxx` with the actual file ID you copied in Step 2.


### Step 5: Run Whisper for Transcription
Run the following code in a new Colab cell to transcribe your uploaded file:

```bash
!whisper "YOUR_FILE_NAME" --model medium

```

### Step 6: Download the Transcription Files
After Whisper completes the transcription, you will find `.txt` and `.srt` files in the Colab environment. To download these files:
- Right-click on the file.
- Select **Download** from the context menu to save the transcription files to your local system.

---

## ⚠️ Warnings and Important Notes

- **Privacy**: Be cautious when uploading sensitive or confidential audio and video files to cloud services like Google Colab. Always ensure that the data you upload is safe and within your privacy requirements.
- **Model Limitations**: Whisper's transcription accuracy may vary depending on the quality of the audio and background noise. It works best with clear, high-quality audio recordings. Noisy or distorted audio may result in inaccurate transcriptions.
- **Large Files**: Transcribing large video or audio files can take a significant amount of time and computational resources. Please be patient while the transcription is being processed.
- **GPU Usage**: Google Colab's free-tier GPU usage is limited, and long-running tasks might be interrupted. For better performance and fewer interruptions, consider upgrading to **Colab Pro**.

## 💡 Additional Information
- You can modify the model to use different sizes (e.g., `small`, `medium`, `large`) based on your needs for speed vs. accuracy. Larger models (like `large`) provide better accuracy, but may require more computational resources.
- Whisper supports a variety of languages. For a full list of supported languages and additional features, check out the [Whisper documentation](https://github.com/openai/whisper).

---

## 🛠️ Dependencies
- **Python 3.x**
- **Whisper**: OpenAI's speech-to-text model.
- **FFmpeg**: For handling audio and video file processing.
- **gdown**: For access to Google Drive 
---

## 🤝 Contributing
Feel free to fork this repository and submit issues or pull requests. Contributions are welcome!

---

## 🙏 Acknowledgements
- **OpenAI** for developing Whisper, the state-of-the-art speech-to-text model.
- **Google Colab** for providing free GPU access that makes running Whisper faster and more accessible.
- The **open-source community** for their continued support and contributions to projects like this.

## 📞 Contact
For questions or feedback, open an issue in the repository or contact me via [asitha.contact.me@gmail.com].

---

## 🔗 Links
- [Whisper GitHub Repository](https://github.com/openai/whisper)
- [Google Colab](https://colab.research.google.com/)
- [Linkdn](https://www.linkedin.com/in/asitha-kanchana-35aa531a8/)
- [GitHub](github.com/AsithaKanchana1)

---

### **Explanation of Sections**:
- **Features**: Highlights the key features of the Whisper Transcription Project.
- **Instructions**: Provides a detailed, step-by-step guide for users to follow when using Whisper on Google Colab.
- **Warnings**: Outlines important cautions and notes about file privacy, model limitations, and usage limitations.
- **License**: Mentions the **MIT License**, and points to the `LICENSE` file (which you can add in your repository).
- **Dependencies**: Lists the software dependencies required for running the project.
- **Contributing**: Encourages users to contribute to the project.
- **Acknowledgements**: Credits the contributors, including OpenAI and Google Colab.
- **Contact**: Provides a way for users to get in touch for support or feedback.
- **Links**: Provides quick access to external resources (Whisper GitHub, Google Colab).

---

## 📑 License

This project is licensed under the **MIT License** - see the LICENSE file for details.

---

### Copyright Notice

Copyright (c) 2024 Asitha Kanchana Palliyaguru

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


