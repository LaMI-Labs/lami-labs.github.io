---
title: Research
date: 2024-01-01
type: landing

design:
  spacing: "6rem"

sections:
  - block: markdown
    id: research
    content:
      title: ""
      text: |
        <section class="research-section">
          <h2 class="research-section-title">Our Mission</h2>
          <div class="research-section-divider"></div>
          <p class="research-mission-text">Write your lab mission statement here.</p>
          <p class="research-mission-text" style="margin-top: 0.85rem;">To this end, our research focuses on Knowledge Integration, enabling the adaptation of large foundation models to domain-specific physical tasks. We explore World Models and test-time self-evolving architectures to ensure adaptive and resilient behavior under real-world uncertainty, and ultimately pursue efficient on-device AI that delivers reliable intelligence on resource-constrained systems.</p>
        </section>

        <section class="research-section">
          <h2 class="research-section-title">Research Area</h2>
          <div class="research-section-divider"></div>
        </section>

        {{< research-cards >}}
    design:
      spacing:
        padding: ["2rem", 0, "2rem", 0]
      css_style: "max-width: 100% !important; width: 100% !important;"
      container: false
---
