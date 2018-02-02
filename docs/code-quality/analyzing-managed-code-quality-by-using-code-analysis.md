---
title: "Analyse de la qualité du Code managé à l’aide de l’analyse du Code | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 2008ac649302d87cc2d45274de3fdb1981aa571d
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2018
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analyse de la qualité d’un code managé à l’aide de l’analyse du code
Vous pouvez utiliser les outils d’analyse de code dans Visual Studio pour découvrir d’éventuels problèmes dans votre code, telles que l’accès aux données non sécurisés, les violations d’utilisation et les problèmes de conception. Analyse du code fonctionne sur les applications de base de données .NET Framework et natives (C et C++). Analyse du code pour le code managé organise des règles dans *ensembles de règles* qui ciblent les problèmes d’encodage.  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâches courantes|Contenu de support|  
|------------------|------------------------|  
|**Effectuer des exercices pratiques :** apprendre les principes fondamentaux de l’analyse du code, corrigez les erreurs dans une application .NET Framework simple.|-   [Procédure pas à pas : Analyse du Code managé pour les erreurs de Code](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Configurer l’analyse du code pour un projet :** règles managé code sont organisées en ensembles de règles qui ciblent des zones spécifiques, telles que la sécurité et de conception. Vous pouvez utiliser une des Microsoft standard définit ou créer les vôtres.|-   [Analyse du code pour une vue d’ensemble du Code managé](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [À l’aide de la règle définit aux règles d’analyse de Code de groupe](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Supprimer les avertissements à l’aide de l’attribut SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Exécuter l’analyse du code :** vous pouvez spécifier l’analyse du code soit exécutée automatiquement chaque fois qu’une configuration de projet est générée, et vous pouvez exécuter manuellement l’analyse du code sur un projet.|-   [Comment : activer et désactiver l’analyse du Code automatique](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Comment : exécuter l’analyse du Code manuellement](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analyser les résultats d’analyse de code :** erreurs et avertissements d’analyse du Code sont répertoriées dans la fenêtre analyse du Code. Vous pouvez choisir un avertissement ou une erreur de titre pour afficher des informations supplémentaires sur l’avertissement et pour afficher et mettre en surbrillance la ligne de code source qui a déclenché la règle. Vous pouvez choisir l’id d’avertissement pour afficher des informations détaillées dans la bibliothèque MSDN qui inclut des informations et des exemples montrant comment résoudre le problème.|-   [Comment : afficher les défauts du Code managé](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Analyse du code pour les avertissements de Code managé](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Avertissements par CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Méthodes anonymes et analyse du Code](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Intégrer l’analyse du code de votre cycle de vie de développement :** stratégies d’archivage dans [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] activer les équipes de développement pour vous assurer que tous les archivages du code répondent à un ensemble commun de normes d’analyse de code. Création d’un élément de travail pour une violation de règle d’analyse code est une procédure simple que vous pouvez effectuer dans la fenêtre liste d’erreurs.|-   [Amélioration de la qualité du Code avec les stratégies d’archivage du projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Comment : synchroniser des ensembles de règles de projet de Code avec la stratégie d’archivage du projet d’équipe](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Comment : créer un élément de travail pour une erreur de Code managé](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|