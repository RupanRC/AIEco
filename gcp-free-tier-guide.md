# GCP Free Tier — $300 Credit & VM Instances

> **Audience:** Mixed experience (some coding, varying cloud exposure)
> **Goal:** Understand what GCP offers, how to use the $300 credit, and what you can build with VM instances

---

## 1. What is GCP?

**Google Cloud Platform (GCP)** is Google's cloud computing service. It gives you access to:

- **Compute** — Virtual machines, serverless functions, containers
- **Storage** — File storage, databases, object storage
- **AI/ML** — Pre-built AI APIs, Vertex AI, GPU instances
- **Networking** — Load balancers, DNS, CDN
- **And 100+ more services**

**Analogy:** If your laptop is a single apartment, GCP is an entire city of infrastructure you can rent by the second.

---

## 2. The $300 Free Credit

### What You Get
- **$300 USD** in free credits
- **Valid for 90 days** from signup
- **Applies to almost all GCP services**
- **No credit card required in some regions** (but usually needs one for verification)

### What This Means in Practice

| Service | What $300 Gets You |
|---------|-------------------|
| **VM (e2-medium, 2 vCPU, 4GB RAM)** | ~400-500 hours of runtime (24/7 for ~17 days) |
| **VM (e2-micro, 0.25-2 vCPU, 1GB RAM)** | ~2,000+ hours (runs 24/7 for all 90 days!) |
| **Cloud Storage (100GB)** | ~$2.60/month — negligible cost |
| **Cloud Functions** | 2M invocations/month free (beyond credit) |
| **Vertex AI (LLM API)** | ~1,000-5,000 API calls depending on model |
| **GPU Instance (T4)** | ~30-50 hours of GPU compute |

### Key Rule
> **Credits don't auto-convert to paid.** When the $300 runs out or 90 days expire, your services stop unless you upgrade to a paid account. You won't be charged unexpectedly.

---

## 3. Always Free Tier (Beyond the $300)

Even after your $300 credit expires, GCP has an **Always Free** tier:

| Resource | Free Limit |
|----------|-----------|
| **e2-micro VM** | 1 instance per month (US regions only) |
| **Cloud Storage** | 5 GB-months |
| **Cloud Functions** | 2M invocations/month |
| **Cloud Build** | 120 build-minutes/day |
| **Artifact Registry** | 500 MB storage |
| **BigQuery** | 1 TB queries/month, 10 GB storage |

**Pro tip:** The e2-micro VM is always free in US regions. You can run a small server 24/7 forever at no cost.

---

## 4. VM Instances — Virtual Machines

### What is a VM?

A **Virtual Machine** is a computer running inside Google's data centers. You pick the CPU, RAM, storage, and OS — and it works exactly like a real computer, accessible over the internet.

**Analogy:** It's like renting a computer in Google's building. You SSH into it, install software, run code — but it lives in their data center, not on your desk.

### Creating Your First VM

