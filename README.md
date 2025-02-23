# LLM4MT: A Comprehensive Evaluation of State-of-the-Art Large Language Models for Machine Translation

<p> This project evaluates multiple large language models (LLMs) across various language pairs using a range of popular evaluation metrics for machine translation (MT) tasks. We compare their performance for a robust understanding of their capabilities. </p>


## Table of Contents
<ul>
  <li><a href="#project-structure"> Project Structure </a></li>
  <li><a href="#installation"> Installation </a></li>
  <li><a href="#usage"> Usage </a></li>
  <li><a href="#model-information"> Model Information </a></li>
  <li><a href="#evaluation-metrics"> Evaluation Metrics </a></li>
  <li><a href="#language-pairs"> Language Pairs </a></li>
  <li><a href="#results-and-visualization"> Results and Visualization </a></li>
</ul>

## Project Structure
<pre>
- LLM4MT.ipynb                  # Jupyter notebook with main code
- README.md                     # Project README file
- evaluation_results            # Directory containing all the evaluation results pair-wise
- requirements.txt              # Text file with library requirements
- mt_evaluation_results.csv     # Evaluation results files in .csv
- mt_evaluation_results.xlsx    # Evaluation results files in .xlsx
</pre>

## Installation
<p>To set up the environment, run the following commands:</p>
<pre> !pip install sacrebleu bert-score torchmetrics nltk rouge-score datasets transformers groq pandas tqdm matplotlib seaborn </pre>

## Download required NLTK datasets
<pre>
import nltk
nltk.download('wordnet')
nltk.download('omw-1.4')
</pre>

## Usage
<ol>
  <li><strong>Load and Evaluate Models</strong>: Execute the cells in <code>LLM4MT.ipynb</code>. The script will:
    <ul>
      <li>Load translation datasets for specified language pairs.</li>
        <li>Translate each text in the dataset using multiple MT models via Groq API.</li>
          <li>Calculate evaluation metrics and save them to CSV.</li>
            <li>Generate heatmaps for performance visualization.</li>
    </ul>
  </li>

<li><strong>Check Installed Versions</strong> (Optional): Use the following snippet to verify installed package versions:
<pre>
import pkg_resources
packages = ['sacrebleu', 'bert_score', 'torchmetrics', 'nltk', 'rouge_score', 'datasets', 'transformers', 'groq', 'pandas', 'tqdm']
for package in packages:
    try:
        version = pkg_resources.get_distribution(package).version
        print(f"{package}: {version}")
    except pkg_resources.DistributionNotFound:
        print(f"{package}: Not installed")
</pre>

</li>

<li><strong>Run Model Translations and Save Outputs</strong>: The translations and metrics are saved as <code>.csv</code> files for each model and language pair. Visualizations are saved as <code>.png</code> images.</li>
<li><strong>Visualize Results</strong>: Visualizations are saved as heatmaps showing model performance across evaluation metrics.</li>

</ol>

## Model Information

<table>
<thead>
<tr>
<th>Model</th>
  <th>Provider</th>
  <th>Context Length</th>
