# WedoHype Voice Agent MCP Server

A powerful MCP server optimized for voice agents, providing complete landing page conversion analysis in a single tool call.

## 🚀 Live Server

**https://wedohype-voice-agent.up.railway.app**

## 🎯 Perfect for Voice Agents

Single tool call: `voice_agent_website_analysis`
- **Input**: Just a URL string
- **Output**: Voice-friendly text summary
- **Works with**: vAPI, Bland AI, Retell AI, and other voice platforms

## What It Does

1. **Website Analysis** - FireCrawl v2 API extracts business information
2. **AI Analysis** - OpenAI GPT-4o identifies 3 landing page conversion opportunities  
3. **Professional Report** - Generates HTML report with conversion recommendations
4. **Email Delivery** - Automatically sends report to business email
5. **Lead Capture** - Silently logs lead in ClickUp
6. **Voice Summary** - Returns simple text for voice agents to speak

## Quick Integration

### vAPI
```json
{
  "functions": [{
    "name": "analyze_website",
    "server": {"url": "https://wedohype-voice-agent.up.railway.app"}
  }]
}
```

### Bland AI / Retell AI
```python
import requests

response = requests.post(
    "https://wedohype-voice-agent.up.railway.app",
    json={
        "tool": "voice_agent_website_analysis",
        "arguments": {"url": "https://example.com"}
    }
)
```

## Environment Variables

Set these in Railway dashboard:

```bash
FIRECRAWL_API_KEY=your_key_here
OPENAI_API_KEY=your_key_here
GMAIL_USER=hello@wedohype.com
GMAIL_CLIENT_ID=your_client_id
GMAIL_CLIENT_SECRET=your_client_secret
GMAIL_REFRESH_TOKEN=your_refresh_token
CLICKUP_API_KEY=your_clickup_key
CLICKUP_LIST_ID=your_list_id
```

## API Setup

- **FireCrawl**: Get key at [firecrawl.dev](https://firecrawl.dev)
- **OpenAI**: Get key at [platform.openai.com](https://platform.openai.com)
- **Gmail**: See [GMAIL_OAUTH2_SETUP.md](GMAIL_OAUTH2_SETUP.md)
- **ClickUp**: Get API key from ClickUp Settings > Apps

## Example Response

**Input**: `{"tool": "voice_agent_website_analysis", "arguments": {"url": "https://acmecorp.com"}}`

**Output**: 
> "I've completed a comprehensive analysis of Acme Corp's website. They're in the technology industry. I identified 3 key landing page conversion opportunities: 1. Headline Optimization - clearer value proposition for better first impression, 2. CTA Simplification - single primary call-to-action with better placement, 3. Form Optimization - reduced friction with social proof placement. I've sent a detailed report to their email at contact@acmecorp.com. The analysis has been completed and logged for follow-up."

## Local Development

```bash
git clone https://github.com/ankaravanas/wedohype-voice-agent.git
cd wedohype-voice-agent
pip install -r requirements.txt
cp .env.example .env  # Edit with your API keys
python voice_agent_mcp_server.py
```

## Testing

```bash
# Test live server
curl -X POST https://wedohype-voice-agent.up.railway.app \
  -H "Content-Type: application/json" \
  -d '{"tool": "voice_agent_website_analysis", "arguments": {"url": "https://wedohype.com"}}'

# Test locally
curl -X POST http://localhost:8000 \
  -H "Content-Type: application/json" \
  -d '{"tool": "voice_agent_website_analysis", "arguments": {"url": "https://wedohype.com"}}'
```

## Files

- `voice_agent_mcp_server.py` - Main server
- `requirements.txt` - Dependencies
- `railway.json` - Railway deployment config
- `VOICE_AGENT_EXAMPLES.md` - Detailed integration examples
- `GMAIL_OAUTH2_SETUP.md` - Gmail setup guide

Railway auto-deploys from GitHub. Just push changes and they go live automatically.

Built for voice agents. Landing page conversion optimization made simple, powerful, and production-ready.