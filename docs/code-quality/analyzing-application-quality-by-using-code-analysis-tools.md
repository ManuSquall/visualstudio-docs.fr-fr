---
title: "Analyse de la qualit&#233; des applications &#224; l&#39;aide des outils d&#39;analyse du code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.analysisresults"
helpviewer_keywords: 
  - "qualité des applications, analyser"
  - "analyse du code"
  - "développement basé sur l'équipe, analyser la qualité des applications"
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# Analyse de la qualit&#233; des applications &#224; l&#39;aide des outils d&#39;analyse du code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Dans cette section  
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)  
 L'outil d'analyse du code managé Visual Studio fournit des informations sur les assemblys managés, notamment les violations des règles de programmation et de design présentées dans les règles de conception de Microsoft .NET Framework.  Les messages d'avertissement identifient les problèmes de programmation et de conception pertinents et, si possible, fournissent des informations relatives à leur résolution.  
  
 [Analyse de la qualité du code C\/C\+\+](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md)  
 L'outil d'analyse du code C\/C\+\+ fournit aux développeurs des informations sur d'éventuelles erreurs présentes dans leur code source C\/C\+\+.  Les erreurs de codage courantes signalées par l'outil sont les dépassements de mémoire tampon, la mémoire désinitialisée, les déréférencements du pointeur null et les fuites de mémoire et de ressources.  
  
 [Utilisation d'ensembles de règles pour regrouper des règles d'analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)  
 Sélectionnez et créez des *ensembles de règles* à appliquer à votre projet.  
  
 [Erreurs d’application d’analyse du code](../code-quality/code-analysis-application-errors.md)  
 Corrigez les erreurs dans les fonctionnalités d'analyse de code.  
  
 [Amélioration de la qualité du code avec des stratégies d’archivage de projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)  
 À l'aide du contrôle de version Team Foundation, vous pouvez créer des stratégies d'archivage pour vos projets d'équipe afin d'appliquer des pratiques permettant d'améliorer le développement de code et d'optimiser le travail en groupe.  Les stratégies d'archivage sont des règles établies au niveau du projet d'équipe et appliquées sur les ordinateurs des développeurs avant que le code ne soit autorisé à être archivé.  
  
### Analyse du code pour les pilotes  
 Les outils d'analyse du code peuvent vous aider à renforcer la stabilité et la fiabilité de votre pilote en analysant systématiquement son code source.  
  
 [Analyse de la qualité des pilotes à l'aide des outils d'analyse du code](http://go.microsoft.com/fwlink/?LinkId=227618)  
 L'analyse du code pour les pilotes est un outil statique de vérification au moment de la compilation qui détecte les erreurs de codage de base dans les programmes C et C\+\+ et inclut un module spécialisé qui est conçu pour détecter les erreurs dans du code de pilote en mode noyau \(principalement\).  Le vérificateur de pilote statique \(SDV, Static Driver Verifier\) est un outil de vérification statique qui analyse systématiquement le code source des pilotes en mode noyau de Windows.  SDV détermine si le pilote interagit correctement avec le noyau du système d'exploitation Windows.  
  
 [Avertissements de l'analyse du code pour les pilotes](http://go.microsoft.com/fwlink/?LinkId=225920)  
 Décrit les avertissements qu'émet l'analyse du code pour les pilotes quand elle détecte une erreur possible dans le code du pilote.  
  
## Tâches connexes  
 [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)  
 Insérer une description ici.  
  
 [Tests unitaires sur votre code](../test/unit-test-your-code.md)  
 Insérer une description ici.