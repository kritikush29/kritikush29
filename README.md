import { useState } from "react";
 
const MUST_HAVE = [
  {
    id: "header",
    name: "Animated wave header",
    tool: "capsule-render.vercel.app",
    desc: "A colorful animated banner at the very top. First thing anyone sees — immediately signals you care about presentation.",
    effort: "Paste & done",
    where: "Very first line of README.md",
    previewUrl: "https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=130&section=header&text=Hey%2C%20I%27m%20Kriti!&fontSize=34&fontColor=fff&animation=twinkling&fontAlignY=36&desc=Frontend%20Dev%20%C2%B7%20Designer%20%C2%B7%20ML%20Curious&descAlignY=60&descSize=13",
    code: `![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=180&section=header&text=Hey%2C%20I%27m%20Kriti!&fontSize=42&fontColor=fff&animation=twinkling&fontAlignY=32&desc=Frontend%20Dev%20%C2%B7%20Designer%20%C2%B7%20ML%20Curious&descAlignY=55&descSize=18)`,
  },
  {
    id: "typing",
    name: "Typing animation",
    tool: "readme-typing-svg.demolab.com",
    desc: "Animated text cycling through your roles. Makes the header feel alive and stops anyone mid-scroll.",
    effort: "Paste & done",
    where: "Below your intro paragraph",
    previewUrl: "https://readme-typing-svg.demolab.com?font=Fira+Code&size=20&pause=1000&color=F75C7E&center=true&vCenter=true&width=500&lines=Frontend+Developer;UI%2FUX+Designer;Python+Explorer;Open+to+Internships+%26+Freelance",
    code: `<p align="center">\n  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&pause=1000&color=F75C7E&center=true&vCenter=true&width=500&lines=Frontend+Developer;UI%2FUX+Designer;Python+Explorer;Open+to+Internships+%26+Freelance" alt="Typing SVG" />\n</p>`,
  },
  {
    id: "skills",
    name: "Skill icons",
    tool: "skillicons.dev",
    desc: "Beautiful, consistent tech icons in one line. A recruiter parses your entire stack in 2 seconds. Way better than a text list.",
    effort: "Paste & done",
    where: "Replace your skills section",
    previewUrl: "https://skillicons.dev/icons?i=react,js,tailwind,vite,py,flask,figma,html,css,mysql&perline=5",
    code: `<p align="center">\n  <a href="https://skillicons.dev">\n    <img src="https://skillicons.dev/icons?i=react,js,tailwind,vite,py,flask,figma,html,css,mysql&perline=5" />\n  </a>\n</p>`,
  },
  {
    id: "repocards",
    name: "Project repo cards",
    tool: "github-readme-stats (anuraghazra)",
    desc: "Styled cards for each project showing language and stars. Turns plain links into something that looks like work you're actually proud of.",
    effort: "Paste & done",
    where: "Inside your Projects section",
    previewUrl: "https://github-readme-stats.vercel.app/api/pin/?username=kritikush29&repo=kalakriti&theme=tokyonight&hide_border=true",
    code: `[![kalakriti](https://github-readme-stats.vercel.app/api/pin/?username=kritikush29&repo=kalakriti&theme=tokyonight&hide_border=true)](https://github.com/kritikush29/kalakriti)\n\n[![JanVaani](https://github-readme-stats.vercel.app/api/pin/?username=kritikush29&repo=JanVaani&theme=tokyonight&hide_border=true)](https://github.com/kritikush29/JanVaani)\n\n[![asteya](https://github-readme-stats.vercel.app/api/pin/?username=kritikush29&repo=asteya&theme=tokyonight&hide_border=true)](https://github.com/kritikush29/asteya)`,
  },
  {
    id: "footer",
    name: "Matching footer wave",
    tool: "capsule-render.vercel.app",
    desc: "A mirrored wave that closes the README. Makes the whole thing feel designed — not like it just stops.",
    effort: "Paste & done",
    where: "Very last line of README.md",
    previewUrl: "https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=100&section=footer",
    code: `![footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=100&section=footer)`,
  },
];
 
