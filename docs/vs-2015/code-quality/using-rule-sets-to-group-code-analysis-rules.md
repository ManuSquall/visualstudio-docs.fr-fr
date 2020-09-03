---
title: Utilisation d’ensembles de règles pour regrouper des règles d’analyse du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30bd2e53531d9abc7d27adba05c3b724c88d61c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603483"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Utilisation d'ensembles de règles pour regrouper des règles d'analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quand vous configurez l’analyse du code dans [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] , [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] ou [!INCLUDE[vsPro](../includes/vspro-md.md)] , vous pouvez choisir parmi une liste d' *ensembles de règles*intégrés Microsoft. Un ensemble de règles est un regroupement logique de règles d’analyse du code qui identifient des problèmes ciblés et des conditions spécifiques. Par exemple, vous pouvez appliquer un ensemble de règles conçu pour analyser le code pour les API disponibles publiquement, ou vous pouvez appliquer un ensemble de règles qui comprend uniquement les règles minimales recommandées. Vous pouvez également appliquer un ensemble de règles qui comprend toutes les règles.

 Vous pouvez personnaliser un ensemble de règles en ajoutant ou en supprimant des règles, ou en modifiant les règles pour qu’elles s’affichent dans la fenêtre **liste d’erreurs** sous la forme d’avertissements ou d’erreurs. Les ensembles de règles personnalisés peuvent satisfaire un besoin pour votre environnement de développement particulier. Lorsque vous personnalisez un ensemble de règles, la page ensemble de règles fournit des outils de recherche et de filtrage pour vous aider dans le processus.

## <a name="common-tasks"></a>Tâches courantes

|Tâche|Contenu associé|
|----------|---------------------|
|**Faire des exercices pratiques :** Utilisez les outils d’analyse du code pour spécifier un ensemble de règles personnalisé pour rechercher et résoudre les problèmes dans une application .NET Framework simple.|-   [Procédure pas à pas : configuration et utilisation d’un ensemble de règles personnalisé](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**Configurer l’analyse du code pour un projet :** Choisissez un ensemble de règles existant pour un projet, un site Web ou une solution.|-   [Comment : configurer l’analyse du code pour un projet de code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [Utilisation d’ensembles de règles pour spécifier les règles C++ à exécuter](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Comment : configurer l’analyse du code pour une application Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Procédure : spécifier des ensembles de règles pour plusieurs projets dans une solution](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**Personnaliser un ensemble de règles :** Spécifiez les règles à appliquer à votre projet.|-   [Création d’ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**Comprendre les ensembles de règles intégrés :** Affichez les règles d’analyse du code qui composent les ensembles de règles intégrés.|-   [Référence de l’ensemble de règles d’analyse du code](../code-quality/code-analysis-rule-set-reference.md)|
|**Intégrer l’analyse du code avec Team Foundation Server :** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] les stratégies d’archivage permettent aux équipes de développement de s’assurer que tous les archivages de code sont conformes à un ensemble commun de normes d’analyse du code.|-   [Comment : synchroniser des ensembles de règles de projet de code avec la stratégie d’archivage de projet d’équipe](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|
