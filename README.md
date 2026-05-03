<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>Beaconchain Dashboard – Full Platform | Validator + Profile + Legal</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(145deg, #0a0c12 0%, #0f1119 100%);
            font-family: 'Inter', system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif;
            color: #eef2ff;
            padding: 2rem 1.5rem;
            line-height: 1.5;
        }

        .container {
            max-width: 1440px;
            margin: 0 auto;
        }

        /* header */
        .app-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1rem;
            margin-bottom: 2.5rem;
            padding-bottom: 1rem;
            border-bottom: 1px solid rgba(255,255,255,0.08);
        }
        .logo h1 {
            font-size: 1.9rem;
            font-weight: 700;
            background: linear-gradient(135deg, #f0f0ff, #a5b4fc);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        .logo p {
            font-size: 0.85rem;
            color: #8b9bff;
        }
        .badge {
            background: rgba(139, 155, 255, 0.15);
            backdrop-filter: blur(4px);
            padding: 0.5rem 1rem;
            border-radius: 60px;
            font-size: 0.85rem;
            border: 1px solid rgba(139, 155, 255, 0.3);
        }

        /* grid layout */
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 1.8rem;
            margin-bottom: 2.5rem;
        }
        .card {
            background: rgba(20, 24, 36, 0.7);
            backdrop-filter: blur(8px);
            border-radius: 32px;
            padding: 1.5rem;
            border: 1px solid rgba(255,255,255,0.05);
            box-shadow: 0 20px 35px -12px rgba(0,0,0,0.4);
            transition: all 0.2s;
        }
        .card:hover {
            border-color: rgba(139, 155, 255, 0.3);
            background: rgba(28, 32, 48, 0.8);
        }
        .card h3 {
            font-size: 1.4rem;
            font-weight: 600;
            margin-bottom: 1.2rem;
            display: flex;
            align-items: center;
            gap: 0.6rem;
            border-left: 3px solid #8b9bff;
            padding-left: 0.75rem;
        }
        .info-row {
            display: flex;
            justify-content: space-between;
            padding: 0.6rem 0;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            flex-wrap: wrap;
            gap: 0.5rem;
        }
        .info-label {
            font-weight: 500;
            color: #a5b4fc;
        }
        .info-value {
            font-family: monospace;
            word-break: break-all;
            text-align: right;
        }
        .endpoint {
            background: #00000030;
            border-radius: 16px;
            padding: 0.8rem;
            margin-top: 0.8rem;
            font-size: 0.8rem;
        }
        .validator-stats {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 0.8rem;
            margin-bottom: 1rem;
            background: rgba(0,0,0,0.3);
            border-radius: 24px;
            padding: 0.8rem;
        }
        .stat {
            text-align: center;
            flex: 1;
        }
        .stat .number {
            font-size: 1.8rem;
            font-weight: 800;
            color: #c084fc;
        }
        .stat .label {
            font-size: 0.7rem;
            color: #9ca3cf;
        }
        .validator-list {
            max-height: 280px;
            overflow-y: auto;
            border-radius: 20px;
            margin-top: 0.8rem;
        }
        .validator-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0.6rem 0.5rem;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            font-size: 0.85rem;
        }
        .validator-index {
            font-weight: 600;
            background: #1e1f2c;
            padding: 0.2rem 0.6rem;
            border-radius: 20px;
        }
        .status-badge {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        .online { color: #4ade80; }
        .offline { color: #f87171; }
        .pending { color: #facc15; }
        button {
            background: #2d2f42;
            border: none;
            color: white;
            padding: 0.5rem 1.2rem;
            border-radius: 40px;
            cursor: pointer;
            font-size: 0.85rem;
            transition: 0.2s;
            margin-top: 0.4rem;
        }
        button:hover {
            background: #4f46e5;
        }
        .tiny-text {
            font-size: 0.7rem;
            color: #8b8daa;
            margin-top: 0.5rem;
        }
        .footer-components {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
            background: rgba(0,0,0,0.25);
            border-radius: 32px;
            padding: 1.8rem;
        }
        .beaconchain-links ul {
            list-style: none;
            margin-top: 0.5rem;
        }
        .beaconchain-links li {
            margin: 0.6rem 0;
        }
        .beaconchain-links a, .developer-info a {
            color: #a5b4fc;
            text-decoration: none;
        }
        .beaconchain-links a:hover, .developer-info a:hover {
            text-decoration: underline;
        }
        .developer-info a {
            color: #f093fb;
        }
        .ownership-note {
            font-size: 0.75rem;
            margin-top: 1rem;
            padding-top: 0.8rem;
            border-top: 1px solid rgba(255,255,255,0.1);
            color: #9ca3af;
        }
        code {
            background: #00000040;
            padding: 0.2rem 0.4rem;
            border-radius: 8px;
            font-size: 0.7rem;
        }
        ::-webkit-scrollbar {
            width: 5px;
        }
        ::-webkit-scrollbar-track {
            background: #1a1c2a;
        }
        ::-webkit-scrollbar-thumb {
            background: #4f46e5;
            border-radius: 10px;
        }
        @media (max-width: 700px) {
            body { padding: 1rem; }
            .card { padding: 1rem; }
        }
        hr {
            border-color: rgba(255,255,255,0.1);
            margin: 0.5rem 0;
        }
    </style>
</head>
<body>
<div class="container">
    <div class="app-header">
        <div class="logo">
            <h1><i class="fas fa-chart-line"></i> Beaconchain Dashboard</h1>
            <p>Ethereum & Gnosis Validator Performance Tracker | 100+ Validators</p>
        </div>
        <div class="badge">
            <i class="fas fa-mobile-alt"></i> v2.0.0 | Full Stack Demo
        </div>
    </div>

    <div class="dashboard-grid">
        <!-- 1) VALIDATOR OVERVIEW CARD -->
        <div class="card">
            <h3><i class="fas fa-users"></i> Validator Fleet</h3>
            <div class="validator-stats" id="statsSummary">
                <div class="stat"><div class="number" id="totalCount">0</div><div class="label">Total Vals</div></div>
                <div class="stat"><div class="number" id="onlineCount">0</div><div class="label">Online</div></div>
                <div class="stat"><div class="number" id="offlineCount">0</div><div class="label">Offline</div></div>
                <div class="stat"><div class="number" id="avgBalance">0</div><div class="label">Avg Balance (ETH)</div></div>
            </div>
            <button id="refreshValidatorsBtn"><i class="fas fa-sync-alt"></i> Refresh mock data</button>
            <div class="validator-list" id="validatorList"></div>
            <div class="tiny-text"><i class="fas fa-chevron-circle-down"></i> Displaying 50 of 100 validators (scroll)</div>
        </div>

        <!-- 2) PROFESSIONAL PROFILE (GitLab/GitHub/ORCID) -->
        <div class="card">
            <h3><i class="fas fa-user-tie"></i> Mahdi Amolimoghaddam</h3>
            <div class="info-row"><span class="info-label">GitLab</span><span class="info-value">gamma.mahdii (ID: 9872165)</span></div>
            <div class="info-row"><span class="info-label">GitHub</span><span class="info-value">Mahdiamoli</span></div>
            <div class="info-row"><span class="info-label">ORCID</span><span class="info-value">0009-0009-7893-9070</span></div>
            <div class="info-row"><span class="info-label">Languages</span><span class="info-value">Farsi (native), English (proficient)</span></div>
            <hr>
            <div class="info-row"><span class="info-label">Founder/Owner</span><span class="info-value">Beaconchain.com (2017–Present)</span></div>
            <div class="info-row"><span class="info-label">President BSC</span><span class="info-value">Binance Smart Chain (2021–Present)</span></div>
            <div class="info-row"><span class="info-label">DPO / Compliance</span><span class="info-value">Euro (2020–Present)</span></div>
            <div class="info-row"><span class="info-label">Web Dev XP</span><span class="info-value">10+ years full‑stack</span></div>
        </div>

        <!-- 3) PREFECT CLOUD + ACCOUNT -->
        <div class="card">
            <h3><i class="fab fa-gitlab"></i> Prefect / GitLab Account</h3>
            <div class="info-row"><span class="info-label">Name</span><span class="info-value">mahdi amolimoghaddam</span></div>
            <div class="info-row"><span class="info-label">Email</span><span class="info-value">gamma.mahdii@gmail.com</span></div>
            <div class="info-row"><span class="info-label">GitLab Handle</span><span class="info-value">@beaconchain-com1</span></div>
            <div class="info-row"><span class="info-label">User ID (Prefect)</span><span class="info-value">42342cea-fdd0-4039-b3b1-17fac8613299</span></div>
            <div class="info-row"><span class="info-label">Work Queue ID</span><span class="info-value">2f3e3d73-6a8c-4ec0-a511-211fad6a3393</span></div>
            <div class="info-row"><span class="info-label">Last active</span><span class="info-value">today at 5:39 AM</span></div>
        </div>

        <!-- 4) API & MONITORING -->
        <div class="card">
            <h3><i class="fas fa-key"></i> API & Monitoring</h3>
            <div class="info-row"><span class="info-label">beaconcha.in API Key</span><span class="info-value">JDJhJDEwJGpvNTVLS1o5</span></div>
            <div class="info-row"><span class="info-label">Machine ID</span><span class="info-value">BSC</span></div>
            <div class="endpoint">
                <div class="info-label"><i class="fas fa-chart-simple"></i> Metrics endpoint</div>
                <code style="word-break:break-all;">https://beaconcha.in/api/v1/client/metrics?apikey=JDJhJDEwJGpvNTVLS1o5&machine=BSC</code>
            </div>
            <div class="endpoint">
                <div class="info-label"><i class="fas fa-cloud-upload-alt"></i> Prefect login key</div>
                <code>pnu_0vUBDWUj3R2aXc46K2jRWoWYJ2BC8d3DBoVh</code>
            </div>
        </div>

        <!-- 5) PREFECT AUTOMATION -->
        <div class="card">
            <h3><i class="fas fa-robot"></i> Prefect Automation</h3>
            <div class="info-row"><span class="info-label">Automation ID</span><span class="info-value">ffb2dcce-aecb-4754-a9c6-896dbf0fa451</span></div>
            <div class="info-row"><span class="info-label">Work Pool ID</span><span class="info-value">1678aad5-ff77-4482-b98e-7c2d137d6bd4</span></div>
            <div class="info-row"><span class="info-label">Workspace</span><span class="info-value">d36df1c1-f0fd-43d3-bd92-2c706c383c56</span></div>
            <div class="info-row"><span class="info-label">Actor</span><span class="info-value">lambda-kelos-field</span></div>
            <details style="margin-top: 12px;">
                <summary style="cursor:pointer; color:#a5b4fc;"><i class="fas fa-code-branch"></i> Payload preview</summary>
                <pre style="background:#0a0c18; padding:0.6rem; border-radius:12px; font-size:0.65rem; overflow-x:auto;">{
  "event": "prefect-cloud.automation.created",
  "payload": { "name": "Beaconchain", "actions": [{"type":"change-flow-run-state"}] }
}</pre>
            </details>
        </div>

        <!-- 6) GDPR AUTHORITIES (National Data Protection) -->
        <div class="card">
            <h3><i class="fas fa-shield-alt"></i> GDPR Authorities</h3>
            <div class="info-row"><span class="info-label">Austria</span><span class="info-value">dsb@dsb.gv.at</span></div>
            <div class="info-row"><span class="info-label">Belgium</span><span class="info-value">commission@privacycommission.be</span></div>
            <div class="info-row"><span class="info-label">Bulgaria</span><span class="info-value">kzld@cpdp.bg</span></div>
            <div class="endpoint">
                <div class="info-label">📜 Official list (EU)</div>
                <span style="font-size:0.7rem;">Full reference available in /docs/gdpr-authorities.md<br>Contact for privacy rights requests.</span>
            </div>
        </div>

        <!-- 7) DOMAIN WHOIS (BEACONCHAIN.US) -->
        <div class="card">
            <h3><i class="fas fa-globe"></i> Domain Ownership</h3>
            <div class="info-row"><span class="info-label">Domain</span><span class="info-value">beaconchain.us</span></div>
            <div class="info-row"><span class="info-label">Registry ID</span><span class="info-value">DD6780204F2B14F38906ACC27BA85BBFD-GDREG</span></div>
            <div class="info-row"><span class="info-label">Creation Date</span><span class="info-value">2025-11-29</span></div>
            <div class="info-row"><span class="info-label">Expiration</span><span class="info-value">2026-11-29</span></div>
            <div class="info-row"><span class="info-label">Registrar</span><span class="info-value">DYNADOT LLC</span></div>
            <div class="info-row"><span class="info-label">Name Servers</span><span class="info-value">ns1.dyna-ns.net / ns2.dyna-ns.net</span></div>
            <div class="tiny-text"><i class="fas fa-lock"></i> WHOIS protected via Super Privacy Service</div>
        </div>

        <!-- 8) OPEN SOURCE CONTRIBUTIONS -->
        <div class="card">
            <h3><i class="fab fa-github"></i> Open Source</h3>
            <div class="info-row"><span class="info-label">Eth2 Beacon Chain Explorer</span><span class="info-value"><a href="https://github.com/Mahdiamoli/eth2-beaconchain-explorer" target="_blank">original/fork</a></span></div>
            <div class="info-row"><span class="info-label">Ethereum.org contribution</span><span class="info-value"><a href="https://github.com/Mahdiamoli/ethereum-org-mahdiamolimoghaddam" target="_blank">PR / edits</a></span></div>
            <div class="info-row"><span class="info-label">Bitcoin Private Key Validator</span><span class="info-value"><a href="https://github.com/Mahdiamoli/bitcoin-private-key-fixer" target="_blank">repo</a></span></div>
            <div class="info-row"><span class="info-label">Solidity compiler contrib</span><span class="info-value">community patches</span></div>
        </div>
    </div>

    <!-- FOOTER with legal + links -->
    <div class="footer-components">
        <div class="beaconchain-links">
            <h3>Beaconchain Dashboard</h3>
            <ul>
                <li><a href="https://beaconchain.us" target="_blank"><i class="fas fa-globe"></i> Official website — beaconchain.us</a></li>
                <li><a href="https://beaconchain.us/dashboard" target="_blank"><i class="fas fa-tachometer-alt"></i> Web app (Dashboard)</a></li>
                <li><a href="https://apps.apple.com/gb/app/beaconchain-dashboard/id1541822121" target="_blank"><i class="fab fa-apple"></i> Download iOS</a></li>
                <li><a href="https://play.google.com/store/apps/details?id=us.beaconchain.beaconchain" target="_blank"><i class="fab fa-android"></i> Download Android</a></li>
            </ul>
            <h4>Contact</h4>
            <p><i class="fas fa-envelope"></i> <a href="mailto:beaconchain@beaconchain.us">beaconchain@beaconchain.us</a> , <a href="mailto:gamma.mahdii@gmail.com">gamma.mahdii@gmail.com</a></p>
            <p><i class="fab fa-godaddy"></i> GoDaddy Expert: <a href="https://experts.godaddy.com/mahdi-amolimoghaddam" target="_blank">mahdi-amolimoghaddam</a></p>
        </div>
        <div class="developer-info">
            <h3>👨‍💻 Mahdi Amolimoghaddam</h3>
            <p>Developer and maintainer of the Beaconchain Dashboard project. Built with love for Ethereum community.</p>
            <p><i class="fab fa-github"></i> GitHub: <a href="https://github.com/beaconchain-com/beaconcha.in" target="_blank">beaconchain-com/beaconcha.in</a> / <a href="https://github.com/Mahdiamoli" target="_blank">Mahdiamoli</a></p>
            <div class="ownership-note">
                <strong><i class="fas fa-copyright"></i> Official Ownership Declaration v2.0.0</strong><br>
                I, <strong>Mahdi Amolimoghaddam</strong>, as sole author and copyright holder, declare complete ownership of the source code, design, and IP of the Beaconchain Dashboard project (v2.0.0+).<br>
                Licensed under <strong>GPL-3.0</strong> with additional terms:<br>
                1️⃣ Attribution – retain this declaration.<br>
                2️⃣ Commercial use prohibited without written consent: <a href="mailto:beaconchain@beaconchain.us">beaconchain@beaconchain.us</a><br>
                3️⃣ Share-Alike – modifications under same GPL-3.0.<br>
                © 2025–2026 Mahdi Amolimoghaddam. All rights reserved.
                <br><br>
                <i class="fas fa-database"></i> GDPR compliance: National Data Protection Authorities listed above. For privacy requests contact DPO.
            </div>
        </div>
    </div>
