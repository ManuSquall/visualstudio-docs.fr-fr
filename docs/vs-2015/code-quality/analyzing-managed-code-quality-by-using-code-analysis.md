---
title: Analyse de la qualité du code managé à l’aide de l’analyse du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d5f0646f26226e9895414db512681e0a7a71faa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671117"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analyse de la qualité d’un code managé à l’aide de l’analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser les outils d’analyse du code de Visual Studio pour détecter les problèmes potentiels dans votre code, tels que l’accès aux données non sécurisé, les violations d’utilisation et les problèmes de conception. L’analyse du code fonctionne sur .NET Framework, les applications natives (C et C++) et les applications de base de données. L’analyse du code managé organise les règles dans des *ensembles de règles* ciblant des problèmes de codage spécifiques.

## <a name="common-tasks"></a>Tâches courantes

|Tâches courantes|Contenu de prise en charge|
|------------------|------------------------|
|**Faire des exercices pratiques :** Découvrez les principes de base de l’analyse du code en corrigeant les défauts dans une application .NET Framework simple.|-   [Procédure pas à pas : analyse du code managé pour les erreurs de code](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|
|**Configurer l’analyse du code pour un projet :** Les règles du code managé sont organisées en ensembles de règles qui ciblent des zones spécifiques, telles que la sécurité et la conception. Vous pouvez utiliser l’un des ensembles de règles standard Microsoft ou créer le vôtre.|-   [Vue d’ensemble de l’analyse du code managé](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Utilisation d’ensembles de règles pour regrouper des règles d’analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Supprimer les avertissements à l’aide de l’attribut SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|
|**Exécuter l’analyse du code :** Vous pouvez spécifier l’exécution automatique de l’analyse du code chaque fois qu’une configuration de projet est générée, et vous pouvez exécuter l’analyse du code manuellement sur un projet.|-   [Comment : activer et désactiver l’analyse du code automatique](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Comment : exécuter l’analyse du code manuellement](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|
|**Analyser les résultats de l’analyse du code :** Les erreurs et avertissements liés à l’analyse du code sont répertoriés dans la fenêtre analyse du code. Vous pouvez choisir un avertissement ou un titre d’erreur pour afficher des informations supplémentaires sur l’avertissement et afficher et mettre en surbrillance la ligne de code source qui a activé la règle. Vous pouvez choisir l’ID d’avertissement pour afficher des informations détaillées dans MSDN Library qui contiennent des informations et des exemples sur la manière de résoudre le problème.|-   [Comment : afficher les erreurs de code managé](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Analyse du code pour les avertissements liés au code managé](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Avertissements par CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Méthodes anonymes et analyse du code](../code-quality/anonymous-methods-and-code-analysis.md)|
|**Intégrez l’analyse du code à votre cycle de vie de développement :** Les stratégies d’archivage dans [!INCLUDE[esprscc](../includes/esprscc-md.md)] permettent aux équipes de développement de s’assurer que tous les archivages de code sont conformes à un ensemble commun de normes d’analyse du code. La création d’un élément de travail pour une violation de règle d’analyse du code est une procédure simple que vous pouvez effectuer dans la fenêtre Liste d’erreurs.|-   [Amélioration de la qualité du code avec les stratégies d’archivage de projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Comment : synchroniser des ensembles de règles de projet de code avec la stratégie d’archivage de projet d’équipe](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Comment : créer un élément de travail pour une erreur de code managé](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|
