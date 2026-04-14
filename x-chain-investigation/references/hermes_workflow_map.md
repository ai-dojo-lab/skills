# Hermes workflow mapping for OpenClaw

Target sequence:
1. browser_navigate
2. browser_get_images
3. browser_vision / vision_analyze
4. explorer follow-through

OpenClaw equivalents:
- browser/open page: current MCP browser flow (in progress)
- image extraction from local screenshots/images: image tool
- vision analysis: image tool with extraction prompt
- mirrors/search fallback: web_fetch/web_search
- explorer follow-through: browser/web_fetch/manual URL tracing
