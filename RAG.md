

### RAG : Instead of asking an LLM to answer only from what it already knows, we first retrieve relevant information and give that information to the LLM as context.
RAG is not an LLM technique. It is a system architecture.

### Why Do we need RAG
<img width="1226" height="622" alt="Screenshot 2026-09-26 at 11 19 12 PM" src="https://github.com/user-attachments/assets/a05eb052-dbb8-40bf-97a8-d2988bfe627e" />

```
RAG is not equal to Fine tuning 
Rag dosen't change model Behaviour/ model unchanged
Fine Tuning : You modify the model's learned parameters.
```

### How RAG Architecture Work

<img width="1299" height="668" alt="Screenshot 2026-09-26 at 11 38 05 PM" src="https://github.com/user-attachments/assets/416c2b71-b4b5-4717-9490-b2280cd64496" />

```JS
function chunkText(text, chunkSize, overlap) {
    const chunks = [];

    let start = 0;

    while (start < text.length) {
        const end = start + chunkSize;

        chunks.push(text.slice(start, end));

        start += chunkSize - overlap;
    }

    return chunks;
}

```

### Better chunking
```
First try:

Paragraph
   ↓
If too large
   ↓
Sentences
   ↓
If still too large
   ↓
Words

```

### The real RAG problem
```
There is no universally correct chunk size.
Resume --> Small chunks
Research paper --> You may want larger chunks 
Source code --> Normal text chunking can perform poorly.
You may want:
 1: Function-level chunks
 2: Class-level chunks
 3: Module-level chunks

```


