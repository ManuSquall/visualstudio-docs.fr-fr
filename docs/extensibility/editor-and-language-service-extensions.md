---
title: "L’éditeur et la langue des Extensions de Service | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 59de764dfcb976dfac303f44a67340e117ae5e06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="editor-and-language-service-extensions"></a>L’éditeur et les Extensions de Service de langage
Vous pouvez étendre la plupart des fonctionnalités de l’éditeur de code Visual Studio. L’éditeur est basée sur Windows Presentation Foundation (WPF) et est écrit en code managé. Bien que cette conception diffère les modèles dans les versions antérieures de Visual Studio, il fournit la plupart de ces fonctionnalités. Pour étendre l’éditeur, utilisez Managed Extensibility Framework (MEF).  
  
 Le Kit de développement logiciel Visual Studio fournit des adaptateurs appelés *shims* pour prendre en charge des VSPackages qui ont été écrites pour les versions antérieures. Néanmoins, si vous avez un VSPackage existant, nous recommandons que vous mettre à jour vers la nouvelle technologie pour obtenir de meilleures performances et fiabilité.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Création d’une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introduction à l’utilisation de modèles d’élément de l’éditeur.|  
|[Extension de l’éditeur et des services de langage](../extensibility/extending-the-editor-and-language-services.md)|Liens vers des documents qui présentent la conception et les fonctionnalités de l’éditeur de base et de montrent comment l’étendre.|  
|[Interfaces héritées dans l’éditeur](../extensibility/legacy-interfaces-in-the-editor.md)|Liens vers des documents qui expliquent comment accéder à l’éditeur principal à partir de code existant.|  
|[Création d’éditeurs et de concepteurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)|Liens vers des documents qui expliquent comment créer des éditeurs personnalisés.|  
|[Extensibilité du service de langage hérité](../extensibility/internals/legacy-language-service-extensibility.md)|Liens vers des documents qui décrivent comment intégrer des langages de programmation dans Visual Studio.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Introduit Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Introduit Windows Presentation Foundation (WPF).|