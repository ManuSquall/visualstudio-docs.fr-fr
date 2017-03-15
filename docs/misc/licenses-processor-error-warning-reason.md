---
title: "Licenses processor error/warning: &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.licx_generator_task"
ms.assetid: 85750198-7bd3-4936-b1eb-954dcc3ff573
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Licenses processor error/warning: &lt;reason&gt;
Un message d'erreur ou d'avertissement s'affiche si un outil retourne une erreur ou un avertissement pendant le traitement d'un fichier .licx.  Dans le cadre du processus de génération, le système de projet transforme le fichier Licenses.licx \(s'il est présent\) en fichier binaire que le gestionnaire de licences [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] comprend.  Cette transformation est réalisée à l'aide d'outils in\-process.  
  
 La cause la plus probable de cette erreur ou de cet avertissement est un fichier .licx incorrect.  Un fichier .licx peut être endommagé s'il est modifié à l'extérieur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mais avec un éditeur de texte.  
  
 Ces fichiers sont normalement managés par les concepteurs Windows Forms et Web Forms.  
  
### Pour corriger cette erreur  
  
1.  Corrigez le format du fichier .licx.  
  
     Une erreur signifie que le fichier binaire n'a pas été généré et que le processus de génération va échouer.  Un avertissement est fourni à titre d'information uniquement.  
  
## Voir aussi  
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/fr-fr/f793852c-da06-4d52-a826-65f635844772)