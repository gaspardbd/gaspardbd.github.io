---
layout: page
title: publications
permalink: /publications/
nav: true
nav_order: 4
---

<div class="publications">
  {% bibliography --group_by year --group_order descending %}
</div>

<style>
.publications {
  margin-top: 0.5rem;
}

.publications .bibliography,
.publications .bibliography ul,
.publications .bibliography ol {
  list-style: none;
  padding-left: 0;
  margin-left: 0;
  counter-reset: none;
}

.publications .bibliography li {
  margin-bottom: 1.8rem;
  padding-bottom: 1.4rem;
  border-bottom: 1px solid var(--global-divider-color);
}

.publications .bibliography .title {
  font-size: 1.1rem;
  font-weight: 600;
  line-height: 1.4;
  margin-bottom: 0.6rem;
}
.publications .bibliography .title a {
  color: var(--global-text-color);
  text-decoration: none;
}
.publications .bibliography .title a:hover {
  color: var(--global-theme-color);
  text-decoration: underline;
}

.publications .bibliography .author {
  margin: 0.25rem 0 0.85rem 0;
  font-size: 0.95rem;
  line-height: 1.5;
}
.publications .bibliography .author a {
  color: var(--global-theme-color);
  border-bottom: none !important;
  text-decoration: none;
}
.publications .bibliography .author a:hover {
  text-decoration: underline;
}
.publications .bibliography .author > em {
  border-bottom: 1px solid currentColor;
  font-style: normal;
}

.publications .bibliography .periodical {
  margin-bottom: 0.2rem;
  line-height: 1.45;
}

.publications .bibliography .links {
  margin-top: 0.75rem;
}
.publications .bibliography .links a.btn {
  display: inline-block;
  margin-right: 0.6rem;
  margin-bottom: 0.5rem;
  padding: 0.35rem 0.7rem;
  background: var(--global-theme-color) !important;
  border: 1px solid var(--global-theme-color) !important;
  color: #fff !important;
  text-decoration: none;
  font-size: 0.82rem;
  font-weight: 500;
  border-radius: 6px;
  transition: opacity 0.2s ease;
}
.publications .bibliography .links a.btn:hover {
  opacity: 0.9;
}

.publications .bibliography div.abstract.hidden {
  margin: 0;
  padding: 0;
  max-height: 0;
  overflow: hidden;
  border: 0;
  opacity: 0;
  text-align: left;
}

.publications .bibliography div.abstract.hidden.open {
  margin-top: 0.8rem;
  padding: 0.9rem 1rem;
  max-height: 40rem;
  overflow: auto;
  opacity: 1;
  background: var(--global-bg-color);
  border: 1px solid var(--global-divider-color);
  border-left: 4px solid var(--global-theme-color);
  border-radius: 6px;
  font-size: 0.92rem;
  line-height: 1.6;
  color: var(--global-text-color-light);
}

.publications .bibliography div.abstract.hidden p {
  margin: 0;
  line-height: 1.6;
}

.publications .bibliography .bibtex,
.publications .bibliography details.bibtex,
.publications .bibliography pre.bibtex {
  position: relative;
  margin-top: 0.8rem;
  padding: 1rem;
  background: var(--global-code-bg-color);
  border: 1px solid var(--global-divider-color);
  overflow-x: auto;
  font-family: "Monaco","Menlo","Ubuntu Mono",monospace;
  font-size: 0.85rem;
  line-height: 1.4;
}

.publications .copy-btn {
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  background: var(--global-theme-color);
  color: #fff;
  border: none;
  padding: 0.35rem 0.6rem;
  font-size: 0.75rem;
  border-radius: 0.3rem;
  cursor: pointer;
}
.publications .copy-btn:hover {
  opacity: 0.9;
}

.publications h2 {
  color: var(--global-theme-color);
  font-size: 1.6rem;
  margin-top: 2.2rem;
  margin-bottom: 1rem;
  padding-bottom: 0.4rem;
  border-bottom: 2px solid var(--global-theme-color);
  display: inline-block;
}

.publications .bibliography li::marker { content: ""; }
</style>
