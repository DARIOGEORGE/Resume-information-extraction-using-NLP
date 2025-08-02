<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
</head>
<body>

  <h1> Resume Parser using NLP & Named Entity Recognition (NER)</h1>

  <p>
    Built an intelligent NLP pipeline to extract structured data like 
    <strong>Name, Skills, Degree, College Name, Email, LinkedIn</strong>, and <strong>Work Experience</strong> from resumes in 
    <code>.pdf</code> and <code>.txt</code> formats using <strong>SpaCy's custom NER model</strong>.
  </p>

  <h2> Key Features</h2>
  <ul>
    <li>Annotated JSON dataset conversion for SpaCy training format</li>
    <li>Custom NER model trained using <code>spacy.blank()</code></li>
    <li>Handles overlapping/misaligned entities smartly</li>
    <li>Supports resume testing via both <code>.txt</code> and <code>.pdf</code></li>
    <li>Regex-based extraction of Email, Phone, LinkedIn</li>
  </ul>

  <h2> Entities Extracted</h2>
  <ul>
    <li><strong>Name</strong></li>
    <li><strong>Degree</strong></li>
    <li><strong>College Name</strong></li>
    <li><strong>Skills</strong></li>
    <li><strong>Email</strong></li>
    <li><strong>Phone</strong></li>
    <li><strong>LinkedIn</strong></li>
    <li><strong>Graduation Year</strong></li>
  </ul>

  <h2> Project Files</h2>
  <ul>
    <li><code>NER.ipynb</code> – Jupyter Notebook to train/test NER model</li>
    <li><code>Entity Recognition in Resumes.json</code> – Annotated dataset</li>
    <li>Utility functions for PDF/TXT extraction and testing</li>
  </ul>

  <h2> Dependencies</h2>
  <pre><code>
spacy==3.x
pdfplumber
PyMuPDF (fitz)
regex (re)
random
  </code></pre>

  <h2> How to Use</h2>
  <ol>
    <li>Upload and load the annotated JSON dataset</li>
    <li>Train the model in <code>NER.ipynb</code></li>
    <li>Test on <code>.txt</code> or <code>.pdf</code> resumes</li>
  </ol>

  <h3> TXT Resume Example</h3>
  <pre><code>
with open("your_resume.txt", "r", encoding="utf-8") as f:
    resume_text = f.read()

doc = nlp(resume_text)
for ent in doc.ents:
    print(f"{ent.label_:<25} ➤ {ent.text}")
  </code></pre>

  <h3> PDF Resume Example</h3>
  <pre><code>
import pdfplumber

with pdfplumber.open("your_resume.pdf") as pdf:
    resume_text = " ".join(page.extract_text() for page in pdf.pages)

doc = nlp(resume_text)
for ent in doc.ents:
    print(f"{ent.label_:<25} ➤ {ent.text}")
  </code></pre>

  <h3> Regex Extraction Example</h3>
  <pre><code>
email = re.search(r'[\w\.-]+@[\w\.-]+', resume_text)
phone = re.search(r'\+91[-\s]?[0-9]{10}', resume_text)
linkedin = re.search(r'linkedin\.com\/[^\s]+', resume_text)

if email: print(f"Email ➤ {email.group()}")
if phone: print(f"Phone ➤ {phone.group()}")
if linkedin: print(f"LinkedIn ➤ {linkedin.group()}")
  </code></pre>

  <h2> Sample Output</h2>
  <pre><code>
Name                     ➤ Rahul Verma
Email                    ➤ rahul.verma@gmail.com
Phone                    ➤ +91-9876543210
LinkedIn                 ➤ linkedin.com/in/rahul-verma
Degree                   ➤ M.Tech in Data Science
College Name             ➤ Indian Institute of Technology
Skills                   ➤ Python, SQL, Machine Learning
  </code></pre>

  <h2> Visual Samples</h2>

  <h3>1. Entities from Text Resume</h3>
  <img width="542" height="170" alt="Text Resume Output" src="https://github.com/user-attachments/assets/425bd061-9e86-40c6-8e98-40cc37c68493" />

  <h3>2. Entities from PDF Resume</h3>
  <img width="370" height="153" alt="PDF Resume Output" src="https://github.com/user-attachments/assets/c7e23d45-257b-483c-98dc-a654c368e7fe" />

  <h2> Project Insights</h2>
  <ul>
    <li>Misaligned spans are skipped to avoid crashes</li>
    <li>High-quality annotations significantly improve accuracy</li>
    <li>Regex complements the NER model for contact detail extraction</li>
  </ul>

  <h2> Future Enhancements</h2>
  <ul>
    <li>Fine-tune with SpaCy's pre-trained transformers</li>
    <li>Build a Streamlit frontend for resume uploads</li>
    <li>Improve annotation alignment using rule-based strategies</li>
  </ul>

  <h2> Conclusion</h2>
  <p>
    This project demonstrates the power of NLP and SpaCy’s NER for real-world information extraction. It automates the parsing of resumes to extract key candidate data for faster screening and matching. With enhancements like regex and visualization, it’s a robust base for any resume analytics or HRTech application.
  </p>

</body>
</html>
