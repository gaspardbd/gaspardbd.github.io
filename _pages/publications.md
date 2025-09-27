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
/* Conteneur principal */
.publications {
  margin-top: 0.5rem;
}

/* Enlever toute numérotation ou puces */
.publications .bibliography,
.publications .bibliography ul,
.publications .bibliography ol {
  list-style: none;
  padding-left: 0;
  margin-left: 0;
  counter-reset: none;
}

/* Chaque entrée bibliographique */
.publications .bibliography li {
  margin-bottom: 1.5rem;
  padding-bottom: 1.25rem;
  border-bottom: 1px solid var(--global-divider-color);
}

/* Titre de la publication */
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

 /* Auteurs complets, visibles immédiatement */
 .publications .bibliography .author {
   margin: 0.2rem 0 0.8rem 0;
   font-size: 0.95rem;
   line-height: 1.5;
 }
 .publications .bibliography .author a {
   color: var(--global-theme-color);
   text-decoration: none;
 }
 .publications .bibliography .author a:hover {
   text-decoration: underline;
 }
 
 /* Supprimer "and" entre les auteurs */
 .publications .bibliography .author .and {
   display: none;
 }

/* Zone des liens (pdf, code, arXiv, etc.) */
.publications .bibliography .links {
  margin-top: 0.75rem;
}
.publications .bibliography .links a {
  display: inline-block;
  margin-right: 0.6rem;
  margin-bottom: 0.5rem;
  padding: 0.35rem 0.7rem;
  background: var(--global-theme-color);
  color: #fff;
  text-decoration: none;
  font-size: 0.82rem;
  font-weight: 500;
  border-radius: 0.35rem;
  transition: opacity 0.2s ease;
}
.publications .bibliography .links a:hover {
  opacity: 0.9;
}

 /* Abstract affiché en entier, bloc propre */
 .publications .bibliography .abstract,
 .publications .bibliography details.abstract,
 .publications .bibliography .entry .abstract {
   margin-top: 0.8rem;
   padding: 0.9rem 1rem;
   background: var(--global-bg-color);
   border-left: 4px solid var(--global-theme-color);
   font-size: 0.92rem;
   line-height: 1.6;
   color: var(--global-text-color-light);
 }
 
 /* Supprimer les boutons ABS */
 .publications .bibliography .abbr,
 .publications .bibliography .abbr abbr {
   display: none !important;
 }

/* Bloc BibTeX + bouton Copy */
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

/* Bouton Copy */
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

/* En-têtes d’année propres */
.publications h2 {
  color: var(--global-theme-color);
  font-size: 1.6rem;
  margin-top: 2.2rem;
  margin-bottom: 1rem;
  padding-bottom: 0.4rem;
  border-bottom: 2px solid var(--global-theme-color);
  display: inline-block;
}

/* Supprimer styles de numérotation spécifiques éventuels du thème */
.publications .bibliography li::marker { content: ""; }
</style>

<script>
document.addEventListener('DOMContentLoaded', function () {
   /* 1) Auteurs complets: si le thème cache des auteurs dans des spans,
         on les force visibles et on supprime un éventuel bouton "more" */
   document.querySelectorAll('.bibliography .author').forEach(function (el) {
     el.querySelectorAll('.hidden, [style*="display: none"]').forEach(function (h) {
       h.style.display = 'inline';
     });
     el.querySelectorAll('.more-authors, .more-authors-btn, .toggle-authors').forEach(function (btn) {
       btn.remove();
     });
     // Supprimer les éléments "and" entre les auteurs
     el.querySelectorAll('.and').forEach(function (andEl) {
       andEl.remove();
     });
   });

  /* 2) Abstract toujours visible:
        certains thèmes enveloppent l'abstract dans <details class="abstract"> */
  document.querySelectorAll('.bibliography details.abstract').forEach(function (det) {
    det.open = true; // au cas où
    const contentNodes = Array.from(det.childNodes).filter(n => n.tagName !== 'SUMMARY');
    const wrapper = document.createElement('div');
    wrapper.className = 'abstract';
    contentNodes.forEach(n => wrapper.appendChild(n));
    det.replaceWith(wrapper);
  });
  
  /* 3) Supprimer tous les boutons ABS */
  document.querySelectorAll('.bibliography .abbr, .bibliography .abbr abbr').forEach(function (el) {
    el.remove();
  });

  /* 3) BibTeX toujours visible et bouton Copy:
        si le BibTeX est dans <details class="bibtex">, on l’ouvre et on remplace par un bloc direct */
  document.querySelectorAll('.bibliography details.bibtex').forEach(function (det) {
    det.open = true;
    // Récupérer tout sauf le <summary>
    const contentNodes = Array.from(det.childNodes).filter(n => n.tagName !== 'SUMMARY');
    const box = document.createElement('div');
    box.className = 'bibtex';
    contentNodes.forEach(n => box.appendChild(n));
    det.replaceWith(box);
  });

  /* 4) Ajouter un bouton Copy sur chaque bloc BibTeX */
  function addCopyButtonTo(node) {
    // éviter doublons
    if (node.querySelector('.copy-btn')) return;
    const btn = document.createElement('button');
    btn.className = 'copy-btn';
    btn.textContent = 'Copy';
    btn.addEventListener('click', function () {
      // texte sans le bouton
      const clone = node.cloneNode(true);
      clone.querySelectorAll('.copy-btn').forEach(b => b.remove());
      const text = clone.textContent.trim();
      navigator.clipboard.writeText(text).then(() => {
        const old = btn.textContent;
        btn.textContent = 'Copied!';
        setTimeout(() => { btn.textContent = old; }, 1600);
      });
    });
    node.appendChild(btn);
  }

  // Cas 1: blocs avec classe .bibtex
  document.querySelectorAll('.bibliography .bibtex').forEach(addCopyButtonTo);

  // Cas 2: <pre class="bibtex"> ou <pre><code class="language-bibtex">
  document.querySelectorAll('.bibliography pre.bibtex, .bibliography pre code.language-bibtex').forEach(function (node) {
    const host = node.closest('pre') || node.parentElement;
    host.classList.add('bibtex');
    addCopyButtonTo(host);
  });
});
</script>
