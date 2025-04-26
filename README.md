# Final Project - Financial-News RAG Assistant with Live Stock-Price Context
*Chen Yang – NUID 002837912*

This Jupyter Notebook presents a complete **Retrieval-Augmented Generation (RAG) assistant** that helps investors and analysts answer natural-language questions about publicly traded companies by combining two complementary data sources:

1. **Semantic News Retrieval** – Topically relevant headlines are fetched from a cleaned CNBC financial-news corpus (2019 – 2024) via a FAISS vector index.  
2. **Live Market Data** – Up-to-date closing prices are pulled on-the-fly with `yfinance`, summarising recent trends (e.g., 30-day movement) for any recognised ticker symbol.

A lightweight language model (DistilGPT-2) then fuses both contexts into a concise answer, giving the user an “at a glance” narrative that blends qualitative news sentiment with quantitative price performance.

### Why this matters — key motivations

- **Information overload**  
  Investors face thousands of headlines per day; manually triaging them is slow and error-prone.

- **Context gaps**  
  News stories rarely include hard numbers, while price charts lack narrative. Merging the two enriches decision-making.

- **Cost-efficient generative AI**  
  The pipeline relies only on open-weights models and free APIs, demonstrating that effective RAG systems need not incur paid token or cloud fees.

### Example interaction

> **Query:** “What drove TSLA’s share price this month and where does it stand now?”

* The FAISS search surfaces headlines about Cybertruck deliveries and price-cut rumours.  
* `yfinance` reports that TSLA gained **≈ 8 %** over the last 30 trading days.  
* The LLM summarises:  
  > “Tesla shares rose about 8 % in the past month, buoyed by renewed EV-demand optimism after the first Cybertruck hand-offs. The stock closed yesterday at \$259.51.”

### Deliverables in this notebook

- End-to-end data pipeline: ingestion → cleaning → embedding → retrieval → generation.  
- Reusable utility functions (`convert_time`, `price_series`, `rag_query`).  
- Ready-to-run Streamlit stub for interactive deployment.

This project showcases a practical, low-cost blueprint for domain-specific RAG applications that amplify human insight by unifying textual and numerical evidence in a single generative answer.
