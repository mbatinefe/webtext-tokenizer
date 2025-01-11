# Web Text Tokenizer

A custom word tokenizer implementation for analyzing web text data, achieving 86% similarity with NLTK's tokenizer.

## Project Overview

This tokenizer was developed specifically for web text analysis, focusing on:
- Discussion forums
- User comments
- Social media content
- Informal web communications

The choice of webtext corpus allows working with:
- Natural language patterns
- Informal writing styles
- Mixed content types
- Real-world language usage

## Features

- Top-down tokenization using regular expressions
- Handles contractions and hyphenated words (e.g. "won't", "ice-cream") 
- Preserves sentence-level punctuation
- Case normalization
- Whitespace cleaning

## Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/webtext-tokenizer.git

# Navigate to directory 
cd webtext-tokenizer

# Install dependencies
pip install nltk
```

## Basic Preview
```python
# Simple example
text = "Hello! This is a web-text example with some punctuation."
tokens = my_tokenizer(text)
print(tokens)
# ['hello', '!', 'this', 'is', 'a', 'web-text', 'example', 'with', 'some', 'punctuation', '.']

# Example with contractions and hyphens
text = "I won't buy that choco-chip ice-cream!"
tokens = my_tokenizer(text)
print(tokens)
# ['i', "won't", 'buy', 'that', 'choco-chip', 'ice-cream', '!']
```

## Implementation Details

### Design Approach
- Top-down tokenization strategy
- Two-part pattern matching:
  1. Word character sequences
  2. Punctuation handling

### Pattern Breakdown
The tokenizer implements a top-down approach using regular expressions:

```python
pattern = r"\w+(?:[-']\w+)*|[.,!?;:]"
```

### Pattern Details

| Component | Description |
|-----------|-------------|
| `\w+` | Match one or more word characters |
| `(?:[-']\w+)*` | Match hyphens/apostrophes + word chars |
| `[.,!?;:]` | Match basic punctuation |

## Evaluation

| Metric | Value |
|--------|--------|
| Similarity Score | 86% |
| Reference | NLTK word_tokenize |
| Test Dataset | NLTK webtext corpus |
| Evaluation Method | Jaccard coefficient |

## Limitations

### Language Support
- English language only
- No Unicode/multilingual support

### Token Processing
- Basic handling of:
  - URLs
  - Email addresses
  - Special characters

### Case Handling
- Loss of capitalization
- No preservation of proper nouns