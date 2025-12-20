# SAGE-MM-Video-Reasoning

> A Gradio-based demonstration for the AllenAI SAGE-MM-Qwen3-VL-4B-SFT_RL multimodal model, specialized in video reasoning tasks. Users upload MP4 videos, provide natural language prompts (e.g., "Describe this video in detail" or custom questions), and receive detailed textual analyses. Supports frame sampling via molmo_utils for efficient processing, with adjustable max new tokens (up to 4096) for response length control.

## Features

- **Video Upload and Analysis**: Handles MP4 inputs; automatically samples frames and generates responses based on prompts.
- **Custom Prompts**: Default "Describe this video in detail"; supports QA, summaries, or specific queries.
- **Advanced Controls**: Slider for max new tokens (128-4096) to tune output verbosity.
- **Interactive Output**: Editable textbox for responses; copy or refine as needed.
- **Custom Theme**: OrangeRedTheme with gradients for a professional interface.
- **Examples Integration**: 5 pre-loaded video samples for quick testing.
- **Efficient Inference**: Auto dtype/device_map; up to 1024 tokens default for balanced speed/quality.

---

<img width="1918" height="1088" alt="Screenshot 2025-12-21 at 05-21-01 SAGE Video Reasoning - a Hugging Face Space by prithivMLmods" src="https://github.com/user-attachments/assets/7427d0a0-cd3a-43ee-9492-48a0d6cde350" />

---

## Prerequisites

- Python 3.10 or higher.
- CUDA-compatible GPU (recommended for auto dtype; falls back to CPU).
- pip >= 23.0.0 (see pre-requirements.txt).
- Stable internet for initial model download (~4B params).

## Installation

1. Clone the repository:
   ```
   git clone https://github.com/PRITHIVSAKTHIUR/SAGE-MM-Video-Reasoning.git
   cd SAGE-MM-Video-Reasoning
   ```

2. Install pre-requirements (for pip version):
   Create a `pre-requirements.txt` file with the following content, then run:
   ```
   pip install -r pre-requirements.txt
   ```

   **pre-requirements.txt content:**
   ```
   pip>=23.0.0
   ```

3. Install dependencies:
   Create a `requirements.txt` file with the following content, then run:
   ```
   pip install -r requirements.txt
   ```

   **requirements.txt content:**
   ```
   git+https://github.com/huggingface/transformers.git@v4.57.1
   git+https://github.com/huggingface/accelerate.git
   git+https://github.com/huggingface/peft.git
   huggingface_hub
   qwen-vl-utils
   sentencepiece
   opencv-python
   torch==2.6.0
   molmo_utils
   torchvision
   matplotlib
   gradio
   ```

4. Start the application:
   ```
   python app.py
   ```
   The demo launches at `http://localhost:7860` (or the provided URL if using Spaces).

## Usage

1. **Upload Video**: Select an MP4 file (height up to 350px preview).

2. **Enter Prompt**: Use default "Describe this video in detail" or customize (e.g., "What is the main action?").

3. **Adjust Tokens**: Expand "Advanced Settings" to set max new tokens (default 1024).

4. **Analyze**: Click "Analyze Video" to process.

5. **Output**: View the generated text response in the editable textbox.

### Examples
- Upload "example-videos/1.mp4" with default prompt: Outputs detailed scene description.
- Upload "example-videos/2.mp4" with "Summarize the events": Provides concise timeline.

## Troubleshooting

- **Model Loading Errors**: Verify transformers v4.57.1 and torch 2.6.0; check device_map="auto" for multi-GPU. Use `dtype=torch.float32` if issues.
- **Video Processing Fails**: Ensure MP4 format; molmo_utils handles sampling—short clips recommended. Check console for frame errors.
- **molmo_utils Missing**: Install via requirements; used for vision info processing.
- **OOM on GPU**: Reduce max_new_tokens; clear cache with `torch.cuda.empty_cache()`.
- **Empty Response**: Ensure prompt is non-empty; default fallback applied.
- **UI Rendering**: Set `ssr_mode=True` if gradients fail; CSS for title sizing.

## Contributing

Contributions encouraged! Fork the repo, add examples or enhance prompts (e.g., multi-video support), and submit PRs with tests. Focus areas:
- Temporal tracking annotations.
- Batch video processing.
- Custom samplers.

Repository: [https://github.com/PRITHIVSAKTHIUR/SAGE-MM-Video-Reasoning.git](https://github.com/PRITHIVSAKTHIUR/SAGE-MM-Video-Reasoning.git)

## License

Apache License 2.0. See [LICENSE](LICENSE) for details.

Built by Prithiv Sakthi. Report issues via the repository.
