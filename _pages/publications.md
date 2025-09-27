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
      margin-bottom: 2rem;
      padding-bottom: 1.5rem;
      border-bottom: 1px solid var(--global-divider-color);
      
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
          
          &:hover {
            text-decoration: underline;
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
          font-size: 0.85rem;
          font-weight: 500;
          transition: all 0.2s ease;
          
          &:hover {
            background: var(--global-hover-color);
          }
        }
      }
      
      .abstract {
        margin-top: 1rem;
        padding: 1rem;
        background: var(--global-bg-color);
        border-left: 4px solid var(--global-theme-color);
        font-size: 0.9rem;
        line-height: 1.6;
        color: var(--global-text-color-light);
      }
      
      .bibtex {
        margin-top: 1rem;
        padding: 1rem;
        background: var(--global-code-bg-color);
        font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
        font-size: 0.8rem;
        line-height: 1.4;
        overflow-x: auto;
        border: 1px solid var(--global-divider-color);
        position: relative;
        
        .copy-btn {
          position: absolute;
          top: 0.5rem;
          right: 0.5rem;
          background: var(--global-theme-color);
          color: white;
          border: none;
          padding: 0.3rem 0.6rem;
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
});
</script>
