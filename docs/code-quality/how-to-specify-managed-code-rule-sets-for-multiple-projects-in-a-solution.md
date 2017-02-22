---
title: "Comment&#160;: sp&#233;cifier des ensembles de r&#232;gles applicables au code manag&#233; pour plusieurs projets dans une solution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.solution"
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: sp&#233;cifier des ensembles de r&#232;gles applicables au code manag&#233; pour plusieurs projets dans une solution
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Par défaut, tous les projets gérés d'une solution se voient assigner *ensemble de règles* d'analyse du code appelé Règles Microsoft minimales recommandées.  Vous pouvez modifier les ensembles de règles assignés aux projets d'une solution dans la boîte de dialogue des propriétés de la solution.  
  
> [!NOTE]
>  Par défaut, l'analyse du code du projet n'est pas exécutée en tant qu'étape de génération.  Pour autoriser l'analyse du code en tant qu'étape de génération, consultez [Procédure : configurer l’analyse du code pour un projet de code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### Pour spécifier un ensemble de règles pour plusieurs projets dans une solution comportant du code managé  
  
1.  Dans le [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], ou [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] ouvre la solution.  
  
2.  Dans le menu **Analyser**, cliquez sur **Configurer l'analyse du code pour la solution**.  
  
3.  Si nécessaire, développez **Propriétés communes**, puis cliquez sur **Paramètres d'analyse du code**.  
  
4.  Vous pouvez spécifier un ensemble de règles pour un ou plusieurs projets.  
  
    -   Pour spécifier un ensemble de règles pour un projet individuel, cliquez sur le nom du projet.  
  
    -   Pour spécifier un ensemble de règles pour plusieurs projets, maintenez la touche CTRL enfoncée et cliquez sur les noms de projet.  
  
    -   Pour spécifier tous les projets de la solution, maintenez la touche MAJ enfoncée et cliquez dans la liste des projets.  
  
5.  Cliquez sur le champ **Ensemble de règles** d'un projet, puis sur le nom de l'ensemble de règles que vous souhaitez appliquer.