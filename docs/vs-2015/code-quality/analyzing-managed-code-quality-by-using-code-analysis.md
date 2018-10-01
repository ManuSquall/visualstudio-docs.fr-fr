---
title: Analyse de la qualité du Code managé à l’aide de l’analyse du Code | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3e0538c47dec2dd11b9488a80dd4f71baddc487f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493607"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analyse de la qualité d’un code managé à l’aide de l’analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [analyser la qualité du Code géré par l’analyse du Code à l’aide de](https://docs.microsoft.com/visualstudio/code-quality/analyzing-managed-code-quality-by-using-code-analysis).  
  
Vous pouvez utiliser les outils d’analyse de code dans Visual Studio pour découvrir d’éventuels problèmes dans votre code, telles que l’accès aux données non sécurisé, les violations de l’utilisation et les problèmes de conception. Analyse du code fonctionne sur .NET Framework, natif (C et C++) et les applications de base de données. Analyse du code pour le code managé organise des règles dans *ensembles de règles* qui ciblent les problèmes d’encodage.  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâches courantes|Contenu de support|  
|------------------|------------------------|  
|**Effectuer des exercices pratiques :** Découvrez les principes fondamentaux de l’analyse du code par la correction des défauts dans une simple application .NET Framework.|-   [Procédure pas à pas : Analyse du Code managé pour les erreurs de Code](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Configurer l’analyse du code pour un projet :** des règles pour managed code sont organisées en ensembles de règles qui ciblent des zones spécifiques, telles que la sécurité et de conception. Vous pouvez utiliser une de Microsoft standard règle définit ou créer les vôtres.|-   [Analyse du code pour une vue d’ensemble du Code managé](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [À l’aide de la règle définit pour les règles d’analyse de Code de groupe](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Supprimer les avertissements à l’aide de l’attribut SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Exécuter l’analyse du code :** vous pouvez spécifier l’analyse du code à exécuter automatiquement chaque fois qu’une configuration de projet est générée, et vous pouvez exécuter manuellement l’analyse du code sur un projet.|-   [Comment : activer et désactiver l’analyse du Code automatique](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Comment : exécuter l’analyse du Code manuellement](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analyser les résultats d’analyse de code :** avertissements d’analyse du Code et les erreurs sont répertoriées dans la fenêtre analyse du Code. Vous pouvez choisir un avertissement ou un titre de l’erreur pour afficher des informations supplémentaires sur l’avertissement et pour afficher et mettre en surbrillance la ligne de code source qui a déclenché la règle. Vous pouvez choisir l’id d’avertissement pour afficher des informations détaillées dans la bibliothèque MSDN qui inclut des informations et des exemples montrant comment résoudre le problème.|-   [Comment : afficher les défauts du Code managé](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Analyse du code pour les avertissements de Code managé](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Avertissements par CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Méthodes anonymes et analyse du Code](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Intégrer l’analyse du code à votre cycle de vie de développement :** stratégies d’archivage dans [!INCLUDE[esprscc](../includes/esprscc-md.md)] activer les équipes de développement pour vous assurer que tous les archivages du code répondent à un ensemble commun de normes d’analyse de code. Création d’un élément de travail pour une violation de règle d’analyse code est une procédure simple que vous pouvez effectuer dans la fenêtre liste d’erreurs.|-   [Améliorer la qualité du Code avec les stratégies d’archivage du projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Comment : synchroniser des ensembles de règles de projet de Code avec la stratégie d’archivage du projet d’équipe](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Comment : créer un élément de travail pour une erreur de Code managé](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|



