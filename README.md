
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Smooche | CX Macro Dashboard 💋</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
  
  <style>
    :root {
      /* Smooche Palette derived from brand screenshot */
      --bg-cream: #FAF7F5;
      --card-bg: #FFFFFF;
      --primary-rose: #D87B8C;
      --rose-dark: #B8596C;
      --rose-light: #F9ECEF;
      --rose-tag: #F3D3DA;
      --text-dark: #2B2325;
      --text-muted: #7A6C70;
      --border-color: #EFE4E6;
      --shadow-sm: 0 4px 12px rgba(216, 123, 140, 0.08);
      --shadow-hover: 0 8px 24px rgba(216, 123, 140, 0.15);
      
      /* Category Color Highlights */
      --cat-shipping: #D87B8C;
      --cat-product: #C36B84;
      --cat-returns: #B8596C;
      --cat-general: #A8495C;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Plus Jakarta Sans', sans-serif;
    }

    body {
      background-color: var(--bg-cream);
      color: var(--text-dark);
      padding: 2rem 1rem;
      min-height: 100vh;
    }

    .container {
      max-width: 1200px;
      margin: 0 auto;
    }

    /* Header Styling */
    header {
      text-align: center;
      margin-bottom: 2.5rem;
    }

    .brand-logo {
      font-size: 2.2rem;
      font-weight: 800;
      letter-spacing: 2px;
      color: var(--text-dark);
      text-transform: uppercase;
      margin-bottom: 0.5rem;
    }

    .brand-subtitle {
      font-size: 1rem;
      color: var(--rose-dark);
      font-weight: 600;
    }

    /* Search & Filter Controls */
    .controls-card {
      background: var(--card-bg);
      border-radius: 16px;
      padding: 1.5rem;
      box-shadow: var(--shadow-sm);
      border: 1px solid var(--border-color);
      margin-bottom: 2rem;
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }

    .search-wrapper {
      position: relative;
      width: 100%;
    }

    .search-wrapper input {
      width: 100%;
      padding: 0.85rem 1rem 0.85rem 2.75rem;
      border: 2px solid var(--border-color);
      border-radius: 12px;
      font-size: 0.95rem;
      outline: none;
      transition: border-color 0.2s;
      background: var(--bg-cream);
    }

    .search-wrapper input:focus {
      border-color: var(--primary-rose);
    }

    .search-icon {
      position: absolute;
      left: 1rem;
      top: 50%;
      transform: translateY(-50%);
      font-size: 1.1rem;
    }

    .filter-pills {
      display: flex;
      flex-wrap: wrap;
      gap: 0.5rem;
    }

    .pill {
      padding: 0.5rem 1.25rem;
      border-radius: 50px;
      background: var(--bg-cream);
      color: var(--text-muted);
      border: 1px solid var(--border-color);
      font-size: 0.85rem;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.2s ease;
    }

    .pill:hover, .pill.active {
      background: var(--primary-rose);
      color: white;
      border-color: var(--primary-rose);
    }

    /* Category Section Headers */
    .category-section {
      margin-bottom: 3rem;
    }

    .category-header {
      background: var(--primary-rose);
      color: white;
      padding: 1rem 1.5rem;
      border-radius: 12px;
      margin-bottom: 1.5rem;
      box-shadow: var(--shadow-sm);
    }

    .category-header h2 {
      font-size: 1.3rem;
      font-weight: 700;
    }

    .category-header p {
      font-size: 0.88rem;
      opacity: 0.92;
      margin-top: 0.2rem;
      font-style: italic;
    }

    /* Template Cards Grid */
    .templates-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
      gap: 1.5rem;
    }

    .card {
      background: var(--card-bg);
      border-radius: 16px;
      border: 1px solid var(--border-color);
      padding: 1.25rem;
      box-shadow: var(--shadow-sm);
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      transition: transform 0.2s, box-shadow 0.2s;
    }

    .card:hover {
      transform: translateY(-2px);
      box-shadow: var(--shadow-hover);
    }

    .card-top {
      margin-bottom: 1rem;
    }

    .card-title-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 0.75rem;
    }

    .card-title {
      font-size: 1.05rem;
      font-weight: 700;
      color: var(--text-dark);
    }

    .tag {
      font-size: 0.75rem;
      padding: 0.25rem 0.6rem;
      border-radius: 20px;
      background: var(--rose-light);
      color: var(--rose-dark);
      font-weight: 600;
    }

    /* Template Variables Controls */
    .variable-inputs {
      background: var(--bg-cream);
      padding: 0.75rem;
      border-radius: 10px;
      margin-bottom: 1rem;
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
    }

    .var-field {
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }

    .var-field label {
      font-size: 0.75rem;
      font-weight: 700;
      color: var(--rose-dark);
      width: 80px;
      text-transform: uppercase;
    }

    .var-field input {
      flex: 1;
      padding: 0.35rem 0.5rem;
      font-size: 0.82rem;
      border: 1px solid var(--border-color);
      border-radius: 6px;
      outline: none;
    }

    .var-field input:focus {
      border-color: var(--primary-rose);
    }

    /* Editable Template Area */
    .template-body {
      width: 100%;
      min-height: 140px;
      padding: 0.85rem;
      font-size: 0.88rem;
      color: var(--text-dark);
      border: 1px solid var(--border-color);
      border-radius: 10px;
      resize: vertical;
      outline: none;
      background: var(--card-bg);
      line-height: 1.45;
      margin-bottom: 0.75rem;
    }

    .template-body:focus {
      border-color: var(--primary-rose);
    }

    /* Intercom Reference Field */
    .intercom-field {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      margin-bottom: 1rem;
    }

    .intercom-field input {
      flex: 1;
      padding: 0.35rem 0.5rem;
      font-size: 0.8rem;
      border: 1px dashed var(--border-color);
      border-radius: 6px;
      color: var(--text-muted);
    }

    /* Action Buttons */
    .card-actions {
      display: flex;
      gap: 0.5rem;
    }

    .btn {
      flex: 1;
      padding: 0.6rem 0.8rem;
      border-radius: 8px;
      border: none;
      font-size: 0.85rem;
      font-weight: 600;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.4rem;
      transition: background 0.2s;
    }

    .btn-primary {
      background: var(--primary-rose);
      color: white;
    }

    .btn-primary:hover {
      background: var(--rose-dark);
    }

    .btn-secondary {
      background: var(--rose-light);
      color: var(--rose-dark);
    }

    .btn-secondary:hover {
      background: var(--rose-tag);
    }

    .toast {
      position: fixed;
      bottom: 2rem;
      right: 2rem;
      background: var(--text-dark);
      color: white;
      padding: 0.8rem 1.5rem;
      border-radius: 30px;
      font-size: 0.88rem;
      font-weight: 600;
      box-shadow: 0 4px 15px rgba(0,0,0,0.2);
      display: none;
      z-index: 100;
    }

    @media (max-width: 600px) {
      .templates-grid {
        grid-template-columns: 1fr;
      }
      .controls-card {
        padding: 1rem;
      }
    }
  </style>
