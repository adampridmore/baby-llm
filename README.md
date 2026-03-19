# Baby LLM — Coding Club Exercise

A hands-on workshop notebook that builds a tiny language model from scratch.
No machine learning experience required. Only Python and `numpy` — no PyTorch, no magic.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/adampridmore/baby-llm/blob/main/baby_llm.ipynb)

---

## What you will build

By the end of the notebook you will have:

1. **Tokenised** text — turned words into numbers a model can work with
2. **Built a bigram model** — a simple lookup table that predicts the next word by counting patterns
3. **Built a neural network** — that does the same job but actually *learns* by adjusting its weights
4. **Watched the loss decrease** — concrete proof the model is getting better
5. **Generated text** from both models and compared the results

---

## Prerequisites

- Python 3.9 or later
- `numpy` and `matplotlib`

Install dependencies:

```bash
pip install numpy matplotlib
```

---

## How to open the notebook

### Option A — Google Colab (easiest, nothing to install)

1. Click the **Open in Colab** badge above, or go directly to:
   [colab.research.google.com/github/adampridmore/baby-llm/blob/main/baby_llm.ipynb](https://colab.research.google.com/github/adampridmore/baby-llm/blob/main/baby_llm.ipynb)
2. Click **File → Save a copy in Drive** — this gives you your own editable copy
3. Run each cell with `Shift + Enter`

`numpy` and `matplotlib` are pre-installed in Colab — no setup needed.

### Option B — VS Code (recommended for local)

1. Install the **Jupyter** extension from Microsoft (`Cmd+Shift+X` → search "Jupyter")
2. Install the **Python** extension from Microsoft if you don't have it
3. Open `baby_llm.ipynb` in VS Code
4. When prompted, select your Python interpreter (Python 3.9+)
5. Run each cell with `Shift + Enter`

### Option B — Browser (classic Jupyter)

```bash
pip install jupyter
jupyter notebook baby_llm.ipynb
```

Opens at `http://localhost:8888` in your browser.

---

## How to follow the exercise

The notebook is structured as a series of numbered steps. **Run each cell in order** from top to bottom.

| Step | What happens |
|------|-------------|
| 1 | Load the training text (Shakespeare sonnets) |
| 2 | Tokenise the text — split into words, build a vocabulary, encode as integers |
| 3 | Build a bigram model — count which words follow which |
| 4 | Measure loss — learn how we score a model's performance |
| 5 | Define the neural network — embeddings and a linear layer |
| 6 | Implement backpropagation — how the network adjusts its weights |
| 7 | Run the training loop — watch the loss fall over 100 epochs |
| 8 | Plot the training curve — a visual of the model learning |
| 9 | Generate text — compare bigram vs neural network output |
| 10 | Experiments — your turn to break things and explore |

**To run a cell:** click on it and press `Shift + Enter`.

**If something goes wrong:** use *Run All* from the top menu to reset and re-run everything from scratch.

---

## Key concepts you will encounter

**Token** — the basic unit the model reads. We use words; real LLMs use subword pieces.

**Vocabulary** — the complete set of known tokens, each mapped to a unique integer.

**Embedding** — a vector of numbers that represents a word. The model learns these representations.

**Loss** — a single number measuring how wrong the model is. Lower is better.

**Cross-entropy loss** — "how much probability did you give to the correct answer?"

**Backpropagation** — the algorithm that computes which direction to nudge each weight to reduce loss.

**Gradient descent** — nudge every weight a small step in the direction that reduces loss. Repeat.

**Temperature** — a knob at generation time. Lower = more predictable output. Higher = more random.

---

## Experiments (Step 10)

Once the notebook is running, try these changes and re-run the training cells:

- **Change `EMBED_DIM`** — try `4` (worse?) or `64` (better?)
- **Change `LEARNING_RATE`** — try `0.1` (unstable?) or `0.001` (too slow?)
- **Change `EPOCHS`** — train for 200 epochs — does the loss keep falling?
- **Change the text** — replace `TEXT` with song lyrics or a book excerpt
- **Change the temperature** — at generation time, try `0.1` vs `2.0`

---

## Our model vs real LLMs

| | This notebook | GPT-4 |
|---|---|---|
| Parameters | ~5,000 | ~1,800,000,000,000 |
| Context window | 1 word | ~128,000 words |
| Architecture | Embedding + Linear | Transformer (attention) |
| Training data | 3 sonnets | Most of the internet |
| Training time | Seconds | Months on thousands of GPUs |

The core ideas are identical. The Transformer's **attention mechanism** is the big missing piece — it lets the model look at *all previous words*, not just the last one.
