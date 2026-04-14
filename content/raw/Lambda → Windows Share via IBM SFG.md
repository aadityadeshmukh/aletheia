**Pattern:** Lambda → S3 → IBM Sterling File Gateway → Windows Network Share

---

### Why this approach

Lambda can't natively write to a Windows UNC path. S3 acts as the intermediary drop zone. SFG — which is already connected to your Windows share — picks up from S3 and delivers the file.

---

### Key components

- **S3 bucket** — file drop zone between Lambda and SFG
- **SFG S3 adapter** — polls or event-triggers on new files in the bucket
- **SFG routing rule** — delivers file from S3 to the target Windows share path
- **IAM role** — grants SFG read access to the S3 bucket

---

### Why better than alternatives (FSx, EC2 proxy, Storage Gateway)

SFG is already in the estate, already connected to the Windows share, and already handles retries, routing, and audit trails. No new infrastructure needed.

---

