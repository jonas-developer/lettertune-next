# LetterTune ✉️🌿

A multi-model, style-mimicking cover letter generator built with **Next.js 15 + TypeScript**.

LetterTune creates a tailored cover letter using:
1. Company + job offer info
2. Applicant background / resume
3. A previous cover letter (style reference)
4. Optional extra instructions (language, length, tone)

It supports 5 AI backends:
- LLaMA (IBM watsonx)
- Granite (IBM watsonx)
- Mistral (IBM watsonx)
- OpenAI
- DeepSeek

---

## Features

- Modern responsive UI (mobile-friendly)
- Style imitation based on a previous cover letter
- Five selectable AI providers
- **Upload CV/resume** - Supports PDF, DOCX, TXT, and MD files
- **Download as PDF** - Export generated cover letter as formatted PDF
- Structured JSON output
- Server-side API routes
- Type-safe throughout

---

## Live Demo

A hosted version of LetterTune is available at: **https://next.lettertune.com**

This public demo showcases the full end-to-end workflow, including model selection and style-based cover letter generation.

---

## Tech Stack

- **Framework:** Next.js 15 (App Router)
- **Language:** TypeScript
- **Styling:** CSS with CSS Variables
- **AI Integration:** IBM watsonx, OpenAI, DeepSeek APIs

---

## Project Structure

```
lettertune-next/
├── app/
│   ├── api/
│   │   └── generate/
│   │       └── route.ts      # API endpoint
│   ├── globals.css            # Global styles
│   ├── layout.tsx            # Root layout
│   └── page.tsx             # Main page
├── components/
│   ├── ActionButtons.tsx
│   ├── AdditionalInstructionsInput.tsx
│   ├── CopyButton.tsx
│   ├── CoverLetterDisplay.tsx
│   ├── DonationCard.tsx
│   ├── ErrorBox.tsx
│   ├── GenerationInfo.tsx
│   ├── Header.tsx
│   ├── InputCard.tsx
│   ├── KeyMatches.tsx
│   ├── Loader.tsx
│   ├── ModelSelector.tsx
│   ├── ResultCard.tsx
│   ├── StyleNotes.tsx
│   └── TextInput.tsx
├── lib/
│   ├── ai.ts                # AI API integrations
│   └── types.ts             # TypeScript interfaces
├── public/
│   └── images/
│       └── logo.png
├── _old/                    # Archived Flask implementation
├── .env.example
├── next.config.js
├── package.json
├── tailwind.config.js
└── tsconfig.json
```

---

## Requirements

- Node.js 18+
- npm or yarn

---

## Local Setup

### 1. Clone

```bash
git clone https://github.com/jonas-developer/lettertune-next.git
cd lettertune-next
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Copy `.env.example` to `.env.local` and add your API keys:

```bash
cp .env.example .env.local
```

Edit `.env.local` with your keys:

```
# Watsonx (IBM) - for LLaMA, Granite, Mistral
WATSONX_API_KEY=your_watsonx_key
WATSONX_PROJECT_ID=your_project_id

# OpenAI
OPENAI_API_KEY=your_openai_key

# DeepSeek (OpenAI-compatible)
DEEPSEEK_API_KEY=your_deepseek_key
```

### 4. Run development server

```bash
npm run dev
```

Open http://localhost:3000

### 5. Build for production

```bash
npm run build
npm start
```

---

## API Endpoint

### POST /api/generate

**Request:**

```json
{
  "model": "openai",
  "company_job_info": "Company: ... Position: ...",
  "applicant_background": "B.A. Business Administration...",
  "previous_cover_letter": "Dear Hiring Team, ...",
  "additional_instructions": "Write in German, under 250 words"
}
```

**Response:**

```json
{
  "cover_letter": "...",
  "key_matches": ["Skill 1", "Skill 2"],
  "style_notes": "Professional yet warm tone...",
  "suggested_subject": "Application for Banking Position",
  "model": "openai",
  "duration": 2.5,
  "used": 1,
  "limit": 100
}
```

---

## Deployment

### Vercel (recommended)

1. Push to GitHub
2. Import project in Vercel
3. Add environment variables in Vercel dashboard
4. Deploy

### Other platforms

Build command:
```bash
npm run build
```

Start command:
```bash
npm start
```

---

## License

MIT © 2026 L.J Bergman
