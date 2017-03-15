---
title: "Éditeur et la langue des Extensions de Service | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 67d250a2806b367a76fa593026f10d4b671c21b2
ms.lasthandoff: 02/22/2017

---
# <a name="editor-and-language-service-extensions"></a>Éditeur et les Extensions de Service de langage
Vous pouvez étendre la plupart des fonctionnalités de l’éditeur de code Visual Studio. L’éditeur est basée sur Windows Presentation Foundation (WPF) et est écrit en code managé. Bien que cette conception diffère les conceptions dans les versions antérieures de Visual Studio, il fournit les mêmes fonctionnalités. Pour étendre l’éditeur, utilisez Managed Extensibility Framework (MEF).  
  
 Le Kit de développement logiciel Visual Studio fournit des adaptateurs appelés *shims* pour prendre en charge les packages VS qui ont été écrits pour les versions antérieures. Néanmoins, si vous avez un VSPackage existant, nous vous recommandons de mettre à la nouvelle technologie pour obtenir de meilleures performances et la fiabilité.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Création d’une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introduction à l’utilisation de modèles d’élément de l’éditeur.|  
|[Extension de l’éditeur et les Services de langage](../extensibility/extending-the-editor-and-language-services.md)|Liens vers des documents qui présentent la conception et les fonctionnalités de l’éditeur de base et de montrent comment l’étendre.|  
|[Interfaces héritées dans l’éditeur](../extensibility/legacy-interfaces-in-the-editor.md)|Contient des liens vers des documents qui expliquent comment accéder à l’éditeur de base à partir de code existant.|  
|[Création de concepteurs et éditeurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)|Contient des liens vers des documents qui expliquent comment créer des éditeurs personnalisés.|  
|[Extensibilité du Service de langage ancien](../extensibility/internals/legacy-language-service-extensibility.md)|Contient des liens vers des documents qui décrivent comment intégrer des langages de programmation dans Visual Studio.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Introduit Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Présente Windows Presentation Foundation (WPF).|