const NICE_TO_HAVE = [
  {
    id: "stats",
    name: "GitHub stats + top languages",
    tool: "github-readme-stats (anuraghazra)",
    desc: "Side-by-side stats card and language breakdown. Strong credibility signal once you have real numbers in public repos.",
    effort: "Paste & done",
    where: "After your Projects section",
    caveat: "Sparse stats look worse than no stats. Add this once you have 5+ repos with real code pushed.",
    previewUrl: "https://github-readme-stats.vercel.app/api/top-langs/?username=kritikush29&layout=compact&theme=tokyonight&hide_border=true",
    code: `<p align="center">\n  <img src="https://github-readme-stats.vercel.app/api?username=kritikush29&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" width="48%" />\n  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=kritikush29&layout=compact&theme=tokyonight&hide_border=true" width="48%" />\n</p>`,
  },
  {
    id: "activity",
    name: "Contribution activity graph",
    tool: "github-readme-activity-graph",
    desc: "A heatmap of your commits over the past year. When filled in, this is one of the strongest credibility signals on any profile.",
    effort: "Paste & done",
    where: "Above footer",
    caveat: "A flat/empty graph hurts more than no graph. Start committing regularly first — even README updates count.",
    previewUrl: "https://github-readme-activity-graph.vercel.app/graph?username=kritikush29&theme=tokyo-night&hide_border=true",
    code: `[![Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=kritikush29&theme=tokyo-night&hide_border=true)](https://github.com/ashutosh00710/github-readme-activity-graph)`,
  },
  {
    id: "snake",
    name: "Contribution snake animation",
    tool: "Platane/snk + GitHub Actions",
    desc: "A snake that eats your GitHub contribution squares. Genuinely memorable — recruiters screenshot this. Worth the 15-minute setup.",
    effort: "15 min setup",
    where: "Above footer",
    previewUrl: null,
    code: `# STEP 1: Create this file in your profile repo:\n# .github/workflows/snake.yml\n\nname: Generate Snake\non:\n  schedule:\n    - cron: "0 0 * * *"\n  workflow_dispatch:\n\njobs:\n  generate:\n    runs-on: ubuntu-latest\n    steps:\n      - uses: Platane/snk@v3\n        with:\n          github_user_name: kritikush29\n          outputs: |\n            dist/github-contribution-grid-snake.svg\n            dist/github-contribution-grid-snake-dark.svg?palette=github-dark\n      - uses: crazy-max/ghaction-github-pages@v3.1.0\n        with:\n          target_branch: output\n          build_dir: dist\n        env:\n          GITHUB_TOKEN: \${{ secrets.GITHUB_TOKEN }}\n\n# STEP 2: Settings > Pages > set source to 'output' branch\n\n# STEP 3: Add to README.md:\n\n<picture>\n  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/kritikush29/kritikush29/output/github-contribution-grid-snake-dark.svg">\n  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/kritikush29/kritikush29/output/github-contribution-grid-snake.svg">\n  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/kritikush29/kritikush29/output/github-contribution-grid-snake.svg">\n</picture>`,
  },
];
 
const SKIP = [
  { id: "streak", name: "GitHub streak counter", reason: "Displays your current and longest commit streak. With a new account, you'll show single-digit numbers — actively worse than nothing. Revisit in 6 months." },
  { id: "trophies", name: "GitHub profile trophies", reason: "Awards based on followers, stars, and commits. With few public repos you get mostly bronze badges, which looks emptier than a blank space." },
  { id: "views", name: "Profile view counter", reason: "A counter in the hundreds signals low reach. Tells recruiters you're small, not growing. Adds nothing positive." },
  { id: "quotes", name: "Random dev quote", reason: "Every README generator adds one. Recruiters immediately recognise this as a copy-pasted template." },
];
 
const ACCENTS = { success: "#3B6D11", warning: "#854F0B", danger: "#A32D2D" };
const BADGE = {
  success: { bg: "var(--color-background-success)", color: "var(--color-text-success)" },
  warning: { bg: "var(--color-background-warning)", color: "var(--color-text-warning)" },
  danger:  { bg: "var(--color-background-danger)",  color: "var(--color-text-danger)"  },
  neutral: { bg: "var(--color-background-secondary)",color: "var(--color-text-secondary)"},
};
 
