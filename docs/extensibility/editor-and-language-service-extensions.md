---
title: Extensions du service de langage et de l’éditeur | Microsoft Docs
description: Vous pouvez étendre la plupart des fonctionnalités de l’éditeur de code Visual Studio, qui est implémenté à l’aide de Windows Presentation Foundation et qui est écrit en code managé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 038253d1863c2d599c7c7a1e5c5a1398d67740ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883517"
---
# <a name="editor-and-language-service-extensions"></a>Extensions du service de langage et de l’éditeur
Vous pouvez étendre la plupart des fonctionnalités de l’éditeur de code Visual Studio. L’éditeur est basé sur le Windows Presentation Foundation (WPF) et écrit en code managé. Bien que cette conception diffère des conceptions dans les versions antérieures de Visual Studio, elle fournit la plupart des fonctionnalités. Pour étendre l’éditeur, utilisez le Managed Extensibility Framework (MEF).

 Le kit de développement logiciel (SDK) Visual Studio fournit des adaptateurs appelés *shims* pour prendre en charge les VSPackages qui ont été écrits pour des versions antérieures. Néanmoins, si vous disposez déjà d’un VSPackage, nous vous recommandons de le mettre à jour vers la nouvelle technologie pour obtenir de meilleures performances et une meilleure fiabilité.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introduction à l’utilisation des modèles d’élément de l’éditeur.|
|[Étendre l’éditeur et les services de langage](../extensibility/extending-the-editor-and-language-services.md)|Liens vers des documents qui présentent la conception et les fonctionnalités de l’éditeur principal et montrent comment l’étendre.|
|[Interfaces héritées dans l’éditeur](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)|Liens vers des documents qui expliquent comment accéder à l’éditeur principal à partir du code existant.|
|[Créer des éditeurs et des concepteurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)|Liens vers des documents qui expliquent comment créer des éditeurs personnalisés.|
|[Extensibilité du service de langage hérité](../extensibility/internals/legacy-language-service-extensibility.md)|Liens vers des documents qui décrivent comment intégrer des langages de programmation dans Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Présente le Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Présente le Windows Presentation Foundation (WPF).|
