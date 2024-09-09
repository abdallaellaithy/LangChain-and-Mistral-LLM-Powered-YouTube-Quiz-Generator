# **LangChain-Powered YouTube Transcript Quiz Generator with Mistral LLM**

This project leverages **LangChain** and the **Mistral-Nemo-Instruct** large language model (LLM) to generate multiple-choice questions and answers from YouTube video transcripts. The generated questions can be used for educational purposes, quizzes, or self-assessment based on the content of the video.

## **Features**
- Utilizes **LangChain** for text processing, prompt management, and output formatting.
- Extracts video transcripts from YouTube using the `youtube_transcript_api`.
- Splits long transcripts into manageable text chunks for efficient question generation.
- Generates multiple-choice questions, correct answers, and three plausible false answers using the **Mistral-Nemo-Instruct** LLM.
- Shuffles answers for randomization to create realistic quizzes.

## **Installation**

Before running the project, install the required dependencies:

```bash
!pip install transformers accelerate mistral_inference langchain youtube_transcript_api
```
## **Usage**

### **Extract Video Transcript**

Use the `extract_video_id` and `fetch_transcript` functions to fetch the transcript from a YouTube video.

**Example:**

```python
video_url = 'YouTube Link'
video_id = extract_video_id(video_url)
transcript = fetch_transcript(video_id)
final_transcript = print_transcript(transcript)
```
### **Split Transcript into Chunks**

Use the `CharacterTextSplitter` from **LangChain** to divide the transcript into manageable chunks:

```python
text_splitter = CharacterTextSplitter(separator=" ", chunk_size=2000, chunk_overlap=0)
normal_chunks = text_splitter.split_text(final_transcript)
```
### **Generate Questions and Answers**

The **Mistral-Nemo-Instruct** LLM is used to generate multiple-choice questions, correct answers, and false answers:

```python
response = generate_text(messages, max_length=1500, num_return_sequences=1)
```
### **Display the Quiz**

The output includes multiple-choice questions with shuffled answers:

```plaintext
Question:
What is the main topic discussed?

Choices:
a) Topic A
b) Topic B
c) Topic C
d) Topic D

Answer: Topic B
```

## **Key Functions**

- **`extract_video_id(url)`**: Extracts the video ID from a YouTube URL.
- **`fetch_transcript(video_id)`**: Fetches the transcript of the video.
- **`generate_text(prompt, max_length, num_return_sequences)`**: Uses **Mistral-Nemo-Instruct** to generate text.

## **Technologies Used**

- **LangChain**: Handles text splitting, prompt formatting, and output parsing.
- **Transformers**: Provides access to pre-trained language models like **Mistral-Nemo-Instruct**.
- **YouTube Transcript API**: Extracts transcripts from YouTube videos.
