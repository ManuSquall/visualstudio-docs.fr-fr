---
title: Vue d’ensemble des propriétés de document personnalisées
description: Découvrez que lorsque vous générez un projet au niveau du document, Visual Studio ajoute deux propriétés personnalisées au document dans le projet.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8c30e0b3253e19316eed24fa26500cd55a3dd515
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847791"
---
# <a name="custom-document-properties-overview"></a>Vue d’ensemble des propriétés de document personnalisées

Quand vous générez un projet au niveau du document, Visual Studio ajoute deux propriétés personnalisées au document dans le projet : \_ AssemblyLocation et \_ AssemblyName. Lorsqu’un utilisateur ouvre un document, le Microsoft Office application vérifie ces propriétés de document personnalisées. S’ils existent dans le document, l’application charge le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , qui démarre la personnalisation. Pour plus d’informations, consultez [architecture des solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="_assemblyname"></a>\_AssemblyName

Cette propriété contient le CLSID d’une interface dans le composant chargeur de solution Office de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . La valeur du CLSID est 4E3C66D5-58D4-491E-A7D4-64AF99AF6E8B. Vous ne devez jamais modifier cette valeur.

## <a name="_assemblylocation"></a>\_AssemblyLocation

Cette propriété contient une chaîne qui fournit des détails sur le manifeste de déploiement pour la personnalisation. Pour plus d’informations sur les manifestes, consultez [manifestes d’application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 La \_ valeur de la propriété AssemblyLocation peut avoir des formats différents, en fonction de la façon dont la solution est déployée :

- Si la solution est publiée pour être installée à partir d’un site Web, d’un chemin d’accès UNC, d’un CD ou d’un lecteur USB, la propriété _AssemblyLocation est au format *DeploymentManifestPath* | *SolutionId*. La chaîne suivante est un exemple :

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Si vous exécutez ou déboguez la solution à partir de Visual Studio, la propriété _AssemblyLocation a le format *DeploymentManifestName* | *SolutionId*| vstolocal. La chaîne suivante est un exemple :

     Classeurexcel1. vsto | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal

  *SolutionId* est un GUID que [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] utilise pour identifier la solution. *SolutionId* est généré automatiquement lorsque vous générez le projet. Le terme **vstolocal** indique au [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que l’assembly doit être chargé à partir du même dossier que le document.

## <a name="see-also"></a>Voir aussi

- [Architecture des solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md)
- [Manifestes d’application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Comment : publier une solution Office à l’aide de ClickOnce](/previous-versions/bb386095(v=vs.110))
- [Comment : créer et modifier des propriétés de document personnalisées](../vsto/how-to-create-and-modify-custom-document-properties.md)