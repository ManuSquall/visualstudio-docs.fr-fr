---
title: Vue d’ensemble de l’analyse du code pour du code managé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b4c22076a5f08b1b8f25722e5c3a5fef27b81b9e
ms.sourcegitcommit: b56dc6fadc6c924beed36bb4c2ccc16cf6bcfa1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68739988"
---
# <a name="code-analysis-for-managed-code-overview"></a>Vue d’ensemble de l’analyse du code managé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'outil d'analyse du code managé analyse les assemblys et signale les informations à leur sujet, notamment les violations des règles de programmation et de design présentées dans les règles de conception de Microsoft .NET Framework.  
  
 L'outil d'analyse représente les contrôles effectués lors d'une analyse comme messages d'avertissement. Les messages d'avertissement identifient les problèmes de programmation et de conception pertinents et, si possible, fournissent des informations relatives à leur résolution.  
  
## <a name="ide-integrated-development-environment-integration"></a>Intégration IDE (environnement de développement intégré)  
 En tant que développeur, vous pouvez lancer automatiquement l'analyse du code sur votre projet ou l'exécuter manuellement.  
  
 Pour exécuter l’analyse du code chaque fois que vous générez un projet, sélectionnez **Activer l’analyse du code sur la build (définit la constante CODE_ANALYSIS)** dans la page de propriétés du projet. Pour plus d'informations, voir [Procédure : Activer et désactiver l’analyse du code automatique](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
 Pour exécuter l’analyse du code manuellement dans un projet, dans le menu **Analyser**, cliquez sur **Exécuter l’analyse du code sur**_nom_projet_. Pour plus d'informations, voir [Procédure : Activer et désactiver l’analyse du code automatique](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
## <a name="rule-sets"></a>Ensembles de règles  
 Les règles d’analyse du code pour le code managé sont regroupées dans des *ensembles de règles*. Vous pouvez utiliser l'un des ensembles de règles standard Microsoft ou créer un ensemble de règles personnalisé pour répondre à un besoin particulier. Pour plus d’informations, consultez [Utilisation d’ensembles de règles pour regrouper des règles d’analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## <a name="in-source-suppression"></a>Suppression à la source  
 Bien souvent, il est utile d'indiquer qu'un avertissement ne s'applique pas. Cela permet d’informer le développeur et les éventuels réviseurs de code, qu’un avertissement a fait l’objet d’une analyse, puis a été supprimé ou ignoré.  
  
 La suppression à la source d'avertissements est implémentée via des attributs personnalisés. Pour supprimer un avertissement, ajoutez l'attribut `SuppressMessage` au code source comme indiqué dans l'exemple suivant :  
  
 ```csharp
 [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
 Public class MyClass
 {
     // code
 }
 ```
  
 Pour plus d’informations, consultez [Supprimer des avertissements à l’aide de l’attribut SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Exécuter l’analyse du code dans le cadre de la stratégie d’archivage  
 En tant qu’organisation, vous pourriez demander à ce que tous les archivages respectent certaines stratégies. En particulier, vous souhaitez vous assurer que vous suivez ces règles :  
  
- Il n'y a eu aucune erreur de build dans le code en cours d'archivage.  
  
- L'analyse du code a été effectuée sur la version de code la plus récente.  
  
  Vous pouvez l'effectuer en spécifiant des stratégies d'archivage. Pour plus d’informations, consultez [Amélioration de la qualité du code avec des stratégies d’archivage de projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## <a name="team-build-integration"></a>Intégration de Team Build  
 Vous pouvez utiliser les fonctionnalités intégrées du système de génération pour exécuter l'outil d'analyse dans le cadre du processus de génération. Pour plus d’informations, consultez l’article [Générer l’application](/azure/devops/pipelines/index).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’ensembles de règles pour regrouper des règles d’analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Guide pratique pour Activer et désactiver l’analyse du code automatique](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
