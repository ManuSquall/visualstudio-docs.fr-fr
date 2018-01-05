---
title: "À l’aide de la règle définit pour les règles d’analyse du Code groupe | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.rulesets.learnmore
helpviewer_keywords: code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 51b282cb86ca83ecf2ace1e4b12c8444928b15e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Utilisation d'ensembles de règles pour regrouper des règles d'analyse du code
Lorsque vous configurez l’analyse du code dans [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], ou [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], vous pouvez choisir parmi une liste d’intégrée de Microsoft *ensembles de règles*. Un ensemble de règles est un regroupement logique de règles d’analyse du code qui identifient les problèmes ciblés et des conditions spécifiques. Par exemple, vous pouvez appliquer un ensemble de règles est conçu pour analyser le code des API publiques disponibles, ou vous pouvez appliquer un ensemble de règles qui inclut uniquement les règles minimales recommandées. Vous pouvez également appliquer un ensemble de règles qui inclut toutes les règles.  
  
 Vous pouvez personnaliser un ensemble de règles en ajoutant ou supprimant des règles, ou en modifiant les règles s’affichent dans le **liste d’erreurs** fenêtre en tant qu’avertissements ou erreurs. Ensembles de règles personnalisés peuvent répondre à un besoin pour votre environnement de développement particulier. Lorsque vous personnalisez un ensemble de règles, la page de jeu de règles fournit des outils pour vous aider dans le processus de filtrage et de recherche.  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Effectuer des exercices pratiques :** utilisez les outils d’analyse de code pour spécifier une règle personnalisée définissent pour rechercher et corriger les problèmes dans une application .NET Framework simple.|-   [Procédure pas à pas : Configuration et à l’aide d’un ensemble de règles personnalisé](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**Configurer l’analyse du code pour un projet :** choisir une règle existante définie pour un projet, un site Web ou une solution.|-   [Comment : configurer l’analyse du Code pour un projet de Code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [À l’aide des ensembles de règles pour spécifier les règles C++ à exécuter](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Comment : configurer l’analyse du Code pour une Application Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Comment : spécifier des ensembles de règles pour plusieurs projets dans une Solution](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**Personnaliser un ensemble de règles :** spécifiez des règles à appliquer à votre projet.|-   [Création d’ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**Comprendre les ensembles de règles intégrés :** afficher les règles d’analyse de code qui composent les ensembles de règles intégrés.|-   [Règle d’analyse du code définie la référence](../code-quality/code-analysis-rule-set-reference.md)|  
|**Intégrer l’analyse du code avec Team Foundation Server :** [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] archiver les stratégies permettent aux équipes de développement pour vous assurer que tous les archivages de code répondent à un ensemble commun de normes d’analyse de code.|-   [Comment : synchroniser des ensembles de règles de projet de Code avec la stratégie d’archivage du projet d’équipe](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|