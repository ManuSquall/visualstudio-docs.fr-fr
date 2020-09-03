---
title: Analyse de la qualité des applications à l’aide des outils d’analyse du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f8ec0706530cd61653d44533654cf453d25eb42e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919069"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>Analyse de la qualité des applications à l'aide des outils d'analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette section, analyse de la [qualité du code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) l’analyse du code Visual Studio pour le code managé fournit des informations sur les assemblys managés, notamment les violations des règles de programmation et de conception énoncées dans les règles de conception du Microsoft .NET Framework. Les messages d'avertissement identifient les problèmes de programmation et de conception pertinents et, si possible, fournissent des informations relatives à leur résolution.

 Analyse [de la qualité du code C/C++ à l’aide de l’analyse du code](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md) L’outil d’analyse du code C/C++ fournit aux développeurs des informations sur les erreurs possibles dans leur code source C/C++. Les erreurs de codage courantes signalées par l'outil sont les dépassements de mémoire tampon, la mémoire désinitialisée, les déréférencements du pointeur null et les fuites de mémoire et de ressources.

 [Utilisation d’ensembles de règles pour regrouper des règles d’analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) Sélectionnez et créez des *ensembles de règles* à appliquer à votre projet.

 [Erreurs d’application d’analyse du code](../code-quality/code-analysis-application-errors.md) Corrigez les erreurs dans la fonctionnalité d’analyse du code.

 [Amélioration de la qualité du code avec les stratégies d’archivage de projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md) Quand vous utilisez Team Foundation Version Control (TFVC), vous pouvez créer des stratégies d’archivage pour vos projets d’équipe qui appliquent des pratiques qui conduisent à un meilleur code et un développement de groupe plus efficace. Les stratégies d’archivage sont des règles établies au niveau du projet d’équipe et appliquées sur les ordinateurs des développeurs avant que le code ne soit autorisé à être archivé.

### <a name="code-analysis-for-drivers"></a>Analyse du code pour les pilotes
 Les outils d'analyse du code peuvent vous aider à renforcer la stabilité et la fiabilité de votre pilote en analysant systématiquement son code source.

 [Analyse de la qualité du pilote à l’aide des outils d’analyse du code](/windows-hardware/drivers/devtest/tools-for-verifying-drivers) L’analyse du code pour les pilotes est un outil de vérification statique au moment de la compilation qui détecte les erreurs de codage de base dans les programmes C et C++ et comprend un module spécialisé conçu pour détecter les erreurs dans le code du pilote en mode noyau (principalement). Le vérificateur de pilote statique (SDV, Static Driver Verifier) est un outil de vérification statique qui analyse systématiquement le code source des pilotes en mode noyau de Windows. SDV détermine si le pilote interagit correctement avec le noyau du système d'exploitation Windows.

 [Avertissements de l’analyse du code pour les pilotes](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings) Décrit les avertissements signalés par l’analyse du code pour les pilotes lorsqu’il détecte une erreur possible dans le code du pilote.

## <a name="related-tasks"></a>Tâches associées
 [Mesure de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) Insérez la description ici.

 [Test unitaire de votre code](../test/unit-test-your-code.md) Insérez la description ici.
