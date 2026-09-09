---
title: Info
date: 2024-01-01
type: landing

design:
  spacing: "6rem"

sections:
  - block: markdown
    id: resources
    content:
      title: Resources
      text: |
        <div class="resource-copy">
          <p class="resource-copy-lead">
            Individual research equipment is provided as follows:
          </p>
          <ul class="resource-copy-list list-disc pl-6 mt-1 mb-1">
            <li><strong>Graduate Students:</strong> Dedicated workstation comprising a choice of desktop or laptop, complemented by dual monitors.</li>
            <li><strong>Undergraduate Students:</strong> Dual monitor setup provided for individual workspaces.</li>
          </ul>
        </div>
        {{< resource-cards >}}
    design:
      spacing:
        padding: ["4.25rem", 0, "2rem", 0]
      css_class: "bg-white dark:bg-gray-800"

  - block: markdown
    id: contact-info
    content:
      title: Contact Information
      text: |
        {{< contact-info-cards >}}
    design:
      spacing:
        padding: ["2rem", 0, "2rem", 0]

  - block: markdown
    id: location
    content:
      title: Location
      text: |
        <style>
          #location .max-w-prose,
          #location .prose {
            max-width: min(1260px, 96vw) !important;
            width: 100% !important;
          }

          #location .location-map-box {
            width: 100%;
            height: 460px;
            border: 1px solid rgba(59, 130, 246, 0.24);
            border-radius: 0.8rem;
            overflow: hidden;
            background: #e2e8f0;
            box-shadow: 0 12px 28px rgba(15, 23, 42, 0.08);
          }

          .dark #location .location-map-box {
            border-color: rgba(96, 165, 250, 0.34);
            background: #1f2937;
            box-shadow: 0 14px 32px rgba(2, 6, 23, 0.35);
          }
        </style>
        <div class="location-map-box">
          <iframe
            src="https://www.google.com/maps?q=35.70631,128.4540&hl=ko&z=15&output=embed"
            width="100%"
            height="100%"
            style="border:0;"
            allowfullscreen=""
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade">
          </iframe>
        </div>
    design:
      spacing:
        padding: ["2rem", 0, "2rem", 0]
      css_class: "bg-white dark:bg-gray-800"
      container: false

---