function Pill({ label, type = "neutral" }) {
  const s = BADGE[type];
  return (
    <span style={{ background: s.bg, color: s.color, fontSize: 10, fontWeight: 500, padding: "2px 8px", borderRadius: 20, whiteSpace: "nowrap" }}>
      {label}
    </span>
  );
}
 
function Card({ item, accent }) {
  const [showCode, setShowCode] = useState(false);
  const [showPreview, setShowPreview] = useState(false);
  const [copied, setCopied] = useState(false);
  const [imgErr, setImgErr] = useState(false);
 
  const doCopy = () => {
    navigator.clipboard.writeText(item.code).then(() => {
      setCopied(true);
      setTimeout(() => setCopied(false), 2500);
    });
  };
 
  const btnBase = {
    background: "transparent",
    border: "0.5px solid var(--color-border-secondary)",
    borderRadius: "var(--border-radius-md)",
    color: "var(--color-text-primary)",
    padding: "5px 11px",
    cursor: "pointer",
    fontSize: 12,
    fontFamily: "inherit",
  };
 
  return (
    <div style={{
      background: "var(--color-background-primary)",
      border: "0.5px solid var(--color-border-tertiary)",
      borderLeft: `3px solid ${accent}`,
      borderRadius: `0 var(--border-radius-lg) var(--border-radius-lg) 0`,
      padding: "14px 16px",
      marginBottom: 8,
    }}>
      <div style={{ display: "flex", alignItems: "center", gap: 8, flexWrap: "wrap", marginBottom: 6 }}>
        <span style={{ fontSize: 14, fontWeight: 500, color: "var(--color-text-primary)", flex: 1, minWidth: 0 }}>{item.name}</span>
        {item.effort && <Pill label={item.effort} />}
      </div>
 
      <p style={{ margin: "0 0 8px", fontSize: 13, color: "var(--color-text-secondary)", lineHeight: 1.6 }}>{item.desc}</p>
 
      {item.caveat && (
        <div style={{ background: "var(--color-background-warning)", borderRadius: "var(--border-radius-md)", padding: "6px 10px", marginBottom: 8 }}>
          <p style={{ margin: 0, fontSize: 12, color: "var(--color-text-warning)", lineHeight: 1.5 }}>⚠ {item.caveat}</p>
        </div>
      )}
 
      {item.where && (
        <p style={{ margin: "0 0 10px", fontSize: 12, color: "var(--color-text-secondary)" }}>
          📍 Place: <span style={{ color: "var(--color-text-info)" }}>{item.where}</span>
        </p>
      )}
 
      <div style={{ display: "flex", gap: 6, flexWrap: "wrap", alignItems: "center" }}>
        <button style={btnBase} onClick={() => setShowCode(v => !v)}>
          {showCode ? "▲ Hide code" : "▼ View code"}
        </button>
        {item.previewUrl && (
          <button style={btnBase} onClick={() => setShowPreview(v => !v)}>
            {showPreview ? "Hide preview" : "👁 See preview"}
          </button>
        )}
        <button
          onClick={doCopy}
          style={{
            ...btnBase,
            marginLeft: "auto",
            background: copied ? "var(--color-background-success)" : "var(--color-background-info)",
            border: copied ? "0.5px solid var(--color-border-success)" : "0.5px solid var(--color-border-info)",
            color: copied ? "var(--color-text-success)" : "var(--color-text-info)",
            fontWeight: 500,
          }}
        >
          {copied ? "✓ Copied!" : "Copy code"}
        </button>
      </div>
 
      {showCode && (
        <div style={{ marginTop: 10, background: "var(--color-background-secondary)", borderRadius: "var(--border-radius-md)", padding: "10px 14px", overflow: "auto" }}>
          <pre style={{ margin: 0, fontFamily: "var(--font-mono)", fontSize: 11, lineHeight: 1.7, color: "var(--color-text-primary)", whiteSpace: "pre-wrap", wordBreak: "break-all" }}>
            {item.code}
          </pre>
        </div>
      )}
 
      {showPreview && item.previewUrl && (
        <div style={{ marginTop: 10, background: "var(--color-background-secondary)", borderRadius: "var(--border-radius-md)", padding: "10px 14px" }}>
          <p style={{ margin: "0 0 8px", fontSize: 11, color: "var(--color-text-secondary)" }}>Live render using your GitHub username:</p>
          {!imgErr && (
            <img src={item.previewUrl} alt={`Preview: ${item.name}`} style={{ maxWidth: "100%", display: "block", borderRadius: 4 }} onError={() => setImgErr(true)} />
          )}
          <a href={item.previewUrl} style={{ fontSize: 11, color: "var(--color-text-info)", display: "block", marginTop: 8 }}>
            ↗ Open preview in browser
          </a>
        </div>
      )}
    </div>
  );
}
 
