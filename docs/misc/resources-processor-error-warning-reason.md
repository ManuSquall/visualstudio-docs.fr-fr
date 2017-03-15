---
title: "Resources processor error/warning: &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.resx_generator_task"
ms.assetid: eb9a1bd0-7e63-4a2b-ad37-54f6e67d9b5a
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resources processor error/warning: &lt;reason&gt;
Un message d'erreur ou d'avertissement s'affiche si un outil retourne une erreur ou un avertissement pendant le traitement d'un fichier .resx.  Dans le cadre du processus de génération, le système de projet transforme chaque fichier .resx en fichier binaire que le gestionnaire de ressources [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] comprend.  Cette transformation est réalisée à l'aide d'outils in\-process.  
  
 La cause la plus probable de cette erreur ou de cet avertissement est un fichier .resx incorrect.  Un fichier .resx peut être endommagé s'il est modifié à l'extérieur de Visual Studio ou dans Visual Studio mais avec un éditeur de texte.  
  
 Ces fichiers sont normalement managés par les concepteurs Windows Forms et Web Forms.  
  
### Pour corriger cette erreur  
  
1.  Corrigez le format du fichier .resx.  
  
     Une erreur signifie que le fichier binaire n'a pas été généré et que le processus de génération va échouer.  Un avertissement est fourni à titre d'information uniquement.  
  
## Voir aussi  
 [Resources in .Resx File Format](http://msdn.microsoft.com/fr-fr/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)