# Digikala Comments Project – Warm-Up Checklist

This checklist summarizes all tasks related to the **Warm-Up phase** of the project, focusing on **Lexical Search and Farsi text indexing** in Elasticsearch.  

---

## ✅ Completed Tasks

### 1. Elasticsearch Setup
- [x] Elasticsearch server installed and running (locally or via Docker)
- [x] Connection to Elasticsearch verified

### 2. Index Creation
- [x] Index `digikala_comments` created
- [x] Custom settings and mappings applied

### 3. Custom Analyzer (`farsi_analyzer`)
- [x] **Char Filter**: `farsi_normalization` defined
  - Normalizes Persian letters (`ي → ی`, `ك → ک`)
  - Converts digits to Persian (`0 → ۰`, `1 → ۱`, …)
  - Removes Kashida (`ـ`)
- [x] **Tokenizer**: `standard` tokenizer used
- [x] **Token Filters**
  - Lowercase conversion
  - Persian stopword removal (`farsi_stop`)
  - Stemming (`farsi_stemmer`)
  - Asciifolding for mixed Persian-English content

### 4. Data Indexing
- [x] CSV file (`digikala-comments.csv`) read in chunks for memory optimization
- [x] Each row sent as a separate document
- [x] Fields `title`, `body`, `advantages`, `disadvantages`, `created_at` indexed
- [x] Analyzer `farsi_analyzer` applied to all text fields
- [x] Dates normalized from Jalali (Shamsi) to Gregorian format

### 5. Sample Queries
- [x] Basic `match` query executed on `body` field
- [x] Elasticsearch BM25 scoring used for ranking

---

## 💡 Notes

- **Chunked Processing**: Used to prevent memory overflow due to large dataset
- **Purpose of Analyzer**: Improves Persian text search by normalizing letters, stemming, and removing stopwords
- **Index Fields**:
  - `title`: Review title
  - `body`: Comment text
  - `advantages`: Positive points
  - `disadvantages`: Negative points
  - `created_at`: Comment release date

---

### ✅ Conclusion

All **Warm-Up tasks (Lexical Search + Farsi indexing)** are completed.  