</head>
<body>

  <div class="container">
    <header>
      <div class="brand-logo">SMOOCHE 💋</div>
      <div class="brand-subtitle">CX Macro & Email Template Dashboard</div>
    </header>

    <!-- Search & Filter Controls -->
    <div class="controls-card">
      <div class="search-wrapper">
        <span class="search-icon">🔎</span>
        <input type="text" id="searchInput" placeholder="Search templates by title, keyword, or text..." oninput="filterTemplates()">
      </div>
      <div class="filter-pills" id="filterPills">
        <button class="pill active" onclick="setCategory('all', this)">All Categories</button>
        <button class="pill" onclick="setCategory('Shipping & Tracking', this)">📦 Shipping & Tracking</button>
        <button class="pill" onclick="setCategory('Shade & Formula', this)">✨ Shade & Formula</button>
        <button class="pill" onclick="setCategory('Returns & Guarantee', this)">💖 Returns & Guarantee</button>
      </div>
    </div>

    <!-- Container where categories and templates load dynamically -->
    <div id="dashboardContent"></div>
  </div>

  <div class="toast" id="toast">Copied to clipboard! ✨</div>

  <script>
    // Initial Macro Data Set
    const initialTemplates = [
      {
        id: "macro-1",
        title: "Order Tracking Update",
        category: "Shipping & Tracking",
        categorySubtitle: "Keeping it smooth, seamless, and tracked to their doorstep. 📦✨",
        intercomRef: "https://app.intercom.com/a/apps/xyz/inbox/inbox/123",
        vars: { CUSTOMER: "Babe", ORDER: "#1001", LINK: "https://smooche.com/track" },
        text: "Hi {{CUSTOMER}},\n\nYour Smooche order {{ORDER}} is officially on its way! 🚚 You can track your glow up in real-time right here: {{LINK}}\n\nLet us know if you need anything else!\n\nLove,\nThe Smooche Team 💋"
      },
      {
        id: "macro-2",
        title: "Adaptive Formula Support",
        category: "Shade & Formula",
        categorySubtitle: "Self-adjusting magic, flawless matches, zero stress. 💄💫",
        intercomRef: "",
        vars: { CUSTOMER: "Gorgeous", PRODUCT: "Color Changing Foundation" },
        text: "Hi {{CUSTOMER}},\n\nThanks for reaching out about the {{PRODUCT}}! 💋 Remember, our adaptive pigment formula reacts to your skin's natural warmth as you blend. Give it 30 seconds to fully adjust to your unique tone!\n\nLet us know how it feels after trying it out!\n\nBest,\nThe Smooche Team 💋"
      },
      {
        id: "macro-3",
        title: "30-Day Guarantee / Return Request",
        category: "Returns & Guarantee",
        categorySubtitle: "Worry-free beauty. If it’s not love at first swipe, we’ve got them. 💖",
        intercomRef: "https://app.intercom.com/a/apps/xyz/inbox/inbox/456",
        vars: { CUSTOMER: "Babe", ORDER: "#1002" },
        text: "Hi {{CUSTOMER}},\n\nWe want you to absolutely love your Smooche experience! 💖 Since you're covered by our 30-Day Money-Back Guarantee for order {{ORDER}}, we'd be happy to process a hassle-free refund or exchange for you.\n\nPlease confirm if you'd prefer a replacement or a full refund!\n\nWarmly,\nThe Smooche Team 💋"
      }
    ];

    // Store state in local memory
    let templatesData = JSON.parse(JSON.stringify(initialTemplates));
    let selectedCategory = 'all';

    function renderDashboard() {
      const container = document.getElementById('dashboardContent');
      const searchQuery = document.getElementById('searchInput').value.toLowerCase();
      container.innerHTML = '';

      // Filter templates based on category & search input
      const filtered = templatesData.filter(t => {
        const matchesCat = (selectedCategory === 'all' || t.category === selectedCategory);
        const matchesSearch = t.title.toLowerCase().includes(searchQuery) ||
                              t.text.toLowerCase().includes(searchQuery) ||
                              t.category.toLowerCase().includes(searchQuery);
        return matchesCat && matchesSearch;
      });

      if (filtered.length === 0) {
        container.innerHTML = `<div style="text-align:center; padding:3rem; color:var(--text-muted);">No macros found matching your search. 💋</div>`;
        return;
      }

      // Group by Category
      const categories = [...new Set(filtered.map(t => t.category))];

      categories.forEach(cat => {
        const catTemplates = filtered.filter(t => t.category === cat);
        const catSubtitle = catTemplates[0]?.categorySubtitle || "Smooche CX Templates";

        const section = document.createElement('div');
        section.className = 'category-section';

        section.innerHTML = `
          <div class="category-header">
            <h2>${cat}</h2>
            <p>${catSubtitle}</p>
          </div>
          <div class="templates-grid" id="grid-${cat.replace(/\s+/g, '-')}"></div>
        `;

        container.appendChild(section);

        const grid = section.querySelector(`.templates-grid`);

        catTemplates.forEach(t => {
          const card = document.createElement('div');
          card.className = 'card';

          // Build dynamic variable inputs
          let varInputsHTML = '';
          for (let key in t.vars) {
            varInputsHTML += `
              <div class="var-field">
                <label>${key}</label>
                <input type="text" value="${t.vars[key]}" oninput="updateVar('${t.id}', '${key}', this.value)">
              </div>
            `;
          }

          card.innerHTML = `
            <div class="card-top">
              <div class="card-title-row">
                <span class="card-title">${t.title}</span>
                <span class="tag">${t.category}</span>
              </div>
              
              <div class="variable-inputs">
                ${varInputsHTML}
              </div>

              <textarea class="template-body" id="text-${t.id}" oninput="updateTextDirectly('${t.id}', this.value)">${renderTextWithVars(t)}</textarea>

              <div class="intercom-field">
                <label style="font-size:0.75rem; color:var(--text-muted);">🔗 Intercom Ref:</label>
                <input type="text" value="${t.intercomRef}" placeholder="Paste ticket link..." onchange="updateIntercomRef('${t.id}', this.value)">
              </div>
            </div>

            <div class="card-actions">
              <button class="btn btn-primary" onclick="copyTemplate('${t.id}')">📋 Copy Macro</button>
              <button class="btn btn-secondary" onclick="restoreOriginal('${t.id}')">↩️ Restore</button>
            </div>
          `;

          grid.appendChild(card);
        });
      });
    }

    function renderTextWithVars(t) {
      let result = t.text;
      for (let key in t.vars) {
        const regex = new RegExp(`{{${key}}}`, 'g');
        result = result.replace(regex, t.vars[key]);
      }
      return result;
    }

    function updateVar(id, key, val) {
      const template = templatesData.find(t => t.id === id);
      if (template) {
        template.vars[key] = val;
        document.getElementById(`text-${id}`).value = renderTextWithVars(template);
      }
    }

    function updateTextDirectly(id, newText) {
      const template = templatesData.find(t => t.id === id);
      if (template) {
        template.text = newText;
      }
    }

    function updateIntercomRef(id, ref) {
      const template = templatesData.find(t => t.id === id);
      if (template) {
        template.intercomRef = ref;
      }
    }

    function restoreOriginal(id) {
      const orig = initialTemplates.find(t => t.id === id);
      const currentIdx = templatesData.findIndex(t => t.id === id);
      if (orig && currentIdx !== -1) {
        templatesData[currentIdx] = JSON.parse(JSON.stringify(orig));
        renderDashboard();
        showToast("Template restored to original! ↩️");
      }
    }

    function copyTemplate(id) {
      const textArea = document.getElementById(`text-${id}`);
      navigator.clipboard.writeText(textArea.value).then(() => {
        showToast("Macro copied to clipboard! 💋");
      });
    }

    function showToast(msg) {
      const toast = document.getElementById('toast');
      toast.innerText = msg;
      toast.style.display = 'block';
      setTimeout(() => {
        toast.style.display = 'none';
      }, 2500);
    }

    function setCategory(cat, btn) {
      selectedCategory = cat;
      document.querySelectorAll('.filter-pills .pill').forEach(p => p.classList.remove('active'));
      btn.classList.add('active');
      renderDashboard();
    }

    function filterTemplates() {
      renderDashboard();
    }

    // Initial Render
    renderDashboard();
  </script>
</body>
</html>
