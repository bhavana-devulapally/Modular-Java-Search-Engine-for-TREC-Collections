# Modular-Java-Search-Engine-for-TREC-Collections


A comprehensive, modular framework for building and experimenting with information retrieval (IR) pipelines, developed as part of the IS 2140 course at the University of Pittsburgh. This project guides you through:

* **Data Preprocessing**: Load, tokenize, normalize, and filter document collections.
* **Index Construction**: Build and inspect inverted indexes over large corpora.
* **Retrieval Models**: Execute unigram language models with Dirichlet smoothing.
* **Relevance Feedback**: Enhance retrieval using pseudo relevance feedback and Rocchio-style weighting.

---

##  Repository Structure

```text
├── modules
│   ├── preprocessing          # Collection loading & text cleaning
│   ├── indexing               # Inverted index writer & reader
│   ├── retrieval              # Query processing & retrieval models
│   └── feedback               # Relevance feedback integration
├── data                      # Sample TREC collections, topics, stopwords
│   ├── docset.trectext
│   ├── docset.trecweb
│   ├── result.trectext        # preprocessed output
│   ├── result.trecweb         # preprocessed output
│   └── topics.txt             # TREC-style query topics
└── bin                       # Compiled class files after build
```

---

##  Prerequisites

* **Java**: JDK 1.8 (Oracle JDK or OpenJDK)
* **Python 3.x** (optional—for any scripting)
* Build tools or IDE (e.g., Maven, Gradle, Eclipse, IntelliJ)

---

##  Quick Start

1. **Clone the repo**

   ```bash
   git clone https://github.com/yourusername/ir-framework.git
   cd ir-framework
   ```

2. **Compile all modules**

   ```bash
   javac -d bin modules/*/src/**/*.java
   ```

3. **Run components**

   * **Preprocessing**:

     ```bash
     java -cp bin modules.preprocessing.HW1Main
     ```
   * **Indexing**:

     ```bash
     java -cp bin modules.indexing.HW2Main
     ```
   * **Retrieval** (unigram LM):

     ```bash
     java -cp bin modules.retrieval.HW3Main <Dirichlet_mu> <TopN>
     ```
   * **Feedback** (pseudo relevance):

     ```bash
     java -cp bin modules.feedback.HW4Main <mu> <alpha> <feedbackDocs> <TopN>
     ```

> **Tip:** Adjust parameters (e.g., µ between 500–2000) to optimize your search effectiveness.

---

##  Module Details

### 1. Data Preprocessing

* **Tasks**: Load TREC-formatted docs, tokenize text, apply stemming, remove stopwords.
* **Key Classes**: `TrectextCollection`, `TrecwebCollection`, `TextTokenizer`, `TextNormalizer`, `StopwordsRemover`.
* **Input**: `data/docset.*` + `data/stopwords.txt`
* **Output**: Cleaned text files in `modules/preprocessing/output`

### 2. Index Construction

* **Tasks**: Build an inverted index mapping terms to document postings.
* **Key Classes**: `MyIndexWriter`, `MyIndexReader`, `PreProcessedCorpusReader`.
* **Input**: Preprocessed files from module 1
* **Output**: Dictionary + posting lists in `modules/indexing/output`

### 3. Retrieval Models

* **Tasks**: Execute a unigram language model with Dirichlet smoothing.
* **Key Classes**: `ExtractQuery`, `QueryRetrievalModel`.
* **Input**: `data/topics.txt` + index from module 2
* **Output**: TREC run file listing top-ranked documents per query

### 4. Relevance Feedback

* **Tasks**: Implement pseudo relevance feedback to refine query models.
* **Key Classes**: `PseudoRFRetrievalModel`.
* **Input**: Same topics and index from previous modules
* **Output**: Enhanced TREC run file incorporating feedback

---

##  Contributing

1. Fork the repository
2. Create a branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "Add new feature"`
4. Push: `git push origin feature/your-feature`
5. Submit a Pull Request

---

