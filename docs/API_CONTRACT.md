# API Contract

## `POST /analyze`

Upload a PDF resume and analyze it in one of two modes.

### Request

`multipart/form-data`

Fields:

- `file` - required PDF resume file
- `mode` - optional, either `resume-only` or `resume-vs-jd`
- `jdText` - optional job description text, required when `mode` is `resume-vs-jd`

### Success Response

```json
{
  "success": true,
  "analysis": {
    "reportTitle": "Resume vs Job Description Analysis",
    "summary": "...",
    "verdict": "...",
    "overallScore": 82,
    "jdMatchScore": 76,
    "scores": {
      "overall": 82,
      "match": 76,
      "readability": 71,
      "impact": 68
    },
    "matchedKeywords": ["React", "Node.js"],
    "missingKeywords": ["AWS", "GraphQL"],
    "strengths": ["Strong project ownership"],
    "gaps": ["Needs more metrics"],
    "suggestions": ["Add measurable outcomes"],
    "actionPlan": ["Rewrite summary", "Add metrics"],
    "formattingIssues": ["Inconsistent bullets"],
    "roleFit": "...",
    "seniority": "Mid-level",
    "experienceSummary": "...",
    "resumeName": "resume.pdf",
    "mode": "resume-vs-jd"
  }
}
```

### Error Response

```json
{
  "success": false,
  "error": "Job description text is required for comparison mode."
}
```

## `GET /health`

Returns a simple health check payload:

```json
{
  "success": true,
  "status": "ok"
}
```