</tr>
</thead>
  <tbody>
    <tr>
      <td>gemma2-9b-it</td>
      <td>Google</td>
      <td>8192 tokens</td>
    </tr>
    <tr>
      <td>gemma-7b-it</td>
      <td>Google</td>
      <td>8192 tokens</td>
    </tr>
    <tr>
      <td>llama3-groq-70b-8192-tool-use-preview</td>
      <td>Groq</td>
      <td>8192 tokens</td>
    </tr>
    <tr>
      <td>llama3-groq-8b-8192-tool-use-preview</td>
      <td>Groq</td>
      <td>8192 tokens</td>
    </tr>
    <tr>
      <td>llama-3.1-70b-versatile</td>
      <td>Meta</td>
      <td>8192 tokens</td>
    </tr>
    <tr>
      <td>llama-3.1-8b-instant</td>
      <td>Meta</td>
      <td>8192 tokens</td>
    </tr>
    <tr>
      <td>mixtral-8x7b-32768</td>
      <td>Mistral</td>
      <td>32768 tokens</td>
    </tr>
    <tr>
      <td>llama-3.2-90b-vision-preview</td>
      <td>Meta</td>
      <td>128000 tokens</td>
    </tr>
    <tr>
      <td>OLMo-1B</td>
      <td>AI2</td>
      <td>8192 tokens</td>
    </tr>
    <tr>
      <td>Phi-3.5-mini</td>
      <td>Microsoft</td>
      <td>8192 tokens</td>
    </tr>
    <tr>
      <td>Phi-2</td>
      <td>Microsoft</td>
      <td>4096 tokens</td>
    </tr>
    <tr>
      <td>Qwen-2.5-0.5B</td>
      <td>Alibaba</td>
      <td>8192 tokens</td>
    </tr>
    <tr>
      <td>Qwen-2.5-1.5B</td>
      <td>Alibaba</td>
      <td>8192 tokens</td>
    </tr>
    <tr>
      <td>Qwen-2.5-3B</td>
      <td>Alibaba</td>
      <td>8192 tokens</td>
    </tr>
  </tbody>
</table>


## Evaluation Metrics
<p>The project calculates the following metrics to assess translation quality:</p>
<ul>
    <li><strong>BLEU</strong>: Measures n-gram overlap between the candidate and reference. <span>↑</span></li>
    <li><strong>chrF</strong>: Character n-gram F-score. <span>↑</span></li>
    <li><strong>TER</strong>: Translation Edit Rate (lower is better). <span>↓</span></li>
    <li><strong>BERTScore</strong>: A semantic similarity metric using BERT embeddings. <span>↑</span></li>
    <li><strong>Word Error Rate (WER)</strong>: The number of word-level errors. <span>↓</span></li>
    <li><strong>Character Error Rate (CER)</strong>: The number of character-level errors. <span>↓</span></li>
    <li><strong>ROUGE</strong>: Measures overlapping n-grams (ROUGE-1, ROUGE-2, and ROUGE-L). <span>↑</span></li>
</ul>
<p>↑: Higher the better and ↓: Lower the better</p>

## Language Pairs
<p>The project evaluates the following language pairs, taken from the <code>BanglaNMT</code>, <code>wmt18</code> and <code>wmt19</code> dataset. For more information visit: <a href="https://huggingface.co/wmt" target="_blank">Hugging Face</a>.</p>

<ul>
        <li>Czech-English (<code>cs-en</code>) | English-Czech (<code>en-cs</code>)</li>
        <li>German-English (<code>de-en</code>) | English-German (<code>en-de</code>)</li>
        <li>Finnish-English (<code>fi-en</code>) | English-Finnish (<code>en-fi</code>)</li>
        <li>French-German (<code>fr-de</code>) | German-French (<code>de-fr</code>)</li>
        <li>Gujarati-English (<code>gu-en</code>) | English-Gujarati (<code>en-gu</code>)</li>
        <li>Kazakh-English (<code>kk-en</code>) | English-Kazakh (<code>en-kk</code>)</li>
        <li>Lithuanian-English (<code>lt-en</code>) | English-Lithuanian (<code>en-lt</code>)</li>
        <li>Russian-English (<code>ru-en</code>) | English-Russian (<code>en-ru</code>)</li>
        <li>Chinese-English (<code>zh-en</code>) | English-Chinese (<code>en-zh</code>)</li>
        <li>Estonian-English (<code>et-en</code>) | English-Estonian (<code>en-et</code>)</li>
        <li>Turkish-English (<code>tr-en</code>) | English-Turkish (<code>en-tr</code>)</li>
        <li>Bangla-English (<code>bn-en</code>) | English-Bangla (<code>en-bn</code>)</li>
</ul>

## Results and Visualization
<p>Evaluation results are saved as <code>.csv</code> files and visualized using heatmaps. These heatmaps illustrate the relative performance of each model across the various evaluation metrics. Visualizations are saved in <code>.png</code> format and named according to the language pair.</p>
