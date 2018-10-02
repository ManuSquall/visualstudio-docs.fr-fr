---
title: Analyse de qualité des applications à l’aide des outils d’analyse de Code | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1b62ac482d18bc8844045d90d32f4d48416daeca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503296"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>Analyse de la qualité des applications à l'aide des outils d'analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [analyser la qualité des applications par les outils d’analyse de Code à l’aide de](https://docs.microsoft.com/visualstudio/code-quality/analyzing-application-quality-by-using-code-analysis-tools).  
  
Dans cette section  
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)  
 L’outil d’analyse de Visual Studio Code fournit des informations sur les assemblys managés, notamment les violations des règles de programmation et de design présentées dans les règles de conception de Microsoft .NET Framework. Les messages d'avertissement identifient les problèmes de programmation et de conception pertinents et, si possible, fournissent des informations relatives à leur résolution.  
  
 [Analyse de la qualité du code C/C++ à l’aide de l’analyse du code](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md)  
 L'outil d'analyse du code C/C++ fournit aux développeurs des informations sur d'éventuelles erreurs présentes dans leur code source C/C++. Les erreurs de codage courantes signalées par l'outil sont les dépassements de mémoire tampon, la mémoire désinitialisée, les déréférencements du pointeur null et les fuites de mémoire et de ressources.  
  
 [Utilisation d’ensembles de règles pour regrouper des règles d’analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)  
 Sélectionnez et créez *ensembles de règles* à appliquer à votre projet.  
  
 [Erreurs d’application d’analyse du code](../code-quality/code-analysis-application-errors.md)  
 Corrigez les erreurs dans les fonctionnalités d'analyse de code.  
  
 [Amélioration de la qualité du code avec les stratégies d’archivage de projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)  
 À l’aide de Team Foundation Version Control (TFVC), vous pouvez créer des stratégies d’archivage pour vos projets d’équipe afin d’appliquer des pratiques permettant d’améliorer le développement de code et d’optimiser le travail en groupe. Les stratégies d'archivage sont des règles établies au niveau du projet d'équipe et appliquées sur les ordinateurs des développeurs avant que le code ne soit autorisé à être archivé.  
  
### <a name="code-analysis-for-drivers"></a>Analyse du code pour les pilotes  
 Les outils d'analyse du code peuvent vous aider à renforcer la stabilité et la fiabilité de votre pilote en analysant systématiquement son code source.  
  
 [Analyse de qualité des pilotes à l’aide des outils d’analyse du Code](http://go.microsoft.com/fwlink/?LinkId=227618)  
 L’analyse du code pour les pilotes est un outil statique de vérification au moment de la compilation qui détecte les erreurs de codage de base dans les programmes C et C++ et inclut un module spécialisé qui est conçu pour détecter les erreurs dans du code de pilote en mode noyau (principalement). Le vérificateur de pilote statique (SDV, Static Driver Verifier) est un outil de vérification statique qui analyse systématiquement le code source des pilotes en mode noyau de Windows. SDV détermine si le pilote interagit correctement avec le noyau du système d'exploitation Windows.  
  
 [Analyse du code pour les avertissements de pilotes](http://go.microsoft.com/fwlink/?LinkId=225920)  
 Décrit les avertissements qu'émet l'analyse du code pour les pilotes quand elle détecte une erreur possible dans le code du pilote.  
  
## <a name="related-tasks"></a>Tâches connexes  
 [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)  
 Insérer une description ici.  
  
 [Tests unitaires sur votre code](../test/unit-test-your-code.md)  
 Insérer une description ici.