</div>

<script>
    (function() {
        const TOTAL_VALIDATORS = 100;
        let validators = [];

        function generateMockValidators() {
            const list = [];
            for (let i = 1; i <= TOTAL_VALIDATORS; i++) {
                const rand = Math.random();
                let status = 'online';
                if (rand < 0.18) status = 'offline';
                else if (rand < 0.24) status = 'pending';
                const balance = (32 + Math.random() * 5).toFixed(2);
                list.push({
                    index: i,
                    status: status,
                    balance: parseFloat(balance),
                    rewards: (Math.random() * 0.85).toFixed(4)
                });
            }
            return list;
        }

        function updateUI() {
            validators = generateMockValidators();
            const total = validators.length;
            const online = validators.filter(v => v.status === 'online').length;
            const offline = validators.filter(v => v.status === 'offline').length;
            const avgBalance = (validators.reduce((s, v) => s + v.balance, 0) / total).toFixed(2);

            document.getElementById('totalCount').innerText = total;
            document.getElementById('onlineCount').innerText = online;
            document.getElementById('offlineCount').innerText = offline;
            document.getElementById('avgBalance').innerText = avgBalance;

            const container = document.getElementById('validatorList');
            container.innerHTML = '';
            const displayList = validators.slice(0, 50);
            displayList.forEach(v => {
                const statusIcon = v.status === 'online' ? '🟢' : (v.status === 'offline' ? '🔴' : '🟡');
                const statusClass = v.status === 'online' ? 'online' : (v.status === 'offline' ? 'offline' : 'pending');
                const div = document.createElement('div');
                div.className = 'validator-item';
                div.innerHTML = `
                    <div><span class="validator-index">#${v.index}</span></div>
                    <div class="status-badge">
                        <span class="${statusClass}">${statusIcon} ${v.status === 'online' ? 'Active' : (v.status === 'offline' ? 'Offline' : 'Pending')}</span>
                        <span style="background:#2a2d3e; padding:2px 8px; border-radius:20px;">${v.balance} ETH</span>
                    </div>
                `;
                container.appendChild(div);
            });
            if (TOTAL_VALIDATORS > 50) {
                const note = document.createElement('div');
                note.style.padding = '0.6rem';
                note.style.textAlign = 'center';
                note.style.fontSize = '0.7rem';
                note.style.color = '#9ca3af';
                note.innerText = `+ ${TOTAL_VALIDATORS - 50} more validators (full support up to 100+ validators)`;
                container.appendChild(note);
            }
        }

        document.getElementById('refreshValidatorsBtn')?.addEventListener('click', () => updateUI());
        updateUI();
    })();
</script>
</body>
</html>