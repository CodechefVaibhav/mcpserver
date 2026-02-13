<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>MCP Server Architecture — Spring Boot 2.x</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600;700&family=Syne:wght@400;600;700;800&display=swap');

  :root {
    --bg: #0a0e1a;
    --surface: #0f1525;
    --surface2: #151d30;
    --border: #1e2d4a;
    --accent: #00d4ff;
    --accent2: #7c3aed;
    --accent3: #10b981;
    --accent4: #f59e0b;
    --accent5: #ef4444;
    --text: #e2e8f0;
    --muted: #64748b;
    --code: #94a3b8;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── grid bg ── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .wrapper {
    position: relative;
    z-index: 1;
    max-width: 1300px;
    margin: 0 auto;
    padding: 40px 32px 80px;
  }

  /* ── header ── */
  header {
    text-align: center;
    margin-bottom: 56px;
  }
  header .badge {
    display: inline-block;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--accent);
    border: 1px solid rgba(0,212,255,0.3);
    padding: 6px 16px;
    border-radius: 100px;
    margin-bottom: 20px;
    background: rgba(0,212,255,0.05);
  }
  header h1 {
    font-size: clamp(28px, 5vw, 48px);
    font-weight: 800;
    line-height: 1.1;
    margin-bottom: 12px;
    background: linear-gradient(135deg, #e2e8f0 30%, var(--accent) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  header p {
    color: var(--muted);
    font-size: 15px;
    font-family: 'JetBrains Mono', monospace;
  }

  /* ── tabs ── */
  .tabs {
    display: flex;
    gap: 8px;
    margin-bottom: 32px;
    border-bottom: 1px solid var(--border);
    padding-bottom: 0;
    flex-wrap: wrap;
  }
  .tab-btn {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    font-weight: 600;
    padding: 10px 20px;
    background: transparent;
    color: var(--muted);
    border: none;
    border-bottom: 2px solid transparent;
    cursor: pointer;
    transition: all 0.2s;
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: -1px;
  }
  .tab-btn:hover { color: var(--text); }
  .tab-btn.active {
    color: var(--accent);
    border-bottom-color: var(--accent);
  }
  .tab-panel { display: none; }
  .tab-panel.active { display: block; }

  /* ── diagram canvas ── */
  .diagram-canvas {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 40px 32px;
    position: relative;
    overflow: hidden;
  }
  .diagram-canvas::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent), transparent);
    opacity: 0.6;
  }

  /* ── plantuml source box ── */
  .plantuml-src {
    background: #070b14;
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    line-height: 1.7;
    color: var(--code);
    overflow-x: auto;
    white-space: pre;
    margin-top: 0;
  }
  .kw   { color: #7c3aed; }
  .str  { color: #10b981; }
  .cmt  { color: #475569; font-style: italic; }
  .node { color: #00d4ff; }
  .arr  { color: #f59e0b; }
  .lbl  { color: #e2e8f0; }
  .anot { color: #f59e0b; }

  /* ── diagram legend ── */
  .legend {
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
    margin-bottom: 32px;
  }
  .legend-item {
    display: flex;
    align-items: center;
    gap: 8px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--muted);
  }
  .legend-dot {
    width: 12px; height: 12px;
    border-radius: 3px;
    flex-shrink: 0;
  }

  /* ── SVG Diagram ── */
  svg.arch { width: 100%; height: auto; }

  /* ── layers ── */
  .layer-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 12px;
    margin-top: 28px;
  }
  .layer-label:first-child { margin-top: 0; }

  /* ── boxes ── */
  .boxes-row {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    margin-bottom: 8px;
  }
  .box {
    flex: 1;
    min-width: 160px;
    border-radius: 10px;
    padding: 14px 16px;
    position: relative;
    border: 1px solid;
    transition: transform 0.2s, box-shadow 0.2s;
    cursor: default;
  }
  .box:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(0,0,0,0.4);
  }
  .box .box-title {
    font-size: 13px;
    font-weight: 700;
    margin-bottom: 4px;
    font-family: 'JetBrains Mono', monospace;
  }
  .box .box-sub {
    font-size: 11px;
    color: var(--muted);
    font-family: 'JetBrains Mono', monospace;
    line-height: 1.5;
  }
  .box .box-badge {
    position: absolute;
    top: 8px; right: 10px;
    font-size: 9px;
    font-family: 'JetBrains Mono', monospace;
    padding: 2px 6px;
    border-radius: 4px;
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  /* box color variants */
  .box-ai {
    background: rgba(124,58,237,0.1);
    border-color: rgba(124,58,237,0.4);
  }
  .box-ai .box-title { color: #a78bfa; }
  .box-ai .box-badge { background: rgba(124,58,237,0.2); color: #a78bfa; }

  .box-mcp {
    background: rgba(0,212,255,0.08);
    border-color: rgba(0,212,255,0.35);
  }
  .box-mcp .box-title { color: var(--accent); }
  .box-mcp .box-badge { background: rgba(0,212,255,0.15); color: var(--accent); }

  .box-spring {
    background: rgba(16,185,129,0.08);
    border-color: rgba(16,185,129,0.35);
  }
  .box-spring .box-title { color: #34d399; }
  .box-spring .box-badge { background: rgba(16,185,129,0.15); color: #34d399; }

  .box-service {
    background: rgba(245,158,11,0.08);
    border-color: rgba(245,158,11,0.35);
  }
  .box-service .box-title { color: #fbbf24; }
  .box-service .box-badge { background: rgba(245,158,11,0.15); color: #fbbf24; }

  .box-infra {
    background: rgba(239,68,68,0.08);
    border-color: rgba(239,68,68,0.3);
  }
  .box-infra .box-title { color: #f87171; }
  .box-infra .box-badge { background: rgba(239,68,68,0.15); color: #f87171; }

  /* ── arrows between layers ── */
  .flow-arrow {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding: 6px 0;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
  }
  .flow-arrow .arrow-line {
    flex: 1;
    height: 1px;
    max-width: 80px;
  }
  .flow-arrow .arrow-label {
    color: var(--muted);
    font-size: 10px;
    letter-spacing: 1px;
    padding: 3px 10px;
    border-radius: 4px;
    background: var(--surface2);
    border: 1px solid var(--border);
  }
  .fa-down::after {
    content: '▼';
    font-size: 10px;
    margin-left: 4px;
  }

  /* ── sequence diagram ── */
  .seq-container {
    overflow-x: auto;
  }
  .seq-diagram {
    min-width: 700px;
    padding: 8px 0;
  }
  .seq-actors {
    display: flex;
    gap: 0;
    margin-bottom: 0;
  }
  .seq-actor {
    flex: 1;
    text-align: center;
    padding: 10px 8px;
    border-radius: 8px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    font-weight: 700;
    border: 1px solid;
    margin: 0 4px;
  }
  .seq-lifelines {
    position: relative;
    min-height: 480px;
    margin: 0 4px;
  }
  .lifeline {
    position: absolute;
    top: 0; bottom: 0;
    width: 1px;
    border-left: 1px dashed;
    opacity: 0.3;
  }
  .seq-msg {
    position: absolute;
    left: 0; right: 0;
    display: flex;
    align-items: center;
    height: 0;
  }
  .seq-msg-line {
    height: 1px;
    background: currentColor;
    position: absolute;
  }
  .seq-msg-label {
    position: absolute;
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    white-space: nowrap;
    padding: 2px 6px;
    border-radius: 3px;
    transform: translateY(-14px);
  }
  .seq-msg-arrow {
    position: absolute;
    font-size: 10px;
  }

  /* ── component grid ── */
  .component-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 16px;
    margin-top: 8px;
  }
  .component-card {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 18px 16px;
    position: relative;
    overflow: hidden;
    transition: border-color 0.2s, transform 0.2s;
  }
  .component-card:hover {
    transform: translateY(-2px);
    border-color: var(--accent);
  }
  .component-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; height: 2px;
  }
  .component-card.c-ai::before   { background: #7c3aed; }
  .component-card.c-mcp::before  { background: var(--accent); }
  .component-card.c-svc::before  { background: var(--accent3); }
  .component-card.c-sec::before  { background: var(--accent5); }
  .component-card.c-obs::before  { background: var(--accent4); }

  .component-card .c-icon {
    font-size: 24px;
    margin-bottom: 10px;
    display: block;
  }
  .component-card .c-name {
    font-size: 14px;
    font-weight: 700;
    font-family: 'JetBrains Mono', monospace;
    margin-bottom: 6px;
  }
  .component-card .c-desc {
    font-size: 11px;
    color: var(--muted);
    line-height: 1.6;
    font-family: 'JetBrains Mono', monospace;
  }
  .component-card .c-tag {
    display: inline-block;
    font-size: 9px;
    font-family: 'JetBrains Mono', monospace;
    padding: 2px 7px;
    border-radius: 4px;
    margin-top: 8px;
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  /* ── plantuml source ── */
  .copy-btn {
    position: absolute;
    top: 12px; right: 12px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    padding: 5px 12px;
    background: var(--surface2);
    border: 1px solid var(--border);
    color: var(--muted);
    border-radius: 6px;
    cursor: pointer;
    transition: all 0.15s;
    letter-spacing: 1px;
  }
  .copy-btn:hover {
    background: var(--accent);
    color: var(--bg);
    border-color: var(--accent);
  }

  /* ── data flow diagram ── */
  .dataflow {
    display: flex;
    flex-direction: column;
    gap: 0;
  }
  .df-step {
    display: flex;
    align-items: stretch;
    gap: 16px;
  }
  .df-connector {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 40px;
    flex-shrink: 0;
  }
  .df-node-num {
    width: 32px; height: 32px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    font-weight: 700;
    flex-shrink: 0;
    z-index: 1;
  }
  .df-vert-line {
    width: 2px;
    flex: 1;
    min-height: 24px;
  }
  .df-content {
    flex: 1;
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 14px 16px;
    margin-bottom: 8px;
    position: relative;
  }
  .df-content .df-title {
    font-size: 13px;
    font-weight: 700;
    font-family: 'JetBrains Mono', monospace;
    margin-bottom: 4px;
  }
  .df-content .df-detail {
    font-size: 11px;
    color: var(--muted);
    font-family: 'JetBrains Mono', monospace;
    line-height: 1.6;
  }
  .df-content .df-payload {
    margin-top: 8px;
    padding: 6px 10px;
    background: #070b14;
    border-radius: 6px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    color: #10b981;
    border: 1px solid var(--border);
  }

  @media (max-width: 640px) {
    .wrapper { padding: 20px 16px 60px; }
    .boxes-row { flex-direction: column; }
    .diagram-canvas { padding: 20px 16px; }
  }

  /* ── author card ── */
  .author-block {
    display: inline-flex;
    align-items: center;
    gap: 14px;
    margin-top: 24px;
    padding: 12px 20px;
    background: rgba(0,212,255,0.05);
    border: 1px solid rgba(0,212,255,0.18);
    border-radius: 50px;
    backdrop-filter: blur(4px);
  }
  .author-avatar {
    width: 40px; height: 40px;
    border-radius: 50%;
    background: linear-gradient(135deg, #7c3aed, #00d4ff);
    display: flex; align-items: center; justify-content: center;
    font-size: 16px; font-weight: 800;
    color: #fff;
    font-family: 'Syne', sans-serif;
    flex-shrink: 0;
    box-shadow: 0 0 0 2px rgba(0,212,255,0.3);
  }
  .author-info { text-align: left; }
  .author-name {
    font-size: 14px;
    font-weight: 700;
    color: var(--text);
    font-family: 'Syne', sans-serif;
    letter-spacing: 0.3px;
  }
  .author-meta {
    font-size: 11px;
    color: var(--muted);
    font-family: 'JetBrains Mono', monospace;
    margin-top: 2px;
  }
  .author-divider {
    width: 1px; height: 28px;
    background: rgba(0,212,255,0.2);
    margin: 0 4px;
  }
  .author-stats {
    display: flex;
    flex-direction: column;
    gap: 2px;
  }
  .author-stat {
    font-size: 10px;
    font-family: 'JetBrains Mono', monospace;
    color: var(--muted);
    white-space: nowrap;
  }
  .author-stat span {
    color: var(--accent);
    font-weight: 600;
  }
</style>
</head>
<body>
<div class="wrapper">

  <header>
    <div class="badge">Architecture Diagram · leaveApp + leaveapp-agent · MCP + Spring Boot 2.x</div>
    <h1>leaveApp MCP Server Architecture<br>for AI Agent Integration</h1>
    <p>leaveApp (Spring Boot 2.7.x) · leaveapp-agent (OpenAI tool-calling) · JSON-RPC 2.0</p>

    <div class="author-block">
      <div class="author-avatar">VK</div>
      <div class="author-info">
        <div class="author-name">Vaibhav Kashyap</div>
        <div class="author-meta">Principal Architect · PeopleStrong · 14+ yrs</div>
      </div>
      <div class="author-divider"></div>
      <div class="author-stats">
        <div class="author-stat"><span>Spring Boot</span> · MCP · AI Agents</div>
        <div class="author-stat">Published on <span>Medium</span></div>
      </div>
    </div>
  </header>

  <div class="tabs">
    <button class="tab-btn active" onclick="switchTab('overview')">Overview</button>
    <button class="tab-btn" onclick="switchTab('sequence')">Request Flow</button>
    <button class="tab-btn" onclick="switchTab('components')">Components</button>
    <button class="tab-btn" onclick="switchTab('plantuml')">PlantUML Source</button>
  </div>

  <!-- ══════════════════════════════════════════════ TAB 1 — OVERVIEW ══ -->
  <div class="tab-panel active" id="tab-overview">
    <div class="diagram-canvas">

      <div class="legend">
        <div class="legend-item"><div class="legend-dot" style="background:#a78bfa"></div>AI / Agent Layer</div>
        <div class="legend-item"><div class="legend-dot" style="background:#00d4ff"></div>MCP Protocol Layer</div>
        <div class="legend-item"><div class="legend-dot" style="background:#34d399"></div>Spring Boot Core</div>
        <div class="legend-item"><div class="legend-dot" style="background:#fbbf24"></div>Business Services</div>
        <div class="legend-item"><div class="legend-dot" style="background:#f87171"></div>Infrastructure</div>
      </div>

      <!-- LAYER 1: AI AGENT -->
      <div class="layer-label">[ Layer 1 ] &nbsp;AI Agent — leaveapp-agent (port 8090)</div>
      <div class="boxes-row">
        <div class="box box-ai">
          <span class="box-badge">LLM</span>
          <div class="box-title">OpenAI GPT-4</div>
          <div class="box-sub">Chat Completions API<br>Tool-calling enabled<br>Reads leave tool schemas</div>
        </div>
        <div class="box box-ai">
          <span class="box-badge">agent loop</span>
          <div class="box-title">AgentService</div>
          <div class="box-sub">POST /api/agent/chat<br>userId-scoped conversations<br>Stores msgs + tool traces in agent_db</div>
        </div>
        <div class="box box-ai">
          <span class="box-badge">webclient</span>
          <div class="box-title">REST Tool Adapters</div>
          <div class="box-sub">WebClient → leaveApp :8082<br>findEmployeeByName · applyLeave<br>approveLeave · getBalance · …</div>
        </div>
      </div>

      <div class="flow-arrow">
        <div class="arrow-line" style="background:linear-gradient(90deg,transparent,rgba(124,58,237,0.5))"></div>
        <div class="arrow-label">HTTP POST · X-MCP-API-Key · JSON-RPC 2.0  ·  leaveapp-agent → leaveApp :8082 ▼</div>
        <div class="arrow-line" style="background:linear-gradient(90deg,rgba(124,58,237,0.5),transparent)"></div>
      </div>

      <!-- LAYER 2: MCP PROTOCOL -->
      <div class="layer-label">[ Layer 2 ] &nbsp;leaveApp — Spring Boot 2.7.x · Java 17 (port 8082)</div>
      <div class="boxes-row">
        <div class="box box-mcp">
          <span class="box-badge">filter</span>
          <div class="box-title">ApiKeyFilter</div>
          <div class="box-sub">OncePerRequestFilter<br>Validates X-MCP-API-Key header</div>
        </div>
        <div class="box box-mcp">
          <span class="box-badge">controller</span>
          <div class="box-title">McpController</div>
          <div class="box-sub">POST /mcp<br>initialize · tools/list<br>tools/call · ping</div>
        </div>
        <div class="box box-mcp">
          <span class="box-badge">REST API</span>
          <div class="box-title">LeaveController</div>
          <div class="box-sub">/api/employees · /api/leaves<br>apply · approve · reject<br>withdraw · balance · pending</div>
        </div>
        <div class="box box-mcp">
          <span class="box-badge">registry</span>
          <div class="box-title">McpToolRegistry</div>
          <div class="box-sub">Scans @McpToolDef beans<br>Generates JSON Schema<br>Invokes via reflection</div>
        </div>
      </div>

      <div class="flow-arrow">
        <div class="arrow-line" style="background:linear-gradient(90deg,transparent,rgba(0,212,255,0.5))"></div>
        <div class="arrow-label">Spring @Component scan · Method invocation ▼</div>
        <div class="arrow-line" style="background:linear-gradient(90deg,rgba(0,212,255,0.5),transparent)"></div>
      </div>

      <!-- LAYER 3: SPRING CORE -->
      <div class="layer-label">[ Layer 3 ] &nbsp;Spring Boot Core + Cross-Cutting Concerns</div>
      <div class="boxes-row">
        <div class="box box-spring">
          <span class="box-badge">security</span>
          <div class="box-title">Spring Security</div>
          <div class="box-sub">WebSecurityConfigurerAdapter<br>Stateless · CSRF disabled<br>Role-based access</div>
        </div>
        <div class="box box-spring">
          <span class="box-badge">aop</span>
          <div class="box-title">ObservabilityAspect</div>
          <div class="box-sub">@Around @McpToolDef<br>Micrometer metrics<br>Structured MDC logging</div>
        </div>
        <div class="box box-spring">
          <span class="box-badge">resilience</span>
          <div class="box-title">Resilience4j</div>
          <div class="box-sub">@RateLimiter per API key<br>@CircuitBreaker on services<br>@TimeLimiter for timeouts</div>
        </div>
        <div class="box box-spring">
          <span class="box-badge">validation</span>
          <div class="box-title">Bean Validation</div>
          <div class="box-sub">@Valid on tool inputs<br>@NotBlank · @Size<br>@ControllerAdvice handler</div>
        </div>
      </div>

      <div class="flow-arrow">
        <div class="arrow-line" style="background:linear-gradient(90deg,transparent,rgba(16,185,129,0.5))"></div>
        <div class="arrow-label">Spring DI · @Autowired · @Transactional ▼</div>
        <div class="arrow-line" style="background:linear-gradient(90deg,rgba(16,185,129,0.5),transparent)"></div>
      </div>

      <!-- LAYER 4: BUSINESS SERVICES -->
      <div class="layer-label">[ Layer 4 ] &nbsp;leaveApp Domain — controller · service · repository · domain · dto</div>
      <div class="boxes-row">
        <div class="box box-service">
          <span class="box-badge">tool bean</span>
          <div class="box-title">LeaveTools</div>
          <div class="box-sub">@McpToolDef applyLeave<br>@McpToolDef withdrawLeave<br>@McpToolDef approveLeave<br>@McpToolDef rejectLeave</div>
        </div>
        <div class="box box-service">
          <span class="box-badge">tool bean</span>
          <div class="box-title">EmployeeTools</div>
          <div class="box-sub">@McpToolDef listEmployees<br>@McpToolDef getEmployee<br>@McpToolDef getLeaveBalance<br>@McpToolDef getPendingLeaves</div>
        </div>
        <div class="box box-service">
          <span class="box-badge">service</span>
          <div class="box-title">LeaveService</div>
          <div class="box-sub">12 leaves/yr per employee<br>APPLY→PENDING · APPROVE/REJECT<br>Only mgr can approve · actor rules</div>
        </div>
        <div class="box box-service">
          <span class="box-badge">service</span>
          <div class="box-title">EmployeeService</div>
          <div class="box-sub">Pre-registered employees<br>No auth · Flyway seed data<br>Manager hierarchy lookup</div>
        </div>
      </div>

      <div class="flow-arrow">
        <div class="arrow-line" style="background:linear-gradient(90deg,transparent,rgba(245,158,11,0.5))"></div>
        <div class="arrow-label">JPA · JDBC · REST · gRPC ▼</div>
        <div class="arrow-line" style="background:linear-gradient(90deg,rgba(245,158,11,0.5),transparent)"></div>
      </div>

      <!-- LAYER 5: INFRA -->
      <div class="layer-label">[ Layer 5 ] &nbsp;Infrastructure · Docker Compose</div>
      <div class="boxes-row">
        <div class="box box-infra">
          <span class="box-badge">leaveApp DB</span>
          <div class="box-title">PostgreSQL</div>
          <div class="box-sub">leaveapp schema<br>Flyway migrations + seed<br>employees · leave_requests</div>
        </div>
        <div class="box box-infra">
          <span class="box-badge">agent DB</span>
          <div class="box-title">agent_db (PostgreSQL)</div>
          <div class="box-sub">leaveapp-agent schema<br>conversations · messages<br>tool invocation traces</div>
        </div>
        <div class="box box-infra">
          <span class="box-badge">rate limit</span>
          <div class="box-title">Rate Limiter</div>
          <div class="box-sub">30 req/min per userId<br>429 on breach<br>Redis / in-mem bucket</div>
        </div>
        <div class="box box-infra">
          <span class="box-badge">metrics</span>
          <div class="box-title">Prometheus + Grafana</div>
          <div class="box-sub">mcp.tool.calls counter<br>mcp.tool.duration timer<br>agent chat latency</div>
        </div>
      </div>

    </div>
  </div>

  <!-- ══════════════════════════════════════════════ TAB 2 — SEQUENCE ══ -->
  <div class="tab-panel" id="tab-sequence">
    <div class="diagram-canvas">
      <div class="dataflow">

        <!-- Step 1 -->
        <div class="df-step">
          <div class="df-connector">
            <div class="df-node-num" style="background:rgba(124,58,237,0.2);color:#a78bfa;border:2px solid #7c3aed">1</div>
            <div class="df-vert-line" style="background:linear-gradient(180deg,#7c3aed33,#00d4ff33)"></div>
          </div>
          <div class="df-content" style="border-color:#7c3aed44">
            <div class="df-title" style="color:#a78bfa">User → leaveapp-agent: Natural language chat</div>
            <div class="df-detail">User sends a plain-English leave request to the agent microservice. AgentService resolves conversation history from agent_db and rate-checks (30 req/min per userId).</div>
            <div class="df-payload">POST http://localhost:8090/api/agent/chat<br>{"userId":"demo-user",<br> "message":"Apply leave for Bob from 2026-03-01 to 2026-03-03 reason: family function"}</div>
          </div>
        </div>

        <!-- Step 2 -->
        <div class="df-step">
          <div class="df-connector">
            <div class="df-node-num" style="background:rgba(0,212,255,0.15);color:#00d4ff;border:2px solid #00d4ff44">2</div>
            <div class="df-vert-line" style="background:linear-gradient(180deg,#00d4ff33,#00d4ff22)"></div>
          </div>
          <div class="df-content" style="border-color:#00d4ff33">
            <div class="df-title" style="color:#00d4ff">AgentService → OpenAI: Chat Completions with tools</div>
            <div class="df-detail">AgentService appends conversation history + registered tool schemas (findEmployeeByName, applyLeave, getLeaveBalance…) and sends to OpenAI GPT-4 Chat Completions API.</div>
            <div class="df-payload">POST https://api.openai.com/v1/chat/completions<br>{"model":"gpt-4","messages":[...],"tools":[<br>  {"type":"function","function":{"name":"findEmployeeByName","parameters":{...}}},<br>  {"type":"function","function":{"name":"applyLeave","parameters":{...}}}]}</div>
          </div>
        </div>

        <!-- Step 3 -->
        <div class="df-step">
          <div class="df-connector">
            <div class="df-node-num" style="background:rgba(0,212,255,0.15);color:#00d4ff;border:2px solid #00d4ff44">3</div>
            <div class="df-vert-line" style="background:linear-gradient(180deg,#00d4ff22,#10b98133)"></div>
          </div>
          <div class="df-content" style="border-color:#00d4ff33">
            <div class="df-title" style="color:#00d4ff">OpenAI → AgentService: tool_calls[findEmployeeByName]</div>
            <div class="df-detail">LLM decides it needs Bob's employeeId first. Returns a tool_call for findEmployeeByName before it can build the applyLeave arguments.</div>
            <div class="df-payload">{"finish_reason":"tool_calls","message":{"tool_calls":[<br>  {"id":"call_1","function":{"name":"findEmployeeByName",<br>   "arguments":"{\"name\":\"Bob\"}"}}]}}</div>
          </div>
        </div>

        <!-- Step 4 -->
        <div class="df-step">
          <div class="df-connector">
            <div class="df-node-num" style="background:rgba(16,185,129,0.15);color:#34d399;border:2px solid #10b98144">4</div>
            <div class="df-vert-line" style="background:linear-gradient(180deg,#10b98133,#f59e0b33)"></div>
          </div>
          <div class="df-content" style="border-color:#10b98144">
            <div class="df-title" style="color:#34d399">REST Tool Adapter → leaveApp: GET /api/employees</div>
            <div class="df-detail">WebClient calls leaveApp's employee endpoint. leaveApp looks up employee by name from PostgreSQL (Flyway seed data). Returns matching employee record.</div>
            <div class="df-payload">GET http://leaveapp:8082/api/employees<br>← [{"id":2,"name":"Bob","managerId":1,...}]<br>Tool result: "1 match — employeeId=2"</div>
          </div>
        </div>

        <!-- Step 5 -->
        <div class="df-step">
          <div class="df-connector">
            <div class="df-node-num" style="background:rgba(245,158,11,0.15);color:#fbbf24;border:2px solid #f59e0b44">5</div>
            <div class="df-vert-line" style="background:linear-gradient(180deg,#f59e0b33,#f59e0b22)"></div>
          </div>
          <div class="df-content" style="border-color:#f59e0b44">
            <div class="df-title" style="color:#fbbf24">OpenAI → AgentService: tool_calls[applyLeave]</div>
            <div class="df-detail">With Bob's employeeId resolved, LLM now constructs the full applyLeave arguments. actorEmployeeId = employeeId (employee applies for themselves). Status will become PENDING.</div>
            <div class="df-payload">{"tool_calls":[{"function":{"name":"applyLeave",<br>  "arguments":"{\"actorEmployeeId\":2,\"employeeId\":2,<br>   \"startDate\":\"2026-03-01\",\"endDate\":\"2026-03-03\",<br>   \"comment\":\"family function\"}"}}]}</div>
          </div>
        </div>

        <!-- Step 6 -->
        <div class="df-step">
          <div class="df-connector">
            <div class="df-node-num" style="background:rgba(245,158,11,0.15);color:#fbbf24;border:2px solid #f59e0b44">6</div>
            <div class="df-vert-line" style="background:linear-gradient(180deg,#f59e0b22,#f59e0b22)"></div>
          </div>
          <div class="df-content" style="border-color:#f59e0b44">
            <div class="df-title" style="color:#fbbf24">REST Tool Adapter → leaveApp: POST /api/leaves/apply</div>
            <div class="df-detail">LeaveService validates: actor == employee (can only apply for self), balance check (12 leaves/yr, only APPROVED count), comment not blank. Days = endDate - startDate + 1 = 3. Creates PENDING request.</div>
            <div class="df-payload">POST http://leaveapp:8082/api/leaves/apply<br>{"actorEmployeeId":2,"employeeId":2,<br> "startDate":"2026-03-01","endDate":"2026-03-03","comment":"family function"}<br>← {"id":5,"status":"PENDING","days":3}</div>
          </div>
        </div>

        <!-- Step 7 -->
        <div class="df-step">
          <div class="df-connector">
            <div class="df-node-num" style="background:rgba(0,212,255,0.15);color:#00d4ff;border:2px solid #00d4ff44">7</div>
            <div class="df-vert-line" style="background:linear-gradient(180deg,#00d4ff22,#7c3aed22)"></div>
          </div>
          <div class="df-content" style="border-color:#00d4ff33">
            <div class="df-title" style="color:#00d4ff">AgentService → OpenAI: tool results → final answer</div>
            <div class="df-detail">All tool results fed back to LLM. LLM synthesizes a natural-language response. AgentService persists conversation + tool trace (toolCalls array + traceId) to agent_db.</div>
            <div class="df-payload">{"finish_reason":"stop","message":{"content":<br> "Leave applied for Bob (2026-03-01 → 2026-03-03, 3 days). Status: PENDING."}}</div>
          </div>
        </div>

        <!-- Step 8 -->
        <div class="df-step">
          <div class="df-connector">
            <div class="df-node-num" style="background:rgba(124,58,237,0.2);color:#a78bfa;border:2px solid #7c3aed">8</div>
          </div>
          <div class="df-content" style="border-color:#7c3aed44">
            <div class="df-title" style="color:#a78bfa">leaveapp-agent → User: structured JSON response</div>
            <div class="df-detail">AgentService returns the final answer with full tool call audit trail, conversationId for multi-turn continuity, and traceId for observability.</div>
            <div class="df-payload">{"answer":"Leave applied successfully for Bob (2026-03-01 to 2026-03-03).",<br> "toolCalls":[{"tool":"findEmployeeByName","args":{"name":"Bob"},"resultSnippet":"1 match"},<br>              {"tool":"applyLeave","args":{...},"resultSnippet":"PENDING"}],<br> "conversationId":"f9c6e1a4-...","traceId":"4e8d7a7f-..."}</div>
          </div>
        </div>

      </div>
    </div>
  </div>

  <!-- ══════════════════════════════════════════════ TAB 3 — COMPONENTS ══ -->
  <div class="tab-panel" id="tab-components">
    <div class="diagram-canvas">
      <div class="component-grid">

        <div class="component-card c-ai">
          <span class="c-icon">🤖</span>
          <div class="c-name">AgentService (leaveapp-agent)</div>
          <div class="c-desc">POST /api/agent/chat entry point. Maintains conversationId for multi-turn. Rate-limits 30 req/min per userId. Stores messages + tool invocations in agent_db.</div>
          <span class="c-tag" style="background:rgba(124,58,237,0.15);color:#a78bfa">AGENT</span>
        </div>

        <div class="component-card c-ai">
          <span class="c-icon">⚡</span>
          <div class="c-name">OpenAI Tool Adapters</div>
          <div class="c-desc">WebClient-based REST adapters calling leaveApp :8082. Tools: findEmployeeByName, applyLeave, withdrawLeave, approveLeave, rejectLeave, getLeaveBalance, getPendingLeaves, getLeaveById.</div>
          <span class="c-tag" style="background:rgba(124,58,237,0.15);color:#a78bfa">TOOLS</span>
        </div>

        <div class="component-card c-mcp">
          <span class="c-icon">🔀</span>
          <div class="c-name">McpController</div>
          <div class="c-desc">@RestController at POST /mcp on leaveApp. Switch-dispatches on JSON-RPC method: initialize, tools/list, tools/call, ping.</div>
          <span class="c-tag" style="background:rgba(0,212,255,0.1);color:#00d4ff">CONTROLLER</span>
        </div>

        <div class="component-card c-mcp">
          <span class="c-icon">📋</span>
          <div class="c-name">McpToolRegistry</div>
          <div class="c-desc">ApplicationContextAware. Scans @McpToolDef on startup. Generates JSON Schema via victools from LeaveApplyInput, EmployeeQueryInput DTOs. Dispatches via reflection.</div>
          <span class="c-tag" style="background:rgba(0,212,255,0.1);color:#00d4ff">REGISTRY</span>
        </div>

        <div class="component-card c-mcp">
          <span class="c-icon">🌐</span>
          <div class="c-name">LeaveController (REST)</div>
          <div class="c-desc">/api/employees · /api/leaves/apply · /api/leaves/{id}/approve · /api/leaves/{id}/reject · /api/leaves/{id}/withdraw · /api/leaves/balance · /api/leaves/pending</div>
          <span class="c-tag" style="background:rgba(0,212,255,0.1);color:#00d4ff">REST API</span>
        </div>

        <div class="component-card c-svc">
          <span class="c-icon">🔧</span>
          <div class="c-name">LeaveTools</div>
          <div class="c-desc">@McpToolDef applyLeave — actor must == employee. @McpToolDef withdrawLeave — only PENDING, only own. @McpToolDef approveLeave / rejectLeave — only manager, only PENDING.</div>
          <span class="c-tag" style="background:rgba(16,185,129,0.1);color:#34d399">TOOL BEAN</span>
        </div>

        <div class="component-card c-svc">
          <span class="c-icon">👥</span>
          <div class="c-name">EmployeeTools</div>
          <div class="c-desc">@McpToolDef listEmployees, getEmployee, getLeaveBalance (available = 12 − approved days in year), getPendingLeaves (for manager). All read-only.</div>
          <span class="c-tag" style="background:rgba(16,185,129,0.1);color:#34d399">TOOL BEAN</span>
        </div>

        <div class="component-card c-svc">
          <span class="c-icon">⚙️</span>
          <div class="c-name">LeaveService</div>
          <div class="c-desc">Core business rules: 12 leaves/yr, days = end−start+1, APPLY→PENDING, actor validation, manager-only approve/reject, only APPROVED leaves deduct balance.</div>
          <span class="c-tag" style="background:rgba(16,185,129,0.1);color:#34d399">SERVICE</span>
        </div>

        <div class="component-card c-sec">
          <span class="c-icon">🔐</span>
          <div class="c-name">ApiKeyFilter</div>
          <div class="c-desc">OncePerRequestFilter on leaveApp. Validates X-MCP-API-Key header from leaveapp-agent. Sets PreAuthenticatedAuthenticationToken on SecurityContext.</div>
          <span class="c-tag" style="background:rgba(239,68,68,0.1);color:#f87171">SECURITY</span>
        </div>

        <div class="component-card c-sec">
          <span class="c-icon">⏱️</span>
          <div class="c-name">Rate Limiter</div>
          <div class="c-desc">leaveapp-agent enforces 30 requests/min per userId. Returns HTTP 429 on breach. Prevents agent loop run-away tool call storms.</div>
          <span class="c-tag" style="background:rgba(239,68,68,0.1);color:#f87171">RATE LIMIT</span>
        </div>

        <div class="component-card c-obs">
          <span class="c-icon">📊</span>
          <div class="c-name">McpObservabilityAspect</div>
          <div class="c-desc">@Around @McpToolDef on leaveApp. Tracks mcp.tool.calls, mcp.tool.duration, mcp.tool.errors via Micrometer. MDC: toolName, actorId, durationMs.</div>
          <span class="c-tag" style="background:rgba(245,158,11,0.1);color:#fbbf24">OBSERVABILITY</span>
        </div>

        <div class="component-card c-svc">
          <span class="c-icon">🗄️</span>
          <div class="c-name">Flyway + PostgreSQL</div>
          <div class="c-desc">leaveApp: employees + leave_requests tables with seed data. leaveapp-agent: agent_db with conversations, messages, tool_invocations tables for full audit trail.</div>
          <span class="c-tag" style="background:rgba(16,185,129,0.1);color:#34d399">DATABASE</span>
        </div>

      </div>
    </div>
  </div>

  <!-- ══════════════════════════════════════════════ TAB 4 — PLANTUML ══ -->
  <div class="tab-panel" id="tab-plantuml">
    <div class="diagram-canvas">
      <p style="color:var(--muted);font-family:'JetBrains Mono',monospace;font-size:12px;margin-bottom:16px;">
        Copy this PlantUML source into <a href="https://www.plantuml.com/plantuml" style="color:var(--accent)">plantuml.com</a> or your IDE plugin to render the diagram.
      </p>

      <!-- DIAGRAM 1 -->
      <h3 style="font-size:13px;font-family:'JetBrains Mono',monospace;color:var(--accent);margin-bottom:8px;letter-spacing:1px;">① COMPONENT DIAGRAM</h3>
      <div style="position:relative">
        <button class="copy-btn" onclick="copyCode('code1',this)">COPY</button>
        <div class="plantuml-src" id="code1"><span class="cmt">' MCP Server — Component Diagram</span>
<span class="cmt">' Paste at: https://www.plantuml.com/plantuml/uml/</span>

<span class="kw">@startuml</span> MCP_Component_Diagram
<span class="cmt">' Author: Vaibhav Kashyap | Principal Architect, PeopleStrong</span>
<span class="cmt">' leaveApp + leaveapp-agent MCP Architecture</span>
<span class="kw">!theme</span> blueprint
<span class="kw">skinparam</span> backgroundColor #0a0e1a
<span class="kw">skinparam</span> componentStyle rectangle
<span class="kw">skinparam</span> defaultFontName JetBrains Mono
<span class="kw">skinparam</span> ArrowColor #00d4ff
<span class="kw">skinparam</span> BorderColor #1e2d4a

<span class="kw">package</span> <span class="str">"leaveapp-agent  :8090"</span> #2d1b4e {
  <span class="kw">component</span> [<span class="node">AgentService\nPOST /api/agent/chat</span>]   <span class="kw">as</span> Agent
  <span class="kw">component</span> [<span class="node">OpenAI GPT-4\nChat Completions API</span>]  <span class="kw">as</span> LLM
  <span class="kw">component</span> [<span class="node">REST Tool Adapters\nWebClient → leaveApp</span>]  <span class="kw">as</span> Tools
  <span class="kw">note right of</span> Agent
    Rate limit: 30 req/min/userId
    Stores conversations in agent_db
  <span class="kw">end note</span>
}

<span class="kw">package</span> <span class="str">"leaveApp  :8082  (Spring Boot 2.7.x · Java 17)"</span> #0d2233 {
  <span class="kw">component</span> [<span class="node">ApiKeyFilter</span>]                  <span class="kw">as</span> Filter
  <span class="kw">component</span> [<span class="node">McpController\nPOST /mcp</span>]         <span class="kw">as</span> McpCtrl
  <span class="kw">component</span> [<span class="node">LeaveController\n/api/leaves/**</span>]  <span class="kw">as</span> LeaveCtrl
  <span class="kw">component</span> [<span class="node">McpToolRegistry\n@McpToolDef scan</span>] <span class="kw">as</span> Registry

  <span class="kw">package</span> <span class="str">"Cross-Cutting"</span> #1a2a1a {
    <span class="kw">component</span> [<span class="node">ObservabilityAspect\n(Micrometer)</span>] <span class="kw">as</span> Obs
    <span class="kw">component</span> [<span class="node">Spring Security\n(ApiKeyFilter)</span>]   <span class="kw">as</span> Sec
    <span class="kw">component</span> [<span class="node">Bean Validation\n@Valid on DTOs</span>]    <span class="kw">as</span> Valid
  }

  <span class="kw">package</span> <span class="str">"Domain Layer"</span> #2a2200 {
    <span class="kw">component</span> [<span class="node">LeaveTools\napplyLeave · withdrawLeave\napproveLeave · rejectLeave</span>]   <span class="kw">as</span> LT
    <span class="kw">component</span> [<span class="node">EmployeeTools\nlistEmployees · getBalance\ngetPendingLeaves</span>]          <span class="kw">as</span> ET
    <span class="kw">component</span> [<span class="node">LeaveService\n12 leaves/yr · PENDING→APPROVED\nmanager-only approve</span>]   <span class="kw">as</span> LS
    <span class="kw">component</span> [<span class="node">EmployeeService\nFlyway seed data\nmanager hierarchy</span>]              <span class="kw">as</span> ES
  }
}

<span class="kw">package</span> <span class="str">"Infrastructure (Docker Compose)"</span> #2a0d0d {
  <span class="kw">database</span>  [<span class="node">PostgreSQL\nleaveapp schema\nemployees · leave_requests</span>] <span class="kw">as</span> DB
  <span class="kw">database</span>  [<span class="node">agent_db\nconversations · messages\ntool_invocations</span>]        <span class="kw">as</span> AgentDB
  <span class="kw">component</span> [<span class="node">Prometheus + Grafana</span>]                                      <span class="kw">as</span> Prom
}

<span class="cmt">' ── Agent internal flow ──</span>
Agent <span class="arr">--></span> LLM   : system prompt + tool schemas\n+ conversation history
LLM   <span class="arr">--></span> Agent : tool_calls[] | final answer
Agent <span class="arr">--></span> Tools : invoke REST tool adapter
Tools <span class="arr">--></span> Filter : HTTP POST/GET  X-MCP-API-Key

<span class="cmt">' ── leaveApp internal ──</span>
Filter   <span class="arr">--></span> Sec
Sec      <span class="arr">--></span> McpCtrl   : /mcp  authenticated
Sec      <span class="arr">--></span> LeaveCtrl : /api/leaves  authenticated
McpCtrl  <span class="arr">--></span> Registry  : dispatch(method)
Registry <span class="arr">--></span> Valid
Valid    <span class="arr">--></span> LT
Valid    <span class="arr">--></span> ET
LT  <span class="arr">--></span> LS : apply / approve / reject / withdraw
ET  <span class="arr">--></span> ES : list / balance / pending
LS  <span class="arr">--></span> DB
ES  <span class="arr">--></span> DB

LT  <span class="arr">..</span> Obs : @Around AOP
ET  <span class="arr">..</span> Obs : @Around AOP
Obs <span class="arr">..></span> Prom : mcp.tool.calls / duration

Agent <span class="arr">..></span> AgentDB : persist conversation\n+ tool trace

<span class="kw">@enduml</span></div>
      </div>

      <div style="height:28px"></div>

      <!-- DIAGRAM 2: SEQUENCE -->
      <h3 style="font-size:13px;font-family:'JetBrains Mono',monospace;color:var(--accent);margin-bottom:8px;letter-spacing:1px;">② SEQUENCE DIAGRAM — Full Tool Call Flow</h3>
      <div style="position:relative">
        <button class="copy-btn" onclick="copyCode('code2',this)">COPY</button>
        <div class="plantuml-src" id="code2"><span class="cmt">' MCP Server — Sequence Diagram</span>

<span class="kw">@startuml</span> MCP_Sequence
<span class="cmt">' Author: Vaibhav Kashyap | Principal Architect, PeopleStrong</span>
<span class="kw">!theme</span> blueprint
<span class="kw">skinparam</span> backgroundColor #0a0e1a
<span class="kw">skinparam</span> SequenceArrowThickness 2
<span class="kw">skinparam</span> defaultFontName JetBrains Mono

<span class="kw">actor</span>     <span class="str">"User"</span>                                          <span class="kw">as</span> User
<span class="kw">box</span> <span class="str">"leaveapp-agent  :8090"</span> #2d1b4e
  <span class="kw">participant</span> <span class="str">"AgentService\nPOST /api/agent/chat"</span>       <span class="kw">as</span> AS
  <span class="kw">participant</span> <span class="str">"OpenAI GPT-4\n(tool calling)"</span>             <span class="kw">as</span> LLM
  <span class="kw">participant</span> <span class="str">"REST Tool Adapters\n(WebClient)"</span>           <span class="kw">as</span> TA
  <span class="kw">database</span>    <span class="str">"agent_db"</span>                                  <span class="kw">as</span> ADB
<span class="kw">end box</span>

<span class="kw">box</span> <span class="str">"leaveApp  :8082  (Spring Boot 2.7.x · Java 17)"</span> #0d2233
  <span class="kw">participant</span> <span class="str">"ApiKeyFilter\n+ Spring Security"</span>           <span class="kw">as</span> Sec
  <span class="kw">participant</span> <span class="str">"LeaveController\n/api/leaves/**"</span>           <span class="kw">as</span> LC
  <span class="kw">participant</span> <span class="str">"LeaveService\n(business rules)"</span>            <span class="kw">as</span> LS
  <span class="kw">participant</span> <span class="str">"EmployeeService"</span>                           <span class="kw">as</span> ES
<span class="kw">end box</span>

<span class="kw">database</span>    <span class="str">"PostgreSQL\n(leaveapp schema)"</span>                <span class="kw">as</span> DB

<span class="cmt">' === STARTUP ===</span>
<span class="kw">==</span> Startup: Tool Registration in leaveApp <span class="kw">==</span>
LC <span class="arr">-></span> LC : McpToolRegistry scans @McpToolDef beans\n(LeaveTools, EmployeeTools)
LC <span class="arr">-></span> LC : Generate JSON Schema for each input DTO\n(LeaveApplyInput, EmployeeQueryInput…)

<span class="cmt">' === APPLY LEAVE ===</span>
<span class="kw">==</span> Use Case: "Apply leave for Bob 2026-03-01 to 2026-03-03" <span class="kw">==</span>
User <span class="arr">-></span>  AS  : POST /api/agent/chat\n{userId:"demo-user", message:"Apply leave for Bob…"}
AS   <span class="arr">-></span>  AS  : rate check (30 req/min per userId)
AS   <span class="arr">-></span>  ADB : load conversation history
AS   <span class="arr">-></span>  LLM : chat/completions + tool schemas\n+ history + user message
LLM  <span class="arr">--></span> AS  : tool_calls[{name:findEmployeeByName,\n args:{name:"Bob"}}]
AS   <span class="arr">-></span>  TA  : invoke findEmployeeByName("Bob")
TA   <span class="arr">-></span>  Sec : GET /api/employees  X-MCP-API-Key
Sec  <span class="arr">-></span>  LC
LC   <span class="arr">-></span>  ES  : findByName("Bob")
ES   <span class="arr">-></span>  DB  : SELECT * FROM employees WHERE name ILIKE 'Bob'
DB   <span class="arr">--></span> ES  : [Employee{id:2,name:"Bob",managerId:1}]
ES   <span class="arr">--></span> LC
LC   <span class="arr">--></span> TA  : [{id:2,name:"Bob",managerId:1}]
TA   <span class="arr">--></span> AS  : tool result "1 match — employeeId=2"
AS   <span class="arr">-></span>  LLM : tool_result + continue
LLM  <span class="arr">--></span> AS  : tool_calls[{name:applyLeave,\n args:{actorEmployeeId:2,employeeId:2,\n       startDate:"2026-03-01",endDate:"2026-03-03",\n       comment:"family function"}}]
AS   <span class="arr">-></span>  TA  : invoke applyLeave(...)
TA   <span class="arr">-></span>  Sec : POST /api/leaves/apply
Sec  <span class="arr">-></span>  LC
LC   <span class="arr">-></span>  LS  : apply(actorId=2, empId=2, 2026-03-01..03)
LS   <span class="arr">-></span>  LS  : validate actor==employee (self-apply rule)
LS   <span class="arr">-></span>  LS  : days = 3 · check balance (12 - approved ≥ 3)
LS   <span class="arr">-></span>  DB  : INSERT leave_request STATUS=PENDING
DB   <span class="arr">--></span> LS  : saved {id:5,status:PENDING}
LS   <span class="arr">--></span> LC  : {id:5,status:PENDING,days:3}
LC   <span class="arr">--></span> TA  : 200 OK {id:5,status:PENDING}
TA   <span class="arr">--></span> AS  : tool result "PENDING — leaveId=5"
AS   <span class="arr">-></span>  LLM : tool_result + continue
LLM  <span class="arr">--></span> AS  : finish_reason:stop\n"Leave applied for Bob…"
AS   <span class="arr">-></span>  ADB : persist messages + toolCalls[] + traceId
AS   <span class="arr">--></span> User : {answer:"Leave applied for Bob (2026-03-01 to 2026-03-03).",\n toolCalls:[...], conversationId:"f9c6...", traceId:"4e8d..."}

<span class="kw">@enduml</span></div>
      </div>

      <div style="height:28px"></div>

      <!-- DIAGRAM 3: DEPLOYMENT -->
      <h3 style="font-size:13px;font-family:'JetBrains Mono',monospace;color:var(--accent);margin-bottom:8px;letter-spacing:1px;">③ DEPLOYMENT / C4 CONTEXT DIAGRAM</h3>
      <div style="position:relative">
        <button class="copy-btn" onclick="copyCode('code3',this)">COPY</button>
        <div class="plantuml-src" id="code3"><span class="cmt">' MCP Server — C4 Context Diagram</span>

<span class="kw">@startuml</span> MCP_C4_Context
<span class="cmt">' Author: Vaibhav Kashyap | Principal Architect, PeopleStrong</span>
<span class="kw">!theme</span> blueprint
<span class="kw">skinparam</span> backgroundColor #0a0e1a
<span class="kw">skinparam</span> defaultFontName JetBrains Mono

<span class="kw">!include</span> https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Context.puml

<span class="lbl">LAYOUT_WITH_LEGEND()</span>

<span class="kw">title</span> leaveApp + leaveapp-agent · System Context (Author: Vaibhav Kashyap, PeopleStrong)

<span class="lbl">Person</span>(user, <span class="str">"HR / Employee / Manager"</span>,
  <span class="str">"Sends natural-language leave\nrequests via chat interface"</span>)

<span class="lbl">System_Boundary</span>(agent_sys, <span class="str">"leaveapp-agent  :8090"</span>) {
  <span class="lbl">Container</span>(agent, <span class="str">"AgentService"</span>,
    <span class="str">"Spring Boot · WebFlux"</span>,
    <span class="str">"POST /api/agent/chat\nRate limit: 30 req/min/userId\nMulti-turn conversationId"</span>)
  <span class="lbl">Container</span>(tools, <span class="str">"REST Tool Adapters"</span>,
    <span class="str">"WebClient"</span>,
    <span class="str">"findEmployeeByName · applyLeave\napproveLeave · rejectLeave\nwithdrawLeave · getLeaveBalance"</span>)
  <span class="lbl">ContainerDb</span>(agentdb, <span class="str">"agent_db"</span>,
    <span class="str">"PostgreSQL"</span>,
    <span class="str">"conversations · messages\ntool_invocations · traceId"</span>)
}

<span class="lbl">System_Ext</span>(openai, <span class="str">"OpenAI GPT-4"</span>,
  <span class="str">"Chat Completions API\nwith tool-calling"</span>)

<span class="lbl">System_Boundary</span>(leave_sys, <span class="str">"leaveApp  :8082  (Spring Boot 2.7.x · Java 17)"</span>) {
  <span class="lbl">Container</span>(mcp,  <span class="str">"McpController + Registry"</span>,
    <span class="str">"Spring MVC · JSON-RPC 2.0"</span>,
    <span class="str">"POST /mcp · initialize\ntools/list · tools/call"</span>)
  <span class="lbl">Container</span>(rest, <span class="str">"LeaveController"</span>,
    <span class="str">"Spring MVC · REST"</span>,
    <span class="str">"/api/employees\n/api/leaves/apply|approve|reject\n/api/leaves/balance|pending"</span>)
  <span class="lbl">Container</span>(domain, <span class="str">"LeaveService + EmployeeService"</span>,
    <span class="str">"Java · Spring · JPA"</span>,
    <span class="str">"12 leaves/yr · PENDING→APPROVED\nActor validation · Manager-only approve"</span>)
  <span class="lbl">Container</span>(sec,  <span class="str">"ApiKeyFilter + Observability"</span>,
    <span class="str">"Spring Security · Micrometer"</span>,
    <span class="str">"X-MCP-API-Key auth\nmcp.tool.calls / duration metrics"</span>)
  <span class="lbl">ContainerDb</span>(db, <span class="str">"PostgreSQL (leaveapp schema)"</span>,
    <span class="str">"Flyway migrations"</span>,
    <span class="str">"employees (seed data)\nleave_requests"</span>)
}

<span class="lbl">Rel</span>(user,   agent,  <span class="str">"Natural language chat"</span>, <span class="str">"HTTP POST :8090"</span>)
<span class="lbl">Rel</span>(agent,  openai, <span class="str">"Chat Completions + tool schemas"</span>, <span class="str">"HTTPS"</span>)
<span class="lbl">Rel</span>(agent,  tools,  <span class="str">"Invoke REST tool"</span>)
<span class="lbl">Rel</span>(tools,  rest,   <span class="str">"REST calls"</span>, <span class="str">"HTTP :8082 + X-MCP-API-Key"</span>)
<span class="lbl">Rel</span>(rest,   domain, <span class="str">"Business logic"</span>)
<span class="lbl">Rel</span>(domain, db,     <span class="str">"Read / Write"</span>, <span class="str">"JPA / JDBC"</span>)
<span class="lbl">Rel</span>(agent,  agentdb,<span class="str">"Persist conversation + tool trace"</span>)
<span class="lbl">Rel</span>(sec,    db,     <span class="str">"Flyway migrations on startup"</span>)

<span class="kw">@enduml</span></div>
      </div>

    </div>
  </div>

</div><!-- end wrapper -->

<script>
function switchTab(name) {
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  document.querySelectorAll('.tab-panel').forEach(p => p.classList.remove('active'));
  document.getElementById('tab-' + name).classList.add('active');
  event.target.classList.add('active');
}

function copyCode(id, btn) {
  const text = document.getElementById(id).innerText;
  navigator.clipboard.writeText(text).then(() => {
    btn.textContent = 'COPIED!';
    btn.style.background = 'var(--accent3)';
    btn.style.color = '#fff';
    setTimeout(() => { btn.textContent = 'COPY'; btn.style.background = ''; btn.style.color = ''; }, 2000);
  });
}
</script>
</body>
</html>
