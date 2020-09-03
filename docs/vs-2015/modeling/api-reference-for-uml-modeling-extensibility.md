---
title: Informations de référence sur les API pour l’extensibilité de modélisation UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e48bf723b8b1cb77cc1f7f4de9cfb562caccde84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672810"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>Référence des API pour l'extensibilité de la modélisation UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez écrire du code de programme pour lire et modifier les modèles que vous créez avec Visual Studio. La référence de l'API fournit des informations sur les classes spécifiques pour vous aider lors de cette tâche. Pour plus d’informations sur les tâches, consultez les rubriques sous [étendre des modèles et des diagrammes UML](../modeling/extend-uml-models-and-diagrams.md). Pour connaître les versions de Visual Studio qui prennent en charge les modèles UML, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="assemblies"></a>Assemblys

|Assembly|Ce que cela vous permet de faire|
|--------------|--------------------------------|
|Microsoft.VisualStudio.Uml.Interfaces.dll|-Lire et modifier les éléments de modèle tels que IUseCase, IAssociation, etc.<br />-Parcourir les relations entre les éléments.<br /><br /> Les espaces de noms et les types correspondent à ceux définis dans la spécification UML.|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-Créer des instances d’éléments de modèle<br />-Accéder aux formes et aux diagrammes et les modifier.|

## <a name="see-also"></a>Voir aussi
 [Étendre les modèles et diagrammes UML](../modeling/extend-uml-models-and-diagrams.md) [référence des API pour modeler SDK pour Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
