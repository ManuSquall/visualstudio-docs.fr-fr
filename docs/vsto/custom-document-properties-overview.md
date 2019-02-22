---
title: Vue d’ensemble des propriétés de document personnalisées
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b3f4038a05478d8e2d747efa700c7ece02e4827
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614417"
---
# <a name="custom-document-properties-overview"></a>Vue d’ensemble des propriétés de document personnalisées

Lorsque vous générez un projet au niveau du document, Visual Studio ajoute deux propriétés personnalisées au document dans le projet : \_AssemblyLocation et \_AssemblyName. Lorsqu’un utilisateur ouvre un document, l’application Microsoft Office vérifie pour ces propriétés de document personnalisées. S’ils existent dans le document, l’application charge le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], qui démarre la personnalisation. Pour plus d’informations, consultez [solutions d’Architecture d’Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

Cette propriété contient le CLSID d’une interface dans le composant de chargeur de solution Office de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. La valeur CLSID est 4E3C66D5 58D - 4-491E-A7D4-64AF99AF6E8B. Cette valeur ne doit jamais changer.

## <a name="assemblylocation"></a>\_AssemblyLocation

Cette propriété contient une chaîne qui fournit des détails sur le manifeste de déploiement pour la personnalisation. Pour plus d’informations sur les manifestes, consultez [manifestes d’Application et déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Le \_valeur de la propriété AssemblyLocation peut avoir différents formats, selon la façon dont la solution est déployée :

- Si la solution est publiée pour être installée à partir d’un site Web, chemin d’accès UNC ou un CD ou un lecteur USB, la propriété _AssemblyLocation a le format *DeploymentManifestPath*|*SolutionID*. La chaîne suivante est un exemple :

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Si vous êtes en cours d’exécution ou débogage de la solution à partir de Visual Studio, la propriété _AssemblyLocation a le format *DeploymentManifestName*|*SolutionID*| vstolocal. La chaîne suivante est un exemple :

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

  Le *SolutionID* est un GUID qui le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] utilise pour identifier la solution. Le *SolutionID* est généré automatiquement lorsque vous générez le projet. Le **vstolocal** terme indique à la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que l’assembly doit être chargé à partir du même dossier que le document.

## <a name="see-also"></a>Voir aussi

- [Architecture des solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md)
- [Manifestes d’application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Guide pratique pour Publier une solution Office à l’aide de ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Guide pratique pour Créer et modifier les propriétés de document personnalisées](../vsto/how-to-create-and-modify-custom-document-properties.md)
