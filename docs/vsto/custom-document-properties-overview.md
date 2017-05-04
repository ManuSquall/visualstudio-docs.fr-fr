---
title: "Vue d&#39;ensemble des propri&#233;t&#233;s de document personnalis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "_AssemblyLocation (propriété)"
  - "_AssemblyName (propriété)"
  - "propriétés de documents personnalisés"
  - "personnalisations au niveau du document (développement Office dans Visual Studio), propriétés personnalisées"
  - "documents (développement Office dans Visual Studio), propriétés personnalisées"
  - "documents Office (développement Office dans Visual Studio), propriétés personnalisées"
ms.assetid: 9a215904-b760-4a49-93e8-a1a708ce0526
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Vue d&#39;ensemble des propri&#233;t&#233;s de document personnalis&#233;es
  Lorsque vous générez un projet au niveau du document, Visual Studio ajoute deux propriétés personnalisées au document du projet : \_AssemblyLocation et \_AssemblyName.  Lorsqu'un utilisateur ouvre un document, l'application Microsoft Office vérifie s'il comporte ces propriétés personnalisées.  Si elles existent dans le document, l'application charge [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], qui démarre la personnalisation.  Pour plus d’informations, consultez [Architecture des solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## \_AssemblyName  
 Cette propriété contient le CLSID d'une interface du composant du chargeur de la solution Office de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  La valeur CLSID est 4E3C66D5\-58D4\-491E\-A7D4\-64AF99AF6E8B.  Cette valeur ne doit jamais être modifiée.  
  
## \_AssemblyLocation  
 Cette propriété contient une chaîne qui fournit des détails relatifs au manifeste de déploiement pour la personnalisation.  Pour plus d'informations sur les manifestes, consultez [Manifestes d'application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 La valeur de la propriété \_AssemblyLocation peut présenter un format différent selon la façon dont la solution est déployée :  
  
-   Si la solution est publiée pour être installée à partir d'un site Web, chemin d'accès UNC, CD ou lecteur USB, la propriété \_AssemblyLocation est au format *DeploymentManifestPath*|*SolutionID*.  La chaîne suivante en est un exemple :  
  
     file:\/\/deployserver\/MyShare\/ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9  
  
-   Si la solution est en cours d'exécution ou de débogage dans Visual Studio, la propriété \_AssemblyLocation est au format *DeploymentManifestName*|*SolutionID*|vstolocal.  La chaîne suivante en est un exemple :  
  
     ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9|vstolocal  
  
 *SolutionID* est un GUID utilisé par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pour identifier la solution.  *SolutionID* est généré automatiquement lorsque vous générez le projet. Le terme d' **vstolocal** indique à [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que l'assembly doit être chargé à partir de le même répertoire que le document.  
  
## Voir aussi  
 [Architecture des solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md)   
 [Manifestes d'application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Comment : publier une solution Office à l'aide de ClickOnce](http://msdn.microsoft.com/fr-fr/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Comment : créer et modifier des propriétés de document personnalisées](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  