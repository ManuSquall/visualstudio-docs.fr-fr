---
title: "Vue d’ensemble des propriétés de Document personnalisées | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4f6dfae83f09398ba9a8d1377c16756487193ee2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="custom-document-properties-overview"></a>Custom Document Properties Overview
  Lorsque vous générez un projet au niveau du document, Visual Studio ajoute deux propriétés personnalisées au document dans le projet : _AssemblyLocation et _AssemblyName. Lorsqu’un utilisateur ouvre un document, l’application Microsoft Office vérifie les propriétés de document personnalisées. S’ils existent dans le document, l’application charge le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], qui démarre la personnalisation. Pour plus d’informations, consultez [Architecture des Solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="assemblyname"></a>_AssemblyName  
 Cette propriété contient le CLSID d’une interface dans le composant de chargeur de solution Office de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. La valeur CLSID est 4E3C66D5 - 58D 4-491E-A7D4-64AF99AF6E8B. Cette valeur ne doit jamais changer.  
  
## <a name="assemblylocation"></a>_AssemblyLocation  
 Cette propriété contient une chaîne qui fournit des détails sur le manifeste de déploiement pour la personnalisation. Pour plus d’informations sur les manifestes, consultez [manifestes d’Application et déploiement dans les Solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Valeur de la propriété The_AssemblyLocation peut avoir des formats différents, selon la façon dont la solution est déployée :  
  
-   Si la solution est publiée pour être installé à partir d’un site Web, chemin d’accès UNC ou un CD ou lecteur USB, la propriété _AssemblyLocation a le format *DeploymentManifestPath*|*SolutionID*. La chaîne suivante est un exemple :  
  
     file://deployserver/myshare/ExcelWorkbook1.VSTO | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9  
  
-   Si vous êtes en cours d’exécution ou le débogage de la solution à partir de Visual Studio, la propriété _AssemblyLocation a le format *DeploymentManifestName*|*SolutionID*| vstolocal. La chaîne suivante est un exemple :  
  
     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal  
  
 Le *SolutionID* est un GUID qui le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] utilise pour identifier la solution. Le *SolutionID* est généré automatiquement lorsque vous générez le projet. Le **vstolocal** terme indique à le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que l’assembly doit être chargé dans le même dossier que le document.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture des Solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architecture des personnalisations au niveau du Document](../vsto/architecture-of-document-level-customizations.md)   
 [Manifestes d’application et déploiement dans les Solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Comment : publier une Solution Office à l’aide de ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Guide pratique pour créer et modifier des propriétés de document personnalisées](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  