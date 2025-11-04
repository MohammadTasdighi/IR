# Digikala Comments Indexing & Analyzer

This project implements a **Farsi (Persian) text indexing system** using Elasticsearch.  
It includes a **custom analyzer** to handle Persian text normalization, stopwords, stemming, and proper tokenization for improved search accuracy.

---

## 📂 Index Configuration: Mapping & Analyzer

The Elasticsearch index configuration (`mapping.json`) consists of two main sections:

1. **Settings**: Defines how text is analyzed before indexing.  
2. **Mappings**: Defines the structure of documents and which analyzer is applied to each field.

---

### ⚙️ 1. Settings (Text Analysis)

**Purpose:** Preprocess Persian text to handle spelling variations, word forms, and remove unimportant words.

#### Char Filter: `farsi_normalization`
- Normalizes letters and numbers:
  - Arabic letters → Persian equivalents (`ي → ی`, `ك → ک`)  
  - Numbers → Persian digits (`0 → ۰`, `1 → ۱`, …)  
  - Removes Kashida (`ـ`)  

#### Token Filters
- **Stopwords (`farsi_stop`)**: removes common Persian words like "و", "که", "از"  
- **Stemming (`farsi_stemmer`)**: reduces words to their base form (e.g., `گوشی‌ها → گوشی`)  
- **Lowercase**: makes search case-insensitive  
- **Asciifolding**: handles mixed Persian-English content  

#### Analyzer: `farsi_analyzer`
Combines the above filters with a **standard tokenizer** to ensure words are consistently indexed.

---

### 🗂️ 2. Mappings (Document Structure)

Defines fields in each document and their analyzers:

| Field | Type | Analyzer | Description |
|-------|------|----------|-------------|
| `title` | `text` | `farsi_analyzer` | Review title |
| `body` | `text` | `farsi_analyzer` | Main review text |
| `advantages` | `text` | `farsi_analyzer` | Positive points mentioned in the review |
| `disadvantages` | `text` | `farsi_analyzer` | Negative points mentioned in the review |
| `created_at` | `date` | — | Comment date (`yyyy-MM-dd`, `yyyy/MM/dd`, `epoch_millis`) |

---

### 💡 Summary (Non-Technical Version)

This configuration makes search work correctly for Persian text, even if letters, numbers, or word forms vary.  
It cleans, normalizes, and stems the text before indexing, so users can find relevant reviews efficiently.

---