1. Go to [console.cloud.google.com](https://console.cloud.google.com)
2. Navigate to **Compute Engine → VM Instances**
3. Click **Create Instance**
4. Configure:
   - **Name:** `my-first-vm`
   - **Region:** `us-central1` (cheapest, and free tier eligible)
   - **Machine type:** `e2-micro` (free tier) or `e2-medium` (more power)
   - **Boot disk:** Ubuntu 22.04 LTS (recommended for beginners)
   - **Firewall:** Allow HTTP and HTTPS traffic
5. Click **Create**

### Connecting to Your VM

```bash
# From your terminal
gcloud compute ssh my-first-vm --zone=us-central1-a

# Or use the browser-based SSH in the GCP Console
```

### What You Can Do With a VM

| Use Case | Machine Type | Est. Monthly Cost |
|----------|-------------|-------------------|
| **Learning Linux** | e2-micro | **Free** (Always Free tier) |
| **Hosting a website** | e2-micro | **Free** |
| **Running a bot/discord server** | e2-small | ~$5-8/month |
| **AI model experimentation** | e2-medium | ~$15-25/month |
| **GPU for ML training** | n1-standard + T4 GPU | ~$0.35/hour (~$250/month) |
| **Web app backend (Node.js, Python)** | e2-medium | ~$15-25/month |
| **Database server** | e2-medium + 50GB disk | ~$20-30/month |

---

## 5. Practical Projects With $300 Credit

### Project 1: Always-On Development Server (~$0)
- **VM:** e2-micro (Always Free)
- **Use:** Git server, code runner, personal API endpoint
- **Duration:** Forever (no credit needed)

### Project 2: AI API Proxy Server (~$15/month)
- **VM:** e2-medium (2 vCPU, 4GB RAM)
- **Use:** Host an API proxy that routes requests to OpenRouter/OpenAI
- **Duration:** ~20 months with $300 credit

### Project 3: GPU Machine Learning (~$250 for 30 days)
- **VM:** n1-standard-4 + NVIDIA T4 GPU
- **Use:** Train small ML models, run LLM inference locally
- **Duration:** ~30 days with $300 credit

### Project 4: Full-Stack App Hosting (~$30/month)
- **VM:** e2-medium + Cloud SQL (database) + Cloud Storage
- **Use:** Deploy a complete web application with database
- **Duration:** ~10 months with $300 credit

### Project 5: AI Agent Hosting (~$15-25/month)
- **VM:** e2-medium
- **Use:** Run AI agents (Open Manus, custom agents) 24/7
- **Connect to:** OpenRouter API for LLM access
- **Duration:** ~12-20 months with $300 credit

---

## 6. Cost Management — Don't Burn Through Credits

### Set Budget Alerts
1. Go to **Billing → Budgets & alerts**
2. Create a budget for $300
3. Set alerts at 25%, 50%, 75%, 90%
4. Get email notifications before you overspend

### Stop Unused VMs
```bash
# Stop a VM (stops billing for compute, but disk still costs)
gcloud compute instances stop my-first-vm --zone=us-central1-a

# Start it again when needed
gcloud compute instances start my-first-vm --zone=us-central1-a

# Delete it completely (removes everything)
gcloud compute instances delete my-first-vm --zone=us-central1-a
```

### Cheapest Regions
| Region | Cost Multiplier |
|--------|----------------|
| us-central1 (Iowa) | 1.0x (cheapest) |
| us-east1 (South Carolina) | 1.0x |
| us-west1 (Oregon) | 1.0x |
| europe-west1 (Belgium) | 1.1x |
| asia-east1 (Taiwan) | 1.1x |

---

## 7. GCP + AI — What You Can Build

### Combine GCP with Your AI Tools

```
┌─────────────────────────────────────────────────┐
│  Your AI Agent (Roo Code / Cline / Open Manus)  │
│  Running on a GCP VM Instance                   │
├─────────────────────────────────────────────────┤
│                                                 │
│  VM (e2-medium) ──→ API Call ──→ OpenRouter    │
│       ↓                                         │
│  Database (Cloud SQL)                           │
│       ↓                                         │
│  File Storage (Cloud Storage)                   │
│       ↓                                         │
│  Web Interface (Cloud Run / App Engine)         │
│                                                 │
└─────────────────────────────────────────────────┘
```

### Example: 24/7 AI Coding Assistant
1. **VM:** e2-medium running Open Manus or a custom agent
2. **API:** OpenRouter for LLM access (free models available)
3. **Storage:** Cloud Storage for project files
4. **Access:** SSH in from anywhere, agent runs continuously
5. **Cost:** ~$15-25/month for the VM + $0 for free LLM models

---

## 8. Step-by-Step: Your First Hour on GCP

### Minute 0-10: Account Setup
1. Go to [cloud.google.com/free](https://cloud.google.com/free)
2. Sign up with Google account
3. Enter billing info (card for verification)
4. Confirm $300 credit is active

### Minute 10-20: Create Your First VM
1. Open Compute Engine → VM Instances
2. Create an `e2-micro` instance in `us-central1`
3. Select Ubuntu 22.04 LTS
4. Allow HTTP/HTTPS traffic
5. Wait 1-2 minutes for it to start

### Minute 20-40: Connect & Explore
1. SSH into the VM (browser SSH or `gcloud` CLI)
2. Run basic commands:
   ```bash
   uname -a          # Check OS
   free -h           # Check RAM
   df -h             # Check disk
   nproc             # Check CPU cores
   ```
3. Install something:
   ```bash
   sudo apt update
   sudo apt install python3 python3-pip git nodejs npm
   ```

### Minute 40-60: Deploy Something
```bash
# Create a simple Python web server
cat > server.py << 'EOF'
from http.server import HTTPServer, SimpleHTTPRequestHandler
import os

class Handler(SimpleHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header('Content-type', 'text/html')
        self.end_headers()
        self.wfile.write(b'<h1>Hello from GCP!</h1>')

HTTPServer(('0.0.0.0', 80'), Handler).serve_forever()
EOF

python3 server.py
# Access at http://YOUR_VM_EXTERNAL_IP
```

---

## 9. Common Mistakes to Avoid

| Mistake | Consequence | Prevention |
|---------|------------|------------|
| **Leaving GPU instances running** | Burns $300 in ~30 hours | Set budget alerts, stop when done |
| **Using expensive regions** | 10-30% higher costs | Stick to us-central1 |
| **Not setting budget alerts** | Surprise charges | Set alerts at 25%, 50%, 75% |
| **Forgetting about disk costs** | Small but adds up | Delete unused disks |
| **Upgrading to paid accidentally** | Auto-charges after credit expires | Don't upgrade until ready |

---

## 10. Quick Reference

| Question | Answer |
|----------|--------|
| **How long does $300 last?** | 90 days max, or until spent |
| **Can I extend the credit?** | No, but Always Free tier continues |
| **Do I need a credit card?** | Yes, for verification (usually) |
| **What happens when credit expires?** | Services stop, no auto-charge |
| **Best VM for learning?** | e2-micro (Always Free in US) |
| **Best VM for AI experiments?** | e2-medium or n1-standard-4 + T4 GPU |
| **Cheapest region?** | us-central1 (Iowa) |
| **Can I host websites?** | Yes, even on free tier |
| **Can I run AI agents?** | Yes, e2-medium is sufficient for agent orchestration |

---

## Next Steps

1. **Sign up** at cloud.google.com/free
2. **Create an e2-micro VM** — it's free, no risk
3. **SSH in and explore** — install Python, Node.js, git
4. **Deploy something small** — a simple web server or bot
5. **Scale up** when you're comfortable — try e2-medium or GPU instances