function Section({ title, sub, type, items }) {
  const s = BADGE[type];
  return (
    <div style={{ marginBottom: 28 }}>
      <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 12, paddingBottom: 8, borderBottom: "0.5px solid var(--color-border-tertiary)" }}>
        <span style={{ background: s.bg, color: s.color, fontSize: 10, fontWeight: 500, padding: "2px 8px", borderRadius: "var(--border-radius-md)", letterSpacing: "0.03em" }}>
          {title}
        </span>
        <span style={{ fontSize: 12, color: "var(--color-text-secondary)" }}>{sub}</span>
      </div>
      {items.map(item => <Card key={item.id} item={item} accent={ACCENTS[type]} />)}
    </div>
  );
}
 
function SkipCard({ item }) {
  return (
    <div style={{ background: "var(--color-background-primary)", border: "0.5px solid var(--color-border-tertiary)", borderLeft: `3px solid ${ACCENTS.danger}`, borderRadius: `0 var(--border-radius-md) var(--border-radius-md) 0`, padding: "10px 14px", marginBottom: 6 }}>
      <p style={{ margin: "0 0 3px", fontSize: 13, fontWeight: 500, color: "var(--color-text-primary)" }}>✕ {item.name}</p>
      <p style={{ margin: 0, fontSize: 12, color: "var(--color-text-secondary)", lineHeight: 1.5 }}>{item.reason}</p>
    </div>
  );
}
 
export default function App() {
  const [showSkip, setShowSkip] = useState(false);
 
  return (
    <div style={{ maxWidth: 680, padding: "4px 0" }}>
      <div style={{ marginBottom: 24 }}>
        <p style={{ margin: "0 0 4px", fontSize: 14, fontWeight: 500, color: "var(--color-text-primary)" }}>
          GitHub README visual kit
        </p>
        <p style={{ margin: 0, fontSize: 12, color: "var(--color-text-secondary)" }}>
          Ranked by impact. Everything is free. Start at the top — must-haves take ~20 minutes total.
        </p>
      </div>
 
      <Section title="MUST-HAVE" sub="Do these first — ~20 minutes total" type="success" items={MUST_HAVE} />
      <Section title="NICE-TO-HAVE" sub="Add once your repos are more active" type="warning" items={NICE_TO_HAVE} />
 
      <div>
        <button
          onClick={() => setShowSkip(v => !v)}
          style={{ width: "100%", textAlign: "left", background: "transparent", border: "0.5px solid var(--color-border-secondary)", borderRadius: "var(--border-radius-md)", color: "var(--color-text-secondary)", padding: "8px 12px", cursor: "pointer", fontSize: 13, fontFamily: "inherit", display: "flex", alignItems: "center", gap: 8 }}
        >
          <span>{showSkip ? "▲" : "▼"}</span>
          <span style={{ color: "var(--color-text-danger)", fontWeight: 500 }}>Skip these</span>
          <span>— {SKIP.length} things that hurt more than help right now</span>
        </button>
        {showSkip && <div style={{ marginTop: 8 }}>{SKIP.map(item => <SkipCard key={item.id} item={item} />)}</div>}
      </div>
 
      <p style={{ margin: "24px 0 0", paddingTop: 16, borderTop: "0.5px solid var(--color-border-tertiary)", fontSize: 11, color: "var(--color-text-secondary)", textAlign: "center" }}>
        All tools free · No sign-up needed (except snake animation requires GitHub Actions)
      </p>
    </div>
  );
}
