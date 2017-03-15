---
title: "Vue d’ensemble de l’analyse du code manag&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectpropertypages.codeanalysis"
helpviewer_keywords: 
  - "analyse du code, code managé"
  - "code managé, analyse du code"
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 35
caps.handback.revision: 35
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vue d’ensemble de l’analyse du code manag&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'outil d'analyse du code managé analyse les assemblys et signale les informations à leur sujet, notamment les violations des règles de programmation et de design présentées dans les règles de conception de Microsoft .NET Framework.  
  
 L'outil d'analyse représente les contrôles effectués lors d'une analyse comme messages d'avertissement.  Les messages d'avertissement identifient les problèmes de programmation et de conception pertinents et, si possible, fournissent des informations relatives à leur résolution.  
  
## Intégration IDE \(environnement de développement intégré\)  
 En tant que développeur, vous pouvez lancer automatiquement l'analyse du code sur votre projet ou l'exécuter manuellement.  
  
 Pour lancer l'analyse du code chaque fois que vous générez un projet, vous sélectionnez **Activer l'analyse du code sur la build \(définit la constante CODE\_ANALYSIS\)** sur la page de propriétés du projet.  Pour plus d'informations, consultez [Comment : activer et désactiver l'analyse du code automatique](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md).  
  
 Pour exécuter manuellement l'analyse du code sur un projet, dans le menu **Analyser**, cliquez sur **Exécuter l'analyse du code sur** *ProjectName*.  Pour plus d'informations, consultez [Comment : activer et désactiver l'analyse du code automatique](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md).  
  
## Ensembles de règles  
 Pour le code managé, les règles d'analyse du code sont regroupées dans des *ensembles de règles*.  Vous pouvez utiliser l'un des ensembles de règles standard Microsoft ou créer un ensemble de règles personnalisé pour répondre à un besoin particulier.  Pour plus d'informations, consultez [Utilisation d'ensembles de règles pour regrouper des règles d'analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## Suppression à la source  
 Bien souvent, il est utile d'indiquer qu'un avertissement ne s'applique pas.  Cela permet d'informer le développeur et les éventuels réviseurs de code, qu'un avertissement a fait l'objet d'une analyse, puis a été supprimé ou ignoré.  
  
 La suppression à la source d'avertissements est implémentée via des attributs personnalisés.  Pour supprimer un avertissement, ajoutez l'attribut `SuppressMessage` au code source comme indiqué dans l'exemple suivant :  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 Pour plus d'informations, consultez [Supprimer des avertissements à l'aide de l'attribut SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## Exécuter l'analyse du code dans le cadre de la stratégie d'archivage  
 En tant qu'organisation, vous pourriez demander à ce que tous les archivages respectent certaines stratégies.  En particulier, vous souhaitez vous assurer que vous suivez ces règles :  
  
-   Il n'y a eu aucune erreur de build dans le code en cours d'archivage.  
  
-   L'analyse du code a été effectuée sur la version de code la plus récente.  
  
 Vous pouvez l'effectuer en spécifiant des stratégies d'archivage.  Pour plus d'informations, consultez [Amélioration de la qualité du code avec des stratégies d’archivage de projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## Intégration de Team Build  
 Vous pouvez utiliser les fonctionnalités intégrées du système de génération pour exécuter l'outil d'analyse dans le cadre du processus de génération.  Pour plus d'informations, consultez [Générer l'application](../Topic/Build%20the%20application.md).  
  
## Voir aussi  
 [Utilisation d'ensembles de règles pour regrouper des règles d'analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Comment : activer et désactiver l'analyse du code automatique](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md)