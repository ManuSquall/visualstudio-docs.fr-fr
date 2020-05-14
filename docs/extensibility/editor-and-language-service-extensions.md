---
title: Extensions de l’éditeur et du service linguistique Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e37165dc5fe9ac010545304218e807d923b424b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712019"
---
# <a name="editor-and-language-service-extensions"></a>Extensions de service d’éditeur et de langue
Vous pouvez étendre la plupart des fonctionnalités de l’éditeur de code Visual Studio. L’éditeur est basé sur la Windows Presentation Foundation (WPF) et est écrit dans le code géré. Bien que cette conception diffère des conceptions dans les versions antérieures de Visual Studio, il fournit la plupart des mêmes caractéristiques. Pour étendre l’éditeur, utilisez le Cadre d’extégabilité gérée (MEF).

 Le Visual Studio SDK fournit des adaptateurs connus sous le nom *de cales* pour prendre en charge VSPackages qui ont été écrits pour les versions antérieures. Néanmoins, si vous avez un VSPackage existant, nous vous recommandons de le mettre à jour vers la nouvelle technologie pour obtenir de meilleures performances et fiabilité.

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Créez une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introduction à l’utilisation des modèles d’élément Editor.|
|[Étendre les services d’éditeur et de langue](../extensibility/extending-the-editor-and-language-services.md)|Liens vers des documents qui introduisent la conception et les caractéristiques de l’éditeur de base et montrent comment l’étendre.|
|[Interfaces héritées dans l’éditeur](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)|Liens vers des documents qui expliquent comment accéder à l’éditeur de base à partir du code existant.|
|[Créez des éditeurs et des designers personnalisés](../extensibility/creating-custom-editors-and-designers.md)|Liens vers des documents qui expliquent comment créer des éditeurs personnalisés.|
|[Héritage service linguistique extéabilité](../extensibility/internals/legacy-language-service-extensibility.md)|Liens vers des documents qui décrivent comment intégrer les langages de programmation dans Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Introduit le Cadre d’extéabilité gérée (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Présente la Windows Presentation Foundation (WPF).|
