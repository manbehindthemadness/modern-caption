<h1>Modern-Caption</h1>

---

**Description:**

This Python script provides functionality for generating image captions using the "modern-caption" library. It utilizes CLIP (Contrastive Language-Image Pretraining) and GPT-2 models for image encoding and caption generation, respectively. Users can generate captions for images using different pre-trained models and decoding methods.

---

**Installation:**

1. **Dependencies:**
   - `torch`
   - `clip`
   - `transformers`
   - `numpy`
   - `PIL`
   - `scikit-image`

2. **Setup:**
   - Ensure you have Python installed on your system.
   - Dependencies will be installed during setup.
   - Setup will **not** overwrite existing installs of PyTorch or Torchvision.
   - Install using pip:
     ```bash
     pip install modern-caption
     ```

---

**Usage:**

1. **Importing the Module:**
   ```python
   from mcaption import Caption
   ```

2. **Initializing the Caption Generator:**
   ```python
   cap = Caption(model='conceptual', device='cpu', prefix_length=10)
   ```

3. **Generating Captions:**
   ```python
   import skimage.io as io
   
   image = io.imread("images/cover.jpg")  # Load the image
   caption_conceptual = cap.predict(image, beam=True)  # Generate caption with beam search
   print("Conceptual Model Caption:", caption_conceptual)
   ```

---

**Explanation:**

- The `Caption` class initializes the image-captioning functionality with options to specify the model, device, and other parameters.
- Users can create multiple instances of the `Caption` class to compare different models or share common resources.
- The `predict` method generates captions for images using the specified model and decoding method.

---

**Examples:**

```python
from mcaption import Caption
import skimage.io as io

# Initialize Caption generator with the 'conceptual' model
cap = Caption(model='conceptual', device='cpu', prefix_length=10)

# Load an image and generate a caption using beam search
image = io.imread("images/cover.jpg")
caption_conceptual = cap.predict(image, beam=True)
print("Conceptual Model Caption:", caption_conceptual)

# Initialize another Caption generator with the 'coco' model, inheriting from the previous one
cap2 = Caption(model='coco', inherit=cap)

# Generate a caption using greedy decoding
caption_coco = cap2.predict(image, beam=False)
print("COCO Model Caption:", caption_coco)
```

---

**Notes:**
- The script demonstrates how to initialize and use the image-captioning functionality provided by the "modern-caption" library.
- Users can experiment with different models and decoding methods to obtain varied captions.
- Ensure that the image paths are correct and accessible.
- This library used the following [repository](https://github.com/rmokady/CLIP_prefix_caption) for conceptual reference.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.