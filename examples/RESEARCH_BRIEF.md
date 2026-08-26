# Research Brief Example

## Task: Investigate Arabic PDF generation options

```markdown
TARGET: Investigate the best approach for generating Arabic PDFs on Cloudflare Workers — specifically evaluating Cloudflare Browser Rendering vs. traditional PDF libraries.

CONTEXT: We need to generate dispatch manifests in Arabic for drivers. The PDFs must render Arabic correctly (RTL, no tofu boxes) and work offline on mobile devices.

SCOPE:
- Freshness: Within 30 days
- Depth: Compare at least 3 approaches
- Sources: Official docs, community discussions, working examples

QUESTIONS:
1. Does Cloudflare Browser Rendering support Arabic natively?
2. What are the alternatives (pdfkit, puppeteer, @react-pdf/renderer)?
3. Which approach has the smallest bundle size?
4. Which approach works offline?
5. What are the pricing implications of each?

EXPECTED OUTPUT:
- Comparison table (approach, bundle size, offline support, Arabic quality, cost)
- Recommendation with justification
- Working example of the recommended approach
- Risks identified

RESEARCH PRINCIPLE:
Distinguish between FACT / SUPPORTED INFERENCE / OPINION / UNKNOWN
Never fabricate benchmarks or test results.
```
