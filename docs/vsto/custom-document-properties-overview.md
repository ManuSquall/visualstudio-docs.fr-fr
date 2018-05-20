---
title: Vue d’ensemble des propriétés de document personnalisées
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: b85dfe077f73a26eadf173197de2ca514ff44679
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="custom-document-properties-overview"></a>Vue d’ensemble des propriétés de document personnalisées

Lorsque vous générez un projet au niveau du document, Visual Studio ajoute deux propriétés personnalisées au document dans le projet : \_AssemblyLocation et \_AssemblyName. Lorsqu’un utilisateur ouvre un document, l’application Microsoft Office vérifie les propriétés de document personnalisées. S’ils existent dans le document, l’application charge le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], qui démarre la personnalisation. Pour plus d’informations, consultez [solutions d’Architecture de Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_Nom de l’assembly

Cette propriété contient le CLSID d’une interface dans le composant de chargeur de solution Office de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. La valeur CLSID est 4E3C66D5 - 58D 4-491E-A7D4-64AF99AF6E8B. Cette valeur ne doit jamais changer.

## <a name="assemblylocation"></a>\_AssemblyLocation

Cette propriété contient une chaîne qui fournit des détails sur le manifeste de déploiement pour la personnalisation. Pour plus d’informations sur les manifestes, consultez [manifestes d’Application et déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Valeur de la propriété The_AssemblyLocation peut avoir des formats différents, selon la façon dont la solution est déployée :

- Si la solution est publiée pour être installé à partir d’un site Web, chemin d’accès UNC ou un CD ou lecteur USB, la propriété _AssemblyLocation a le format *DeploymentManifestPath*|*SolutionID*. La chaîne suivante est un exemple :

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Si vous êtes en cours d’exécution ou le débogage de la solution à partir de Visual Studio, la propriété _AssemblyLocation a le format *DeploymentManifestName*|*SolutionID*| vstolocal. La chaîne suivante est un exemple :

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

 Le *SolutionID* est un GUID qui le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] utilise pour identifier la solution. Le *SolutionID* est généré automatiquement lorsque vous générez le projet. Le **vstolocal** terme indique à le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que l’assembly doit être chargé dans le même dossier que le document.

## <a name="see-also"></a>Voir aussi

- [Architecture des solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md)
- [Manifestes d’application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Comment : publier une solution Office à l’aide de ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Comment : créer et modifier les propriétés de document personnalisées](../vsto/how-to-create-and-modify-custom-document-properties.md)
