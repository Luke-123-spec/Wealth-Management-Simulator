<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Portfolio Manager Challenge</title>
    <style>
      :root {
        color-scheme: dark;
        --bg: #0f1418;
        --bg-2: #1a2329;
        --panel: #161d22;
        --panel-2: #202a31;
        --text: #eef2f4;
        --muted: #9aa3ab;
        --accent: #3b6ea6;
        --accent-2: #5d8fc8;
        --accent-3: #8fb7e4;
        --burgundy: #7a3d4a;
        --burgundy-2: #9c5563;
        --danger: #9b4d4d;
        --border: rgba(255, 255, 255, 0.12);
        --shadow: rgba(0, 0, 0, 0.3);
      }

      * {
        box-sizing: border-box;
      }

      body {
        margin: 0;
        font-family: "Inter", "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
        background: linear-gradient(135deg, var(--bg) 0%, var(--bg-2) 100%);
        color: var(--text);
        min-height: 100vh;
        line-height: 1.6;
      }

      .app-shell {
        max-width: 1180px;
        margin: 0 auto;
        padding: 28px 24px 40px;
      }

      .hero {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 24px;
        margin-bottom: 20px;
        padding-bottom: 18px;
        border-bottom: 1px solid var(--border);
      }

      .eyebrow {
        text-transform: uppercase;
        letter-spacing: 0.24em;
        color: var(--accent-3);
        font-size: 0.74rem;
        font-weight: 700;
        margin: 0 0 8px;
      }

      h1,
      h2,
      h3,
      p {
        margin-top: 0;
      }

      h1, h2, h3 {
        font-family: "Georgia", "Times New Roman", serif;
        letter-spacing: 0.01em;
        color: var(--text);
      }

      .hero-copy {
        color: var(--muted);
        max-width: 720px;
        line-height: 1.7;
        font-size: 1rem;
      }

      .card {
        background: linear-gradient(135deg, var(--panel) 0%, var(--panel-2) 100%);
        border: 1px solid var(--border);
        border-radius: 18px;
        padding: 24px;
        box-shadow: 0 18px 42px var(--shadow);
      }

      .setup-card {
        max-width: 900px;
      }

      .setup-grid {
        display: grid;
        grid-template-columns: 1.2fr 0.8fr;
        gap: 24px;
        align-items: start;
      }

      .history-panel {
        background: linear-gradient(135deg, rgba(122, 61, 74, 0.16), rgba(47, 79, 127, 0.08));
        border: 1px solid var(--border);
        border-radius: 16px;
        padding: 16px;
      }

      .history-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 10px;
      }

      .history-list {
        list-style: none;
        padding: 0;
        margin: 0;
        display: grid;
        gap: 8px;
      }

      .history-entry {
        background: rgba(255, 255, 255, 0.04);
        border: 1px solid var(--border);
        border-radius: 10px;
        padding: 10px;
        font-size: 0.95rem;
      }

      .small-btn {
        padding: 8px 12px;
        font-size: 0.85rem;
      }

      label {
        display: block;
        font-weight: 600;
        margin: 12px 0 6px;
      }

      input[type="text"],
      input[type="number"] {
        width: 100%;
        background: var(--panel-2);
        color: var(--text);
        border: 1px solid var(--border);
        border-radius: 12px;
        padding: 12px 14px;
        font-size: 1rem;
      }

      input[type="number"] {
        margin-top: 10px;
      }

      .primary-btn,
      .secondary-btn {
        border: none;
        border-radius: 999px;
        padding: 12px 18px;
        cursor: pointer;
        font-weight: 700;
        transition: transform 0.2s ease, background 0.2s ease;
      }

      .primary-btn:hover,
      .secondary-btn:hover {
        transform: translateY(-1px);
      }

      .primary-btn {
        background: linear-gradient(135deg, var(--burgundy), var(--accent));
        color: white;
        margin-top: 18px;
        box-shadow: 0 10px 24px rgba(122, 61, 74, 0.24);
      }

      .secondary-btn {
        background: rgba(255, 255, 255, 0.04);
        color: var(--text);
        border: 1px solid rgba(219, 207, 179, 0.16);
      }

      .full-width {
        width: 100%;
      }

      .hidden {
        display: none !important;
      }

      .round-banner {
        background: linear-gradient(135deg, rgba(122, 61, 74, 0.18), rgba(47, 79, 127, 0.14));
        border: 1px solid var(--border);
        border-radius: 14px;
        padding: 14px 18px;
        margin-bottom: 16px;
        font-weight: 700;
      }

      .country-card {
        margin-bottom: 20px;
      }

      .company-grid {
        display: grid;
        grid-template-columns: repeat(2, minmax(0, 1fr));
        gap: 16px;
        margin-bottom: 20px;
      }

      .company-card {
        background: rgba(255, 255, 255, 0.03);
        border: 1px solid var(--border);
        border-radius: 16px;
        padding: 18px;
      }

      .company-card h3 {
        font-size: 1.05rem;
        margin-bottom: 8px;
      }

      .company-card p {
        color: var(--muted);
        line-height: 1.5;
        margin-bottom: 10px;
      }

      .allocation-controls {
        display: flex;
        align-items: center;
        margin-top: 10px;
      }

      .allocation-input {
        flex: 1;
        text-align: center;
        font-weight: 700;
      }

      .clear-btn {
        border: 1px solid var(--border);
        border-radius: 999px;
        background: rgba(255, 255, 255, 0.06);
        color: var(--text);
        width: 36px;
        height: 36px;
        cursor: pointer;
        margin-left: 6px;
      }

      .clear-btn:hover {
        background: rgba(255, 104, 104, 0.16);
      }

      .share-hint {
        margin-top: 8px;
        color: #dcecff;
        font-size: 0.9rem;
        font-weight: 700;
        letter-spacing: 0.01em;
        text-shadow: 0 0 10px rgba(93, 143, 200, 0.16);
      }

      .adjust-row {
        display: flex;
        align-items: center;
        gap: 8px;
        margin-top: 10px;
        flex-wrap: wrap;
      }

      .adjust-btn {
        border: 1px solid var(--border);
        border-radius: 999px;
        background: rgba(255, 255, 255, 0.06);
        color: var(--text);
        padding: 8px 12px;
        cursor: pointer;
        font-size: 0.88rem;
      }

      .adjust-btn:hover {
        background: rgba(70, 184, 255, 0.16);
      }

      .adjust-value {
        width: 90px;
        text-align: center;
        padding: 8px 10px;
        border-radius: 999px;
        border: 1px solid var(--border);
        background: var(--panel-2);
        color: var(--text);
      }

      .price-pill {
        display: inline-block;
        padding: 7px 10px;
        border-radius: 999px;
        background: rgba(93, 143, 200, 0.22);
        border: 1px solid rgba(143, 183, 228, 0.35);
        color: #dcecff;
        font-weight: 700;
        margin-bottom: 8px;
      }

      .allocation-toolbar {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 12px;
        margin-bottom: 16px;
        flex-wrap: wrap;
      }

      .review-toolbar {
        margin-bottom: 12px;
      }

      .review-panel {
        margin-bottom: 16px;
        border: 1px solid rgba(122, 61, 74, 0.24);
        background: rgba(47, 79, 127, 0.1);
      }

      .toolbar-note {
        color: var(--muted);
        margin: 0;
      }

      .summary-card {
        display: flex;
        flex-direction: column;
        gap: 10px;
      }

      .summary-row {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding-bottom: 8px;
        border-bottom: 1px solid rgba(255, 255, 255, 0.08);
      }

      .summary-row:last-child {
        border-bottom: none;
      }

      .result-grid {
        display: grid;
        gap: 12px;
        margin-top: 16px;
      }

      .result-item {
        background: rgba(255, 255, 255, 0.03);
        border: 1px solid var(--border);
        border-radius: 14px;
        padding: 14px;
      }

      .result-item .good {
        color: var(--accent-2);
      }

      .result-item .bad {
        color: var(--danger);
      }

      .summary-hero {
        margin-bottom: 16px;
      }

      .summary-sentence {
        color: var(--accent-2);
        font-size: 1.05rem;
        line-height: 1.7;
        margin-bottom: 0;
      }

      .summary-highlight {
        border-color: rgba(122, 61, 74, 0.35);
        background: rgba(47, 79, 127, 0.12);
      }

      @media (max-width: 840px) {
        .hero {
          flex-direction: column;
          align-items: flex-start;
        }

        .company-grid {
          grid-template-columns: 1fr;
        }
      }
    </style>
  </head>
  <body>
    <div class="app-shell">
      <header class="hero">
        <div>
          <p class="eyebrow">Wealth Management Simulation</p>
          <h1>Portfolio Manager Challenge</h1>
          <p class="hero-copy">
            This local simulation recreates a fast-paced portfolio challenge built around country context, company fundamentals and market shocks.
          </p>
        </div>
        <button id="resetBtn" class="secondary-btn">Reset Game</button>
      </header>

      <section id="setupSection" class="card setup-card">
        <div class="setup-grid">
          <div>
            <h2>Start your portfolio</h2>
            <label for="playerName">Your name</label>
            <input id="playerName" type="text" maxlength="40" placeholder="Enter your name" />
            <button id="startBtn" class="primary-btn">Begin the challenge</button>
          </div>
          <div class="history-panel">
            <div class="history-header">
              <h3>Previous attempts</h3>
              <button type="button" id="clearHistoryBtn" class="secondary-btn small-btn">Clear</button>
            </div>
            <ul id="historyList" class="history-list"></ul>
          </div>
        </div>
      </section>

      <section id="gameSection" class="hidden">
        <div id="roundBanner" class="round-banner"></div>
        <div id="countryCard" class="card country-card"></div>
        <div class="review-toolbar">
          <button type="button" id="reviewToggleBtn" class="secondary-btn hidden">Review previous round</button>
        </div>
        <div id="reviewPanel" class="review-panel card hidden"></div>
        <form id="allocationForm" class="allocation-form">
          <div class="allocation-toolbar">
            <button type="button" id="equalSplitBtn" class="secondary-btn">Split evenly</button>
            <p class="toolbar-note">Enter a pound value for each company and see the implied share count instantly.</p>
          </div>
          <div id="companyGrid" class="company-grid"></div>
          <div class="summary-card card">
            <div class="summary-row">
              <span>Portfolio value</span>
              <strong id="wealthDisplay">£1,000,000</strong>
            </div>
            <div class="summary-row">
              <span>Allocated</span>
              <strong id="allocationDisplay">£0</strong>
            </div>
            <div class="summary-row">
              <span>Remaining</span>
              <strong id="remainingDisplay">£1,000,000</strong>
            </div>
            <button type="submit" class="primary-btn full-width">Lock in your allocation</button>
          </div>
        </form>
      </section>

      <section id="resultsSection" class="card hidden"></section>
    </div>

    <script>
      const ROUND_COUNT = 3;
      const STARTING_WEALTH = 1000000;
      const state = {
        playerName: "",
        round: 1,
        wealth: STARTING_WEALTH,
        results: [],
        roundData: null,
        lastRoundReview: null,
        challengeSetup: null,
      };

      const countryPool = [
        { name: "Anthropica", description: "A capitalist island nation off the coast of China. Political tensions have been rising and public unrest is becoming more visible.", economy: "The economy is still performing relatively well, but growth is slowing as industry moves out and domestic small businesses struggle." },
        { name: "Veloria", description: "A fast-growing republic with close links to the EU, though there is concern over an increasingly divided parliament.", economy: "Growth remains strong, driven by technology and services, but inflation and housing costs are beginning to bite." },
        { name: "Kaldor", description: "A resource-rich state with a recent shift toward infrastructure investment and energy exports.", economy: "Commodity prices have boosted government revenues, but the broader economy remains vulnerable to global demand swings." },
        { name: "Novastra", description: "A newly industrialised country with a strong export base and a young, urbanising population.", economy: "The economy is expanding quickly, though political reforms and labour shortages are creating uncertainty." },
        { name: "Aurelia", description: "A wealthy constitutional monarchy with a strong services sector and a growing focus on green industrial policy.", economy: "The country has strong public finances, but housing shortages and ageing demographics are weighing on medium-term productivity." },
        { name: "Brindor", description: "A heavily industrialised federation facing pressure from regional inequality and growing trade protectionism.", economy: "Manufacturing remains important, although weak export demand and supply chain bottlenecks have reduced momentum." },
        { name: "Meridia", description: "A democratic market economy known for digital infrastructure and strong pharmaceutical research capabilities.", economy: "Growth is resilient, but an expensive labour market and higher financing costs are squeezing smaller firms." },
        { name: "Solvane", description: "A high-income republic with deep ties to global capital markets and a strong emphasis on financial regulation.", economy: "The outlook is stable, though the country faces slower expansion as consumer demand cools and borrowing costs remain elevated." },
        { name: "Eryndor", description: "A frontier market with a young population and an ambitious government-led infrastructure programme.", economy: "Public investment is supporting growth, but weak institutions and currency volatility remain significant risks." },
        { name: "Talania", description: "A diverse republic with strong agricultural exports and a fast-growing middle class.", economy: "The economy is expanding, although seasonal shocks and political disputes over subsidies are creating volatility." },
        { name: "Cestria", description: "A highly urbanised state with advanced logistics networks and significant exposure to global trade routes.", economy: "The economy is competitive and efficient, but dependence on imported energy is making it vulnerable to price swings." },
        { name: "Orivon", description: "A resource-rich but politically fragile state that is trying to attract foreign investment while managing internal divisions.", economy: "Commodity revenues are supporting growth, but governance concerns and uneven infrastructure are limiting long-term confidence." },
        { name: "Lysara", description: "A small open economy heavily dependent on tourism and foreign investment, with a recent rise in anti-immigration sentiment.", economy: "Growth is uneven, and the country is vulnerable to sudden shifts in visitor demand and external financing conditions." },
        { name: "Dovan", description: "A post-industrial republic with a strong engineering base and a history of political volatility.", economy: "The economy is recovering, though labour shortages and regional inequality are holding back investment momentum." },
        { name: "Rashel", description: "A central European state with strong export manufacturing and an increasingly assertive national policy agenda.", economy: "The economy has solid fundamentals, but higher energy prices and policy uncertainty are driving concerns about inflation." },
        { name: "Ilyra", description: "A low-tax republic known for financial services and shipping, with a growing debate over regulatory oversight.", economy: "The economy is dynamic, though exposure to global capital flows means it can swing quickly when sentiment turns." },
        { name: "Parthos", description: "A large federation with strong agricultural output but severe regional divisions over political reform.", economy: "The economy is mixed, with strong rural production offset by weak industry and public spending constraints." },
        { name: "Nivara", description: "A developing market with major urban growth and ambitious digital transformation plans.", economy: "Growth is rapid, but infrastructure bottlenecks and subsidy reforms are creating uneven outcomes across sectors." },
        { name: "Sorell", description: "A mountainous state with a strong export base in precision manufacturing and premium food products.", economy: "The country is stable, but it is exposed to climate risk and labour shortages in key export industries." },
        { name: "Marek", description: "A major oil and gas producer with significant state influence over strategic sectors.", economy: "Energy income supports the economy, although diversification remains limited and the outlook is sensitive to commodity cycles." },
        { name: "Caldria", description: "A highly diversified democracy with strong education and research capabilities, but growing social tensions.", economy: "The economy is sophisticated and resilient, although high living costs are reducing consumer confidence." },
        { name: "Vantor", description: "A frontier economy with ambitious infrastructure investment and a heavy reliance on external debt.", economy: "Growth is promising, but currency weakness and sovereign borrowing concerns remain significant constraints." },
        { name: "Terenia", description: "A coastal republic with deep defence and aerospace links and an increasingly strategic geopolitical role.", economy: "The economy is supported by government contracts, but it remains highly sensitive to global defence spending cycles." },
        { name: "Fjordis", description: "A small northern state with strong renewable energy capacity and a highly skilled workforce.", economy: "The economy is stable and innovative, though labour scarcity and weather-related disruption can still affect output." },
        { name: "Qadara", description: "A large emerging market with strong demographics and widening investment in urban logistics.", economy: "The country is growing quickly, although policy unpredictability and inflation are making investors cautious." },
      ];

      const companyPool = [
        { id: "jcdorgan", name: "JCDorgan", sector: "Financials", description: "A domestic finance juggernaut with a strong retail banking franchise and a growing wealth management arm.", context: "Its earnings are tied closely to domestic lending, consumer confidence and interest-rate expectations. It usually performs well when credit conditions stay stable, but it can be vulnerable when funding costs rise.", watchlist: "Watch mortgage demand, fee income and any sign that margin pressure is building.", basePrice: 2.4, sensitivity: 1.0 },
        { id: "halcyon", name: "Halcyon Energy", sector: "Energy", description: "A large-scale power producer focused on renewables and grid infrastructure with strong long-term contracts.", context: "The company benefits from policy support for clean energy, but its valuation can swing sharply on commodity prices, policy changes and interest-rate expectations.", watchlist: "Watch power prices, capex guidance and any indication that regulation is tightening.", basePrice: 3.15, sensitivity: 1.05 },
        { id: "sorrel", name: "Sorrel Apparel", sector: "Consumer", description: "A fashion retailer with manufacturing hubs in Vietnam and a strong online sales channel.", context: "Its margins are highly exposed to shipping costs, labour conditions and consumer spending. Overseas production makes it more vulnerable to supply chain shocks and currency moves.", watchlist: "Watch freight costs, inventory levels and any disruption to its Asian production base.", basePrice: 1.75, sensitivity: 1.2 },
        { id: "maris", name: "Maris Biotech", sector: "Healthcare", description: "A biotech company developing advanced diagnostics and specialist medical devices with a promising pipeline.", context: "The business carries a high-growth profile, but its value depends heavily on clinical milestones, regulatory approvals and investor sentiment around innovation risk.", watchlist: "Watch trial results, FDA or equivalent approvals and any change in risk appetite.", basePrice: 4.6, sensitivity: 1.15 },
        { id: "avent", name: "Avent Logistics", sector: "Industrials", description: "A logistics operator serving ports, freight corridors and high-growth Asian trade routes.", context: "The firm tends to benefit from expanding global trade, but it is also exposed to fuel costs, geopolitical tensions and sudden changes in traffic volumes.", watchlist: "Watch shipping demand, costs per shipment and any sign that trade routes are weakening.", basePrice: 2.95, sensitivity: 1.08 },
        { id: "lumen", name: "Lumen Digital", sector: "Technology", description: "A software group specialising in AI productivity tools for enterprise clients.", context: "The company sits at the centre of a fast-moving technology theme, but valuations can change quickly when investors rotate away from high-growth names.", watchlist: "Watch customer wins, sales growth and the broader mood around technology valuations.", basePrice: 5.2, sensitivity: 1.12 },
        { id: "northstar", name: "Northstar Metals", sector: "Materials", description: "A mining group focused on copper, nickel and battery metals with operations across several emerging markets.", context: "The company benefits from electrification demand, but its valuation is highly exposed to commodity prices and geopolitical disruptions.", watchlist: "Watch ore prices, operating costs and any change in government permitting rules.", basePrice: 3.45, sensitivity: 1.18 },
        { id: "cinder", name: "Cinder Foods", sector: "Consumer Staples", description: "A food producer with strong branded household products and a broad distribution network in Europe and Asia.", context: "The business tends to be defensive, but margin pressure from input costs and consumer substitution can still move the stock materially.", watchlist: "Watch commodity inflation, volume growth and retailer inventory levels.", basePrice: 2.1, sensitivity: 0.92 },
        { id: "meridian", name: "Meridian Utilities", sector: "Utilities", description: "A regulated utility operator with a growing renewable generation portfolio and a strong balance sheet.", context: "The company is often favoured during risk-off periods, though regulatory changes and long-duration capital projects can still affect sentiment.", watchlist: "Watch rate reset decisions, maintenance spend and policy updates around network investment.", basePrice: 2.85, sensitivity: 0.9 },
        { id: "quell", name: "Quell Telecom", sector: "Telecommunications", description: "A wireless network provider with expanding broadband and enterprise connectivity services.", context: "The firm benefits from recurring revenue, but competition, spectrum costs and capital intensity can weigh on valuation multiples.", watchlist: "Watch subscriber growth, average revenue per user and network upgrade costs.", basePrice: 4.1, sensitivity: 1.01 },
        { id: "atlas", name: "Atlas Build", sector: "Real Estate", description: "A property developer and construction group with exposure to urban housing and infrastructure projects.", context: "The company can be sensitive to interest rates, planning delays and government spending cycles.", watchlist: "Watch mortgage rates, project pipeline updates and land acquisition costs.", basePrice: 2.7, sensitivity: 1.14 },
        { id: "nova", name: "Nova Retail", sector: "Consumer Discretionary", description: "A regional retail chain combining online commerce with physical stores and strong loyalty programmes.", context: "The business is tied to disposable incomes and consumer sentiment, making it vulnerable when spending slows.", watchlist: "Watch footfall, same-store sales and promotional intensity.", basePrice: 1.95, sensitivity: 1.16 },
        { id: "solace", name: "Solace Pharma", sector: "Healthcare", description: "A specialist pharmaceutical group focused on oncology and rare diseases with a strong late-stage pipeline.", context: "The company can be highly sensitive to clinical trial outcomes, pricing regulation and patent litigation.", watchlist: "Watch trial readouts, FDA rulings and reimbursement policy changes.", basePrice: 4.25, sensitivity: 1.17 },
        { id: "vesta", name: "Vesta Insurance", sector: "Financials", description: "A regional insurer with strong underwriting discipline and growing digital distribution channels.", context: "The business can benefit from higher premiums, but it remains exposed to catastrophe losses and claims inflation.", watchlist: "Watch claims ratios, reserve strength and catastrophe exposure.", basePrice: 3.2, sensitivity: 0.95 },
        { id: "riverstone", name: "Riverstone Water", sector: "Utilities", description: "A water infrastructure business providing treatment, distribution and recycling services to major urban areas.", context: "The company often has defensive revenues, though regulatory capital spending cycles and environmental compliance costs can affect returns.", watchlist: "Watch water scarcity, regulatory fines and capex guidance.", basePrice: 2.55, sensitivity: 0.88 },
        { id: "brightloop", name: "Brightloop AI", sector: "Technology", description: "A software firm building automation platforms for large manufacturers and enterprise service providers.", context: "The company has significant growth potential, but valuations can change quickly as market sentiment shifts around AI spending.", watchlist: "Watch enterprise contract wins, margin trends and software spending cycles.", basePrice: 5.8, sensitivity: 1.22 },
        { id: "harborline", name: "Harborline Shipping", sector: "Industrials", description: "A container shipping specialist with routes spanning the Atlantic and Pacific.", context: "The company is exposed to freight demand, fuel prices and international trade policy changes.", watchlist: "Watch charter rates, bunker costs and route disruption reports.", basePrice: 2.8, sensitivity: 1.11 },
        { id: "basilisk", name: "Basilisk Aerospace", sector: "Industrials", description: "A manufacturer of aircraft components and defence systems for civil and government customers.", context: "The company benefits from long-term contracts, but it is sensitive to order timing and changes in defence budgets.", watchlist: "Watch order intake, production delays and government procurement cycles.", basePrice: 3.9, sensitivity: 1.04 },
        { id: "crownvale", name: "Crownvale Foods", sector: "Consumer Staples", description: "A branded food manufacturer with strong exposure to grocery and convenience retail channels.", context: "The company can defend well during downturns, though commodity prices and packaging costs continue to matter.", watchlist: "Watch input costs, retailer promotions and shelf-space wins.", basePrice: 2.15, sensitivity: 0.96 },
        { id: "trident", name: "Trident Mining", sector: "Materials", description: "A diversified mining company with exposure to iron ore, lithium and gold.", context: "The company is highly sensitive to cyclical commodity prices and geopolitical shocks around major mining jurisdictions.", watchlist: "Watch ore prices, mine output and permitting issues.", basePrice: 3.65, sensitivity: 1.19 },
        { id: "evergreen", name: "Evergreen Homes", sector: "Real Estate", description: "A residential property company building mixed-income developments in fast-growing urban centres.", context: "The business is exposed to mortgage rates, construction costs and planning approvals.", watchlist: "Watch home sales, build cost inflation and interest-rate expectations.", basePrice: 2.35, sensitivity: 1.13 },
        { id: "midnight", name: "Midnight Retail", sector: "Consumer Discretionary", description: "A fashion and lifestyle retailer with both online and high-street stores.", context: "The company is influenced by consumer confidence, competition and fashion trend cycles.", watchlist: "Watch footfall, inventory turns and promotional discounting.", basePrice: 1.8, sensitivity: 1.18 },
        { id: "frostline", name: "Frostline Logistics", sector: "Industrials", description: "A cold-chain logistics provider serving food, pharmaceutical and e-commerce customers.", context: "The company benefits from expanding logistics complexity, but it is exposed to fuel prices and temperature-control disruption.", watchlist: "Watch refrigerated capacity, fuel costs and route reliability.", basePrice: 2.9, sensitivity: 1.06 },
        { id: "oracle", name: "Oracle Grid", sector: "Utilities", description: "An electricity network operator with significant exposure to grid-modernisation projects.", context: "The company benefits from long-term demand for energy infrastructure, but capital expenditure and regulation remain central.", watchlist: "Watch network outages, rate reviews and maintenance spend.", basePrice: 3.05, sensitivity: 0.93 },
        { id: "neo", name: "Neo Health", sector: "Healthcare", description: "A health-tech company selling digital diagnostics and remote monitoring services to hospitals and insurers.", context: "The business can be driven by adoption rates, reimbursement policy and data-security concerns.", watchlist: "Watch contracted wins, regulatory pressure and margin growth.", basePrice: 4.7, sensitivity: 1.09 },
        { id: "silverpeak", name: "Silverpeak Bank", sector: "Financials", description: "A digital bank with strong consumer lending, card services and a growing SME franchise.", context: "The company is exposed to credit quality, funding costs and digital competition.", watchlist: "Watch bad debt trends, deposit pricing and fintech disruption.", basePrice: 3.45, sensitivity: 1.02 },
        { id: "signal", name: "Signal Media", sector: "Communication Services", description: "A media group with a large advertising platform and growing subscription content services.", context: "The company benefits from digital ad spending, but it is vulnerable to changes in consumer attention and platform competition.", watchlist: "Watch advertiser budgets, engagement trends and content licensing.", basePrice: 2.6, sensitivity: 1.08 },
        { id: "terra", name: "Terra Renewables", sector: "Energy", description: "A developer of solar, storage and wind assets with exposure to utility-scale infrastructure projects.", context: "The business benefits from decarbonisation trends, but it remains sensitive to subsidy changes and project delays.", watchlist: "Watch project approvals, power pricing and policy support.", basePrice: 3.3, sensitivity: 1.1 },
        { id: "pioneer", name: "Pioneer Chemicals", sector: "Materials", description: "A specialty chemicals producer supplying industrial and consumer manufacturing sectors.", context: "The company is influenced by raw material costs, environmental regulation and industrial demand.", watchlist: "Watch feedstock prices, plant utilisation and regulatory compliance.", basePrice: 2.95, sensitivity: 1.07 },
        { id: "diamond", name: "Diamond Retail", sector: "Consumer Discretionary", description: "A premium retailer operating luxury and lifestyle brands across multiple geographies.", context: "The company is sensitive to consumer spending, fashion cycles and currency swings.", watchlist: "Watch same-store sales, margins and luxury demand trends.", basePrice: 4.0, sensitivity: 1.2 },
        { id: "sunline", name: "Sunline Telecom", sector: "Telecommunications", description: "A broadband and mobile operator expanding into enterprise digital services.", context: "The firm benefits from rising data usage, but competition and network investment can pressure returns.", watchlist: "Watch churn, spectrum costs and service rollouts.", basePrice: 3.75, sensitivity: 1.0 },
        { id: "verdant", name: "Verdant Foods", sector: "Consumer Staples", description: "A premium food and beverage business with strong international distribution and rising brand value.", context: "The company can be supported by resilient consumer demand, but supply shocks and inflation remain important risks.", watchlist: "Watch input costs, distribution strength and consumer price elasticity.", basePrice: 2.45, sensitivity: 0.98 },
        { id: "arcstone", name: "Arcstone Capital", sector: "Financials", description: "A private markets investor with holdings in infrastructure, healthcare and technology.", context: "The company often benefits from strong capital markets, but valuations can be volatile when liquidity tightens.", watchlist: "Watch fundraising momentum, asset valuations and exit activity.", basePrice: 3.6, sensitivity: 1.14 },
        { id: "cobalt", name: "Cobalt Auto", sector: "Consumer Discretionary", description: "A vehicle manufacturer with strong electric vehicle exposure and an expanding software platform.", context: "The firm is exposed to demand cycles, battery costs and regulatory incentives around electrification.", watchlist: "Watch EV demand, production ramp-up and battery input costs.", basePrice: 4.4, sensitivity: 1.21 },
        { id: "aurex", name: "Aurex Biotech", sector: "Healthcare", description: "A biotechnology business focusing on gene-editing and personalised medicine platforms.", context: "The company can move sharply on clinical milestones, regulatory decisions and investor risk appetite.", watchlist: "Watch trial data, patent disputes and funding environment.", basePrice: 5.1, sensitivity: 1.24 },
        { id: "greenport", name: "Greenport Energy", sector: "Energy", description: "A renewable energy developer focused on solar, wind and storage projects in multiple markets.", context: "The company benefits from decarbonisation trends, but policy changes and grid connection delays can hurt execution.", watchlist: "Watch project timing, subsidy policy and battery storage economics.", basePrice: 3.2, sensitivity: 1.09 },
        { id: "horizon", name: "Horizon Software", sector: "Technology", description: "A business software provider serving logistics, retail and financial services clients.", context: "The company can benefit from digital transformation budgets, but competitive pressure can compress margins.", watchlist: "Watch customer retention, product innovation and cloud cost growth.", basePrice: 4.8, sensitivity: 1.06 },
        { id: "noble", name: "Noble Property", sector: "Real Estate", description: "A commercial real estate group investing in logistics parks, offices and industrial sites.", context: "The company is highly sensitive to occupancy, interest rates and demand for flexible workspace.", watchlist: "Watch leasing volumes, valuations and refinancing conditions.", basePrice: 2.75, sensitivity: 1.15 },
        { id: "peak", name: "Peak Insurance", sector: "Financials", description: "A specialist insurer focused on catastrophe and climate risk underwriting.", context: "The company can be volatile around natural disaster losses and reinsurance pricing.", watchlist: "Watch catastrophe frequency, premium growth and claims reserves.", basePrice: 3.1, sensitivity: 1.16 },
      ];

      const eventTemplates = [
        { label: "Supply chain disruption", description: "A major weather event, shipping bottleneck or input shortage disrupts operations and forces a sharp reassessment of near-term cash flows.", move: -0.45 },
        { label: "Positive earnings surprise", description: "Strong demand, better margins and an upbeat outlook lift the market’s view of the company materially.", move: 0.55 },
        { label: "Regulatory pressure", description: "New rules or tax changes hit pricing power and weaken sentiment around future earnings.", move: -0.3 },
        { label: "Consumer confidence improves", description: "A strong spending backdrop and rising confidence support higher valuation multiples across the sector.", move: 0.4 },
        { label: "Geopolitical shock", description: "Political tension, trade restrictions or sanctions rapidly reshape expectations for growth and profitability.", move: -0.25 },
        { label: "Inflation spike", description: "Rising input costs and wage pressures squeeze margins and push investors to reassess valuation multiples.", move: -0.25 },
        { label: "Earthquake or natural disaster", description: "A severe weather event or physical disruption damages operations and increases uncertainty around future cash generation.", move: -0.5 },
        { label: "Commodity price surge", description: "Rising commodity prices improve revenues and margins for businesses with strong commodity exposure.", move: 0.5 },
        { label: "Interest rate shock", description: "Faster-than-expected borrowing costs weigh on valuations and hurt capital-intensive businesses.", move: -0.35 },
        { label: "Cybersecurity breach", description: "A data breach or operational incident raises concerns over resilience, compliance and customer trust.", move: -0.4 },
        { label: "Acquisition announcement", description: "A strategic acquisition or partnership lifts confidence in growth prospects and earnings quality.", move: 0.45 },
        { label: "Market re-rating", description: "Investors rotate into quality businesses and reward resilient operators with a stronger valuation.", move: 0.35 },
        { label: "No major change", description: "The market takes a breather and the stock remains broadly stable despite the wider noise.", move: 0.05 },
      ];

      function getCompanySpecificEvent(company) {
        const sector = company.sector?.toLowerCase() || "";

        const sectorEvents = {
          healthcare: [
            { label: "Safety concern", description: `Reports emerged that ${company.name}’s new treatment was linked to serious adverse events in clinical use, prompting emergency reviews and a sharp sell-off.`, move: -0.7 },
            { label: "Trial success", description: `A major phase-three study for ${company.name} delivered breakthrough results, boosting confidence in its long-term pipeline and lifting sentiment materially.`, move: 0.7 },
            { label: "Regulatory setback", description: `Officials raised concerns over ${company.name}’s latest product approval process, sending investors into a risk-off stance.`, move: -0.5 },
          ],
          technology: [
            { label: "Product recall", description: `${company.name} was forced to halt a flagship software rollout after a major defect caused customer outages and reputational damage.`, move: -0.45 },
            { label: "AI breakthrough", description: `${company.name} announced a major AI product launch that dramatically improved its growth outlook and sparked renewed investor optimism.`, move: 0.65 },
            { label: "Cyberattack", description: `${company.name} disclosed a major data breach affecting several enterprise clients, increasing regulatory and reputational concerns.`, move: -0.5 },
          ],
          energy: [
            { label: "Operational outage", description: `${company.name} suffered a major plant outage that cut output and raised questions over near-term earnings resilience.`, move: -0.4 },
            { label: "Energy policy tailwind", description: `${company.name} benefited from a fresh government clean-energy subsidy package, improving the outlook for future cash flows.`, move: 0.5 },
            { label: "Commodity swing", description: `${company.name} was lifted by a sharp rise in energy pricing that boosted earnings expectations for the quarter.`, move: 0.45 },
          ],
          consumer: [
            { label: "Product recall", description: `${company.name} recalled a major product line after quality-control issues raised concerns over brand trust and margins.`, move: -0.5 },
            { label: "Strong holiday demand", description: `${company.name} reported stronger-than-expected demand during the peak season, boosting investor confidence.`, move: 0.55 },
            { label: "Supply bottleneck", description: `${company.name} faced a major inventory shortage after disruption to its overseas supply chain.`, move: -0.4 },
          ],
          financials: [
            { label: "Credit concern", description: `${company.name} saw rising defaults in its loan book, prompting fears over profitability and capital strength.`, move: -0.45 },
            { label: "Strong earnings", description: `${company.name} reported better-than-expected lending income and capital generation, lifting the stock.`, move: 0.5 },
            { label: "Regulatory inquiry", description: `${company.name} was drawn into a major regulatory probe around underwriting practices and compliance controls.`, move: -0.4 },
          ],
          materials: [
            { label: "Mine incident", description: `${company.name} was hit by a serious mining accident that disrupted operations and raised safety concerns.`, move: -0.55 },
            { label: "Commodity strength", description: `${company.name} benefited from a sharp move higher in key metal prices, improving its near-term outlook.`, move: 0.6 },
            { label: "Permitting delay", description: `${company.name} faced a major permitting delay that could push back expansion plans and weaken sentiment.`, move: -0.4 },
          ],
          utilities: [
            { label: "Infrastructure failure", description: `${company.name} suffered a major grid failure that led to service disruption and higher repair costs.`, move: -0.4 },
            { label: "Regulatory support", description: `${company.name} received a favourable regulatory ruling that improved long-term earnings visibility.`, move: 0.45 },
            { label: "Rate review", description: `${company.name} was impacted by a rate review that raised concerns over future returns.`, move: -0.35 },
          ],
          industrials: [
            { label: "Factory shutdown", description: `${company.name} halted production at a key facility after a major equipment failure and safety investigation.`, move: -0.45 },
            { label: "Contract win", description: `${company.name} secured a large long-term contract that improved the outlook for future revenue growth.`, move: 0.5 },
            { label: "Trade restriction", description: `${company.name} was hit by fresh trade restrictions that disrupted exports and raised cost concerns.`, move: -0.4 },
          ],
          realestate: [
            { label: "Development delay", description: `${company.name} saw a major project delayed by planning issues, increasing concern over execution and cash flow.`, move: -0.45 },
            { label: "Property rally", description: `${company.name} benefited from a surge in property demand that boosted expectations for pricing and sales volumes.`, move: 0.5 },
            { label: "Rate pressure", description: `${company.name} faced rising financing costs that weakened the outlook for future developments.`, move: -0.4 },
          ],
          telecommunications: [
            { label: "Network outage", description: `${company.name} experienced a widespread outage that damaged customer trust and raised service concerns.`, move: -0.4 },
            { label: "Subscriber growth", description: `${company.name} reported strong subscriber growth and better-than-expected pricing power.`, move: 0.5 },
            { label: "Spectrum setback", description: `${company.name} was affected by a new spectrum ruling that raised costs and increased competitive pressure.`, move: -0.35 },
          ],
          consumerdiscretionary: [
            { label: "Brand backlash", description: `${company.name} faced a major public backlash over a product issue, hurting sentiment and sales expectations.`, move: -0.45 },
            { label: "Luxury demand", description: `${company.name} benefited from a strong rebound in premium consumer spending and upbeat demand trends.`, move: 0.5 },
            { label: "Inventory overhang", description: `${company.name} was forced to discount heavily after inventory levels rose faster than expected.`, move: -0.35 },
          ],
          consumerstaples: [
            { label: "Food safety issue", description: `${company.name} was linked to a food safety incident that sparked recalls and raised concerns over brand reliability.`, move: -0.5 },
            { label: "Volume growth", description: `${company.name} reported unexpectedly strong retail volume growth and higher market share.`, move: 0.45 },
            { label: "Input cost spike", description: `${company.name} faced higher packaging and ingredient costs that weighed on margins.`, move: -0.35 },
          ],
        };

        if (sectorEvents[sector]) {
          const positiveEvents = sectorEvents[sector].filter((event) => event.move >= 0);
          const negativeEvents = sectorEvents[sector].filter((event) => event.move < 0);
          if (Math.random() < 0.45 && positiveEvents.length) {
            return pickRandom(positiveEvents);
          }
          if (negativeEvents.length) {
            return pickRandom(negativeEvents);
          }
          return pickRandom(sectorEvents[sector]);
        }

        const positiveTemplates = eventTemplates.filter((event) => event.move >= 0);
        const negativeTemplates = eventTemplates.filter((event) => event.move < 0);
        if (Math.random() < 0.45 && positiveTemplates.length) {
          return pickRandom(positiveTemplates);
        }
        if (negativeTemplates.length) {
          return pickRandom(negativeTemplates);
        }
        return pickRandom(eventTemplates);
      }

      function init() {
        document.getElementById("startBtn").addEventListener("click", startGame);
        document.getElementById("resetBtn").addEventListener("click", resetGame);
        document.getElementById("allocationForm").addEventListener("submit", handleAllocation);
        document.getElementById("equalSplitBtn")?.addEventListener("click", fillEqualAllocation);
        document.getElementById("clearHistoryBtn")?.addEventListener("click", clearAttemptHistory);
        document.getElementById("playerName").addEventListener("keydown", (event) => {
          if (event.key === "Enter") {
            event.preventDefault();
            startGame();
          }
        });
        document.getElementById("reviewToggleBtn")?.addEventListener("click", toggleReviewPanel);
        renderSetup();
      }

      function renderSetup() {
        document.getElementById("setupSection").classList.remove("hidden");
        document.getElementById("gameSection").classList.add("hidden");
        document.getElementById("resultsSection").classList.add("hidden");
        window.scrollTo({ top: 0, behavior: "smooth" });
        renderAttemptHistory();
        document.getElementById("playerName").focus();
      }

      function startGame() {
        const input = document.getElementById("playerName");
        const name = input.value.trim();
        if (!name) {
          input.focus();
          return;
        }

        state.playerName = name;
        state.round = 1;
        state.wealth = STARTING_WEALTH;
        state.results = [];
        state.lastRoundReview = null;
        state.challengeSetup = buildChallengeSetup();
        renderRound();
      }

      function resetGame() {
        state.playerName = "";
        state.round = 1;
        state.wealth = STARTING_WEALTH;
        state.results = [];
        state.lastRoundReview = null;
        state.challengeSetup = null;
        document.getElementById("playerName").value = "";
        renderSetup();
      }

      function getPerformanceCategory(value) {
        const portfolioValue = Number(value) || 0;
        if (portfolioValue >= 1250000) return { label: "Excellent", color: "#8fb7e4", description: "Exceptional outcome — the portfolio has materially outperformed the starting point and the risk-taking paid off." };
        if (portfolioValue >= 1125000) return { label: "Strong", color: "#5d8fc8", description: "Very strong result — the portfolio has performed well and the allocation choices were broadly effective." };
        if (portfolioValue >= 1000000) return { label: "Solid", color: "#b7c7ff", description: "Good outcome — the portfolio held up well and ended at or above the starting level." };
        if (portfolioValue >= 900000) return { label: "Mixed", color: "#f2c36b", description: "Mixed outcome — results were uneven and the portfolio only narrowly avoided a loss." };
        return { label: "Needs work", color: "#f08d7f", description: "Needs work — the portfolio ended below the starting level and the strategy was not effective enough." };
      }

      function saveAttemptHistory() {
        const history = JSON.parse(localStorage.getItem("portfolioChallengeHistory") || "[]");
        const performance = getPerformanceCategory(state.wealth);
        const entry = {
          name: state.playerName,
          date: new Date().toLocaleDateString("en-GB"),
          finalValue: state.wealth,
          performance: performance.label,
        };

        const updatedHistory = [entry, ...history].slice(0, 8);
        localStorage.setItem("portfolioChallengeHistory", JSON.stringify(updatedHistory));
      }

      function renderAttemptHistory() {
        const historyList = document.getElementById("historyList");
        if (!historyList) return;

        const history = JSON.parse(localStorage.getItem("portfolioChallengeHistory") || "[]");
        if (!history.length) {
          historyList.innerHTML = '<li class="history-entry">No previous attempts yet.</li>';
          return;
        }

        historyList.innerHTML = history
          .map((entry) => {
            const performance = entry.performance || getPerformanceCategory(entry.finalValue).label;
            return `
              <li class="history-entry">
                <strong>${entry.name}</strong><br />
                ${entry.date} · £${formatCurrency(entry.finalValue)}<br />
                <span style="color:${getPerformanceCategory(entry.finalValue).color}; font-weight:700;">${performance}</span>
              </li>
            `;
          })
          .join("");
      }

      function clearAttemptHistory() {
        localStorage.removeItem("portfolioChallengeHistory");
        renderAttemptHistory();
      }

      function getCompanyMomentumContext(previousRoundResults, companyId) {
        if (!previousRoundResults?.length) {
          return { allocationBias: 1, signal: "" };
        }

        const previousCompany = previousRoundResults.find((entry) => entry.id === companyId);
        if (!previousCompany) {
          return { allocationBias: 1, signal: "" };
        }

        const previousReturn = ((previousCompany.newPrice - previousCompany.startPrice) / previousCompany.startPrice) || 0;
        if (previousReturn > 0.12) {
          return {
            allocationBias: 0.7,
            signal: `Momentum warning: ${previousCompany.name} performed strongly last round, so the next macro backdrop is likely to favour trimming exposure rather than adding to it.`,
          };
        }

        if (previousReturn < -0.08) {
          return {
            allocationBias: 1.15,
            signal: `Contrarian signal: ${previousCompany.name} was weaker last round, so the next round may offer a lower-risk entry point if the macro backdrop improves.`,
          };
        }

        return { allocationBias: 1, signal: "" };
      }

      function buildEvenAllocation(total, count) {
        if (count <= 0) return [];

        const roundedTotal = Math.round(total);
        const base = Math.floor(roundedTotal / count);
        const remainder = roundedTotal % count;
        const values = Array(count).fill(base);

        if (count > 0) {
          values[count - 1] += remainder;
        }

        return values;
      }

      function buildDefaultAllocations(wealth, companies) {
        const weights = companies.map((company) => company.allocationBias ?? 1);
        const totalWeight = weights.reduce((sum, weight) => sum + weight, 0) || 1;
        const rawValues = weights.map((weight) => wealth * (weight / totalWeight));

        const values = rawValues.map((value) => Math.floor(value));
        const totalAllocated = values.reduce((sum, value) => sum + value, 0);
        const difference = Math.round(wealth) - totalAllocated;

        if (difference !== 0) {
          values[0] += difference;
        }

        return values;
      }

      function renderRound() {
        const roundData = buildRoundData(state.challengeSetup, state.round);
        state.roundData = roundData;

        document.getElementById("setupSection").classList.add("hidden");
        document.getElementById("gameSection").classList.remove("hidden");
        document.getElementById("resultsSection").classList.add("hidden");
        window.scrollTo({ top: 0, behavior: "smooth" });

        const roundBanner = document.getElementById("roundBanner");
        roundBanner.innerHTML = `<strong>Round ${state.round}</strong> of ${ROUND_COUNT} — ${state.playerName}, you have £${formatCurrency(state.wealth)} to allocate.`;

        const countryCard = document.getElementById("countryCard");
        countryCard.innerHTML = `
          <h2>${roundData.country.name}</h2>
          <p><strong>Context:</strong> ${roundData.country.description}</p>
          <p><strong>Economy:</strong> ${roundData.country.economy}</p>
          <p><strong>Macro theme:</strong> ${roundData.scenarioHeadline}</p>
        `;

        const defaultAllocations = buildDefaultAllocations(state.wealth, roundData.companies);
        const companyGrid = document.getElementById("companyGrid");
        companyGrid.innerHTML = roundData.companies
          .map((company, index) => {
            const defaultAllocation = defaultAllocations[index];
            const cautionText = company.forwardSignal
              ? `<p class="forward-signal"><strong>Forward signal:</strong> ${company.forwardSignal}</p>`
              : "";
            return `
              <div class="company-card">
                <span class="price-pill">${company.sector}</span>
                <h3>${company.name}</h3>
                <p>${company.description}</p>
                <p><strong>Context:</strong> ${company.context}</p>
                <p><strong>What to watch:</strong> ${company.watchlist}</p>
                <p><strong>Opening price:</strong> $${company.startPrice.toFixed(2)}</p>
                ${cautionText}
                <label for="company-${index}">Allocation (£)</label>
                <div class="allocation-controls">
                  <input id="company-${index}" type="text" class="allocation-input" inputmode="numeric" value="${formatInputValue(defaultAllocation)}" />
                  <button type="button" class="clear-btn" data-index="${index}" aria-label="Clear allocation">⌫</button>
                </div>
                <div class="share-hint" id="share-${index}">≈ 0.00 shares</div>
                <div class="adjust-row">
                  <input id="adjust-${index}" type="text" class="adjust-value" inputmode="numeric" value="25,000" />
                  <button type="button" class="adjust-btn" data-index="${index}" data-direction="add">+ add</button>
                  <button type="button" class="adjust-btn" data-index="${index}" data-direction="subtract">− reduce</button>
                </div>
              </div>
            `;
          })
          .join("");

        renderReviewControls();

        document.querySelectorAll(".allocation-input").forEach((input) => {
          input.addEventListener("input", (event) => {
            event.target.value = formatInputValue(event.target.value);
            updateAllocationSummary();
          });
        });

        document.querySelectorAll(".adjust-value").forEach((input) => {
          input.addEventListener("input", (event) => {
            event.target.value = formatInputValue(event.target.value);
          });
        });

        document.querySelectorAll(".adjust-btn").forEach((button) => {
          button.addEventListener("click", () => applyAdjustment(button));
        });

        document.querySelectorAll(".clear-btn").forEach((button) => {
          button.addEventListener("click", () => clearAllocation(button));
        });

        updateAllocationSummary();
      }

      function buildChallengeSetup() {
        const country = pickRandom(countryPool);
        const companies = shuffle(companyPool)
          .slice(0, 4)
          .map((company, index) => ({
            ...company,
            startPrice: Number((1.8 + index * 0.35 + Math.random() * 0.9).toFixed(2)),
          }));

        return {
          country,
          companies,
        };
      }

      function buildRoundData(challengeSetup, roundNumber) {
        const previousRoundResults = state.results[state.results.length - 1]?.results || [];
        const previousRoundLoss = previousRoundResults.some((entry) => entry.value < entry.amount);

        const negativeMacroSignals = [
          "Global rates remain elevated and investors are rotating away from high-beta names.",
          "The country’s macro backdrop is mixed, with political risk rising alongside still-healthy growth.",
          "Markets are looking for companies with defensive cash flows and less exposure to trade disruption.",
        ];

        const positiveMacroSignals = [
          "The broad market backdrop is improving and investors are willing to re-rate higher-growth businesses again.",
          "A more supportive macro backdrop is encouraging rotation back toward quality growth names.",
          "Improving confidence is allowing investors to focus more on earnings momentum than short-term risk aversion.",
          "The economy is stabilising and investors are gradually rewarding durable earnings and execution.",
        ];

        const scenarioHeadline = pickRandom(
          previousRoundLoss ? negativeMacroSignals : positiveMacroSignals
        );

        const macroUpdate = pickRandom([
          `The macro backdrop is stabilising, and investors are becoming slightly more comfortable taking measured positions in quality companies.`,
          `The growth story is still intact, but a more constructive backdrop is supporting gradual gains rather than sharp outsized swings.`,
          `Investors are beginning to reward steadier earnings quality again, while still remaining selective on highly cyclical names.`,
          `The market is calmer than before, with confidence recovering enough to support a more gradual upward trend across the broader portfolio.`,
        ]);

        const marketSignal = pickRandom([
          "The market is rewarding firms with pricing power and punishing those reliant on fragile supply chains.",
          "Investors are rotating towards cash-generative businesses with lower sensitivity to political noise.",
          "Volatility is moderating, so guidance and execution are starting to matter more than headline momentum alone.",
          "Recent strength is encouraging a steadier, more constructive tone for investors seeking durable returns rather than short-term spikes.",
        ]);

        const companies = challengeSetup.companies.map((company) => {
          const momentum = getCompanyMomentumContext(previousRoundResults, company.id);
          const isMacroNegative = scenarioHeadline.toLowerCase().includes("rates") || scenarioHeadline.toLowerCase().includes("mixed") || scenarioHeadline.toLowerCase().includes("defensive") || scenarioHeadline.toLowerCase().includes("trade disruption");

          return {
            ...company,
            allocationBias: isMacroNegative ? momentum.allocationBias : 0.9,
            forwardSignal: isMacroNegative && momentum.signal ? momentum.signal : "The broader tone is mildly negative, so this company is better treated as a measured holding rather than a high-conviction allocation.",
          };
        });

        return {
          country: challengeSetup.country,
          companies,
          scenarioHeadline,
          macroUpdate,
          marketSignal,
          roundNumber,
        };
      }

      function renderReviewControls() {
        const reviewButton = document.getElementById("reviewToggleBtn");
        const reviewPanel = document.getElementById("reviewPanel");

        if (!state.lastRoundReview) {
          reviewButton?.classList.add("hidden");
          reviewPanel?.classList.add("hidden");
          return;
        }

        reviewButton?.classList.remove("hidden");
        reviewPanel?.classList.add("hidden");
        reviewButton.textContent = state.round > 1 ? "Review previous round" : "Review last round";
      }

      function toggleReviewPanel() {
        const reviewPanel = document.getElementById("reviewPanel");
        if (!state.lastRoundReview || !reviewPanel) return;

        const isHidden = reviewPanel.classList.contains("hidden");
        reviewPanel.classList.toggle("hidden", !isHidden);

        if (!isHidden) {
          reviewPanel.innerHTML = "";
          return;
        }

        reviewPanel.innerHTML = `
          <h3>Previous round review</h3>
          <p><strong>${state.lastRoundReview.country.name}</strong> — ${state.lastRoundReview.country.description}</p>
          <p><strong>Portfolio value:</strong> £${formatCurrency(state.lastRoundReview.portfolioValue)}</p>
          <p><strong>Macro update:</strong> ${state.lastRoundReview.macroUpdate}</p>
          <div class="result-grid">
            ${state.lastRoundReview.results
              .map((item) => `
                <div class="result-item">
                  <h3>${item.name}</h3>
                  <p><strong>Event:</strong> ${item.event.label} — ${item.event.description}</p>
                  <p><strong>Price:</strong> $${item.startPrice.toFixed(2)} → $${item.newPrice.toFixed(2)}</p>
                </div>
              `)
              .join("")}
          </div>
          <button type="button" class="primary-btn" id="closeReviewBtn">Back to allocation</button>
        `;

        document.getElementById("closeReviewBtn")?.addEventListener("click", toggleReviewPanel);
      }

      function updateAllocationSummary() {
        const inputs = Array.from(document.querySelectorAll(".allocation-input"));
        const total = inputs.reduce((sum, input) => sum + parseNumericInputValue(input.value), 0);
        const remaining = state.wealth - total;
        const normalizedRemaining = Math.abs(remaining) <= 2 ? 0 : remaining;
        document.getElementById("allocationDisplay").textContent = `£${formatCurrency(total)}`;
        document.getElementById("remainingDisplay").textContent = `£${formatCurrency(normalizedRemaining)}`;
        document.getElementById("wealthDisplay").textContent = `£${formatCurrency(state.wealth)}`;

        if (Math.abs(remaining) <= 2) {
          document.getElementById("remainingDisplay").textContent = "£0";
        }

        inputs.forEach((input, index) => {
          const company = state.roundData?.companies?.[index];
          const amount = parseNumericInputValue(input.value);
          const shareCount = company ? amount / company.startPrice : 0;
          const hint = document.getElementById(`share-${index}`);
          if (hint) {
            hint.textContent = `≈ ${shareCount.toFixed(2)} shares at $${company.startPrice.toFixed(2)}`;
          }
        });
      }

      function fillEqualAllocation() {
        const inputs = Array.from(document.querySelectorAll(".allocation-input"));
        if (!inputs.length) return;

        const values = buildEvenAllocation(state.wealth, inputs.length);
        inputs.forEach((input, index) => {
          input.value = values[index];
        });

        updateAllocationSummary();
      }

      function clearAllocation(button) {
        const index = Number(button.dataset.index);
        const input = document.querySelector(`#company-${index}`);
        if (input) {
          input.value = "";
          updateAllocationSummary();
        }
      }

      function applyAdjustment(button) {
        const index = Number(button.dataset.index);
        const input = document.querySelector(`#company-${index}`);
        const adjustmentInput = document.querySelector(`#adjust-${index}`);
        if (!input || !adjustmentInput) return;

        const currentValue = parseNumericInputValue(input.value);
        const adjustment = parseNumericInputValue(adjustmentInput.value);
        const nextValue = button.dataset.direction === "add" ? currentValue + adjustment : Math.max(0, currentValue - adjustment);
        input.value = nextValue;
        updateAllocationSummary();
      }

      function handleAllocation(event) {
        event.preventDefault();
        const inputs = Array.from(document.querySelectorAll(".allocation-input"));
        const allocations = inputs.map((input) => parseNumericInputValue(input.value));
        const total = allocations.reduce((sum, value) => sum + value, 0);
        const tolerance = 2;
        const difference = state.wealth - total;

        if (Math.abs(difference) > tolerance) {
          document.getElementById("remainingDisplay").textContent = `£${formatCurrency(state.wealth - total)} — allocate the full portfolio`;
          return;
        }

        if (Math.abs(difference) > 0) {
          const lastInput = inputs[inputs.length - 1];
          if (lastInput) {
            const lastValue = parseNumericInputValue(lastInput.value);
            lastInput.value = Math.max(0, lastValue + difference);
            updateAllocationSummary();
          }
        }

        const adjustedAllocations = inputs.map((input) => parseNumericInputValue(input.value));
        const adjustedTotal = adjustedAllocations.reduce((sum, value) => sum + value, 0);
        const roundedDifference = state.wealth - adjustedTotal;

        if (Math.abs(roundedDifference) > tolerance) {
          document.getElementById("remainingDisplay").textContent = `£${formatCurrency(state.wealth - adjustedTotal)} — allocate the full portfolio`;
          return;
        }

        const results = state.roundData.companies.map((company, index) => {
          const amount = adjustedAllocations[index];
          const shares = amount / company.startPrice;
          const event = getCompanySpecificEvent(company);
          const sensitivity = company.sensitivity || 1;
          const priceImpact = Math.max(-0.08, Math.min(0.15, event.move * sensitivity * 0.28));
          const newPrice = Number(Math.max(0.05, company.startPrice * (1 + priceImpact)).toFixed(2));
          const value = shares * newPrice;

          return {
            ...company,
            amount,
            shares,
            event,
            startPrice: company.startPrice,
            newPrice,
            value,
          };
        });

        const portfolioValue = results.reduce((sum, item) => sum + item.value, 0);
        state.wealth = Number(portfolioValue.toFixed(2));
        state.lastRoundReview = {
          round: state.round,
          country: state.roundData.country,
          macroUpdate: state.roundData.macroUpdate,
          marketSignal: state.roundData.marketSignal,
          portfolioValue: state.wealth,
          results,
        };
        state.results.push({ round: state.round, results, country: state.roundData.country, portfolioValue: state.wealth });

        renderResults(results);
      }

      function finishGame() {
        saveAttemptHistory();
        renderFinalSummary();
      }

      function renderResults(results) {
        document.getElementById("gameSection").classList.add("hidden");
        document.getElementById("resultsSection").classList.remove("hidden");
        window.scrollTo({ top: 0, behavior: "smooth" });

        if (state.round >= ROUND_COUNT) {
          finishGame();
          return;
        }

        const change = state.wealth - STARTING_WEALTH;
        const percentChange = STARTING_WEALTH ? (change / STARTING_WEALTH) * 100 : 0;
        const summary = `
          <h2>Round ${state.round} complete</h2>
          <p><strong>${state.playerName}</strong> finished the round with a portfolio value of <strong>£${formatCurrency(state.wealth)}</strong>.</p>
          <p>${change >= 0 ? "You created value" : "You lost value"} this round, with a ${percentChange >= 0 ? "gain" : "loss"} of ${Math.abs(percentChange).toFixed(1)}%.</p>
        `;

        const items = results
          .map((item) => {
            const gain = item.value - item.amount;
            const statusClass = gain >= 0 ? "good" : "bad";
            return `
              <div class="result-item">
                <h3>${item.name}</h3>
                <p><strong>Event:</strong> ${item.event.label} — ${item.event.description}</p>
                <p><strong>Price:</strong> $${item.startPrice.toFixed(2)} → $${item.newPrice.toFixed(2)}</p>
                <p><strong>Allocation:</strong> £${formatCurrency(item.amount)}</p>
                <p><strong>Position value:</strong> £${formatCurrency(item.value.toFixed(2))}</p>
                <p class="${statusClass}"><strong>Round impact:</strong> ${gain >= 0 ? "+" : ""}£${formatCurrency(gain.toFixed(2))}</p>
              </div>
            `;
          })
          .join("");

        document.getElementById("resultsSection").innerHTML = `
          ${summary}
          <div class="result-grid">
            <div class="result-item">
              <h3>Macro environment update</h3>
              <p>${state.roundData.macroUpdate}</p>
              <p><strong>Market signal:</strong> ${state.roundData.marketSignal}</p>
            </div>
            ${items}
          </div>
          <button id="nextRoundBtn" class="primary-btn">Move to next round</button>
        `;

        document.getElementById("nextRoundBtn")?.addEventListener("click", nextRound);
      }

      function renderFinalSummary() {
        const overallChange = state.wealth - STARTING_WEALTH;
        const percentChange = STARTING_WEALTH ? (overallChange / STARTING_WEALTH) * 100 : 0;
        const direction = overallChange >= 0 ? "gain" : "loss";
        const performance = getPerformanceCategory(state.wealth);
        const sentence = `${state.playerName}, you finished the challenge with a ${direction} of ${Math.abs(percentChange).toFixed(1)}%, ending at £${formatCurrency(state.wealth)} from your starting £1,000,000. Professional wealth managers typically target annual growth of around 5%; this challenge reflects that long-term approach, where patience and stability matter more than immediate rewards.`;

        const roundSummary = state.results
          .map((entry) => `
            <div class="result-item">
              <h3>Round ${entry.round}</h3>
              <p><strong>Country:</strong> ${entry.country.name}</p>
              <p><strong>Portfolio value:</strong> £${formatCurrency(entry.portfolioValue)}</p>
            </div>
          `)
          .join("");

        document.getElementById("resultsSection").innerHTML = `
          <div class="summary-hero">
            <h2>Challenge complete</h2>
            <p class="summary-sentence">${sentence}</p>
          </div>
          <div class="result-grid">
            <div class="result-item summary-highlight">
              <h3>Final portfolio</h3>
              <p><strong>Final value:</strong> £${formatCurrency(state.wealth)}</p>
              <p><strong>Overall change:</strong> ${overallChange >= 0 ? "+" : ""}£${formatCurrency(overallChange.toFixed(2))} (${overallChange >= 0 ? "+" : ""}${percentChange.toFixed(1)}%)</p>
              <p><strong>Performance:</strong> <span style="color:${performance.color}; font-weight:700;">${performance.label}</span></p>
              <p>${performance.description}</p>
              <p><strong>Band ranges:</strong></p>
              <p>• Excellent: £1,250,000+</p>
              <p>• Strong: £1,125,000–£1,249,999</p>
              <p>• Solid: £1,000,000–£1,124,999</p>
              <p>• Mixed: £900,000–£999,999</p>
              <p>• Needs work: below £900,000</p>
            </div>
            ${roundSummary}
          </div>
          <button id="playAgainBtn" class="primary-btn">Play again</button>
        `;

        document.getElementById("playAgainBtn")?.addEventListener("click", resetGame);
      }

      function nextRound() {
        if (state.round < ROUND_COUNT) {
          state.round += 1;
          renderRound();
        }
      }

      function formatCurrency(value) {
        return Number(value).toLocaleString("en-GB", {
          minimumFractionDigits: 0,
          maximumFractionDigits: 0,
        });
      }

      function parseNumericInputValue(value) {
        if (value === null || value === undefined || value === "") {
          return 0;
        }

        const cleaned = String(value).replace(/,/g, "").replace(/[^\d.-]/g, "");
        if (!cleaned) {
          return 0;
        }

        const parsed = Number(cleaned);
        return Number.isFinite(parsed) ? Math.max(0, Math.round(parsed)) : 0;
      }

      function formatInputValue(value) {
        const parsed = parseNumericInputValue(value);
        return parsed === 0 ? "" : parsed.toLocaleString("en-GB");
      }

      function pickRandom(array) {
        return array[Math.floor(Math.random() * array.length)];
      }

      function shuffle(array) {
        const copy = [...array];
        for (let i = copy.length - 1; i > 0; i -= 1) {
          const j = Math.floor(Math.random() * (i + 1));
          [copy[i], copy[j]] = [copy[j], copy[i]];
        }
        return copy;
      }

      init();
    </script>
  </body>
</html>
