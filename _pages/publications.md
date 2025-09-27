---
layout: page
title: publications
permalink: /publications/
nav: true
nav_order: 4
---

<div class="publications">
  <div class="publications-header">
    <h1>Publications</h1>
    <p class="publications-subtitle">Research contributions in computer vision, machine learning, and 4D perception</p>
  </div>
  
  {% bibliography --group_by year --group_order descending %}
</div>

<style>
.publications-header {
  text-align: center;
  margin-bottom: 3rem;
  padding-bottom: 2rem;
  border-bottom: 2px solid var(--global-divider-color);
}

.publications-header h1 {
  color: var(--global-theme-color);
  font-size: 2.5rem;
  margin-bottom: 1rem;
  font-weight: 700;
}

.publications-subtitle {
  color: var(--global-text-color-light);
  font-size: 1.1rem;
  margin: 0;
}

.publications {
  .bibliography {
    li {
      background: var(--global-card-bg-color);
      border-radius: 12px;
      padding: 1.5rem;
      margin-bottom: 2rem;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      transition: all 0.3s ease;
      border: 1px solid var(--global-divider-color);
      
      &:hover {
        transform: translateY(-2px);
        box-shadow: 0 4px 16px rgba(0,0,0,0.15);
      }
      
      .title {
        font-size: 1.2rem;
        font-weight: 600;
        margin-bottom: 0.8rem;
        line-height: 1.4;
        
        a {
          color: var(--global-text-color);
          text-decoration: none;
          
          &:hover {
            color: var(--global-theme-color);
          }
        }
      }
      
      .author {
        margin-bottom: 1rem;
        font-size: 0.95rem;
        line-height: 1.5;
        
        a {
          color: var(--global-theme-color);
          text-decoration: none;
          border-bottom: 1px dashed var(--global-theme-color);
          
          &:hover {
            border-bottom-style: solid;
          }
        }
      }
      
      .links {
        margin-top: 1rem;
        padding-top: 1rem;
        border-top: 1px solid var(--global-divider-color);
        
        a {
          display: inline-block;
          margin-right: 1rem;
          margin-bottom: 0.5rem;
          padding: 0.4rem 0.8rem;
          background: var(--global-theme-color);
          color: white;
          text-decoration: none;
          border-radius: 6px;
          font-size: 0.85rem;
          font-weight: 500;
          transition: all 0.2s ease;
          
          &:hover {
            background: var(--global-hover-color);
            transform: translateY(-1px);
          }
        }
      }
      
      .abstract {
        margin-top: 1rem;
        padding: 1rem;
        background: var(--global-bg-color);
        border-radius: 8px;
        border-left: 4px solid var(--global-theme-color);
        font-size: 0.9rem;
        line-height: 1.6;
        color: var(--global-text-color-light);
      }
      
      .bibtex {
        margin-top: 1rem;
        padding: 1rem;
        background: var(--global-code-bg-color);
        border-radius: 8px;
        font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
        font-size: 0.8rem;
        line-height: 1.4;
        overflow-x: auto;
        border: 1px solid var(--global-divider-color);
        
        .copy-btn {
          float: right;
          background: var(--global-theme-color);
          color: white;
          border: none;
          padding: 0.3rem 0.6rem;
          border-radius: 4px;
          font-size: 0.7rem;
          cursor: pointer;
          transition: background 0.2s ease;
          
          &:hover {
            background: var(--global-hover-color);
          }
        }
      }
    }
  }
  
  h2 {
    color: var(--global-theme-color);
    font-size: 1.8rem;
    margin-top: 3rem;
    margin-bottom: 1.5rem;
    padding-bottom: 0.5rem;
    border-bottom: 2px solid var(--global-theme-color);
    display: inline-block;
  }
}
</style>

<script>
document.addEventListener('DOMContentLoaded', function() {
  // Add copy functionality for BibTeX
  const bibtexBlocks = document.querySelectorAll('.bibtex');
  bibtexBlocks.forEach(block => {
    const copyBtn = document.createElement('button');
    copyBtn.className = 'copy-btn';
    copyBtn.textContent = 'Copy';
    copyBtn.onclick = function() {
      const text = block.textContent.replace('Copy', '').trim();
      navigator.clipboard.writeText(text).then(() => {
        copyBtn.textContent = 'Copied!';
        setTimeout(() => {
          copyBtn.textContent = 'Copy';
        }, 2000);
      });
    };
    block.appendChild(copyBtn);
  });
  
  // Add expand/collapse for abstracts
  const abstracts = document.querySelectorAll('.abstract');
  abstracts.forEach(abstract => {
    if (abstract.textContent.length > 200) {
      const shortText = abstract.textContent.substring(0, 200) + '...';
      const fullText = abstract.textContent;
      
      abstract.innerHTML = `
        <span class="abstract-short">${shortText}</span>
        <span class="abstract-full" style="display: none;">${fullText}</span>
        <button class="expand-btn" style="background: none; border: none; color: var(--global-theme-color); cursor: pointer; font-size: 0.8rem; margin-top: 0.5rem;">Show more</button>
      `;
      
      const expandBtn = abstract.querySelector('.expand-btn');
      const shortSpan = abstract.querySelector('.abstract-short');
      const fullSpan = abstract.querySelector('.abstract-full');
      
      expandBtn.onclick = function() {
        if (fullSpan.style.display === 'none') {
          fullSpan.style.display = 'inline';
          shortSpan.style.display = 'none';
          expandBtn.textContent = 'Show less';
        } else {
          fullSpan.style.display = 'none';
          shortSpan.style.display = 'inline';
          expandBtn.textContent = 'Show more';
        }
      };
    }
  });
});
</script>
