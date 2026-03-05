---
marp: true
theme: default
paginate: true
footer: ' Institut für Informatik  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 10.3.2026'
style: |
  @import url('https://fonts.googleapis.com/css2?family=Arial:wght@400;700&display=swap');
  section {
    font-family: Arial, sans-serif;
    font-size: 18pt;
    padding-bottom: 3.5rem;
  }
  h1 {
    font-size: 28pt;
    font-weight: bold;
  }
  h2 {
    font-size: 22pt;
    font-weight: bold;
  }
  h3 {
    font-size: 20pt;
    font-weight: bold;
  }
  table {
    font-size: 16pt;
  }
  .highlight {
    color: #00496A;
  }
  .alert {
    color: #cc0000;
  }
  /* Footer with logo */
  section::before {
    content: "";
    position: absolute;
    bottom: 0.3rem;
    left: 3.5rem;
    width: 6rem;
    height: 2.5rem;
    background-image: url("uni-koeln-logo.png");
    background-size: contain;
    background-repeat: no-repeat;
    background-position: left;
    z-index: 1;
  }
  /* Footer text styling */
  footer {
    position: absolute;
    left: 11rem;
    bottom: 1rem;
    font-size: 10pt;
    color: #00496A;
  }
  /* Adjust pagination position to right side */
  section::after {
    position: absolute;
    bottom: 2rem;
    right: 2rem;
    font-size: 10pt;
    color: #00496A;
    content: attr(data-marpit-pagination);
    font-weight: bold;
    
  }

---

<!-- _paginate: "" -->
# Transformer



**Referent:** Paulin Saher
**Datum:** 31.1.2026

---

# Inhalt

- Beispiel Gpt3 basierend auf 3Blue1Brown
- Übersicht 



---

Disclaimer

Wörter != Tokens

Wörter einfacher für Menschen deswegen hier austauschbar für besseres Verständnis

![](https://dataplatform.cloud.ibm.com/docs/api/content/wsj/analyze-data/images/fm-tokenization.png?context=wx&locale=de)
Quelle: https://dataplatform.cloud.ibm.com/docs/api/content/wsj/analyze-data/images/fm-tokenization.png?context=wx&locale=de


---


# Grundidee
1. Wörter -> Embedding -> Vektor
2. Gesamten Input verstehen -> Attention
3. Neues Wort als Vektor Generieren -> Attention
4. Neues Wort Generieren -> Unembedding


---
![bg](Screenshot_05-Mär_11-46-02_org.kde.haruna.png)








---



![bg](Screenshot_05-Mär_11-47-18_383.png)




---

# 1. Embedding
GPT3 50,257 Einzigartige Tokens
Tokens representiert als 12.288 Dimensionale Vektoren


![height:400](Screenshot_05-Mär_11-48-52_9885.png)

---

# 1.1 Grundidee Embedding Matrix
Bedeutung Mathematisch darstellen

---


![bg](Screenshot_05-Mär_11-49-27_16135.png) 

---

![bg](Screenshot_05-Mär_11-49-41_20720.png)

---

![bg](Screenshot_05-Mär_11-51-32_3377.png)

---

# 1.2 Ziel von Embedding
Durch Rechnungen Kontext verstehen und enkodieren.

---

![bg](Screenshot_05-Mär_11-54-34_19266.png)

---

# 2 Attention
Embedding erklärt das Wort aber Kontext fehlt
Kontext kommt von andern Wörtern

---

![bg](Screenshot_05-Mär_12-38-32_205.png)

---

![bg](Screenshot_05-Mär_12-43-47_30492.png)

---

# 2.1 Wie Effizient Kontext suchen

Ineffizient Jedes Wort Gleich zu wiegen

### Queries 

Suche für bestimmte Attribute zum Beschreiben des Wortes (z.b. Adjektive)


---
# Vielen Dank für Ihre Aufmerksamkeit!

**Noch Fragen oder Anmerkungen?**

---
# Quellen 