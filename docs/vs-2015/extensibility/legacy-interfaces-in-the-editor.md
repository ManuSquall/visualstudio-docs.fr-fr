---
title: Les Interfaces héritées dans l’éditeur | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ae8f087a9f52ca2eff130b7972c2cd9d68a139f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504267"
---
# <a name="legacy-interfaces-in-the-editor"></a>Interfaces héritées dans l’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Interfaces hérité dans l’éditeur](https://docs.microsoft.com/visualstudio/extensibility/legacy-interfaces-in-the-editor).  
  
Vous pouvez accéder à l’éditeur Visual Studio à partir des interfaces héritées. Le SDK Visual Studio inclut des adaptateurs appelés *shims*, qui activent ces interfaces interagir avec le nouvel éditeur. Néanmoins, nous recommandons que vous mettez à jour votre code hérité pour utiliser l’éditeur de nouvelles API. Votre code sera plus performant, et vous pouvez utiliser les nouvelles technologies telles que Windows Presentation Foundation (WPF) et de Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Adaptation du code hérité à l’éditeur](../extensibility/adapting-legacy-code-to-the-editor.md)|Explique comment adapter votre code vers le nouvel éditeur.|  
|[Comportement nouveau ou modifié avec les adaptateurs de l’éditeur](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Explique comment le comportement des adaptateurs éditeur diffère de celui des versions antérieures de l’éditeur.|  
|[Dans l’éditeur de base](../extensibility/inside-the-core-editor.md)|Décrit les différents composants de versions antérieures de l’éditeur.|  
|[Instanciation de l’éditeur de base à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Explique comment utiliser l’API héritée pour instancier l’éditeur principal.|  
|[Fabriques d’éditeur](../extensibility/editor-factories.md)|Explique comment utiliser des fabriques d’éditeur avec l’API héritée.|  
|[Guide pratique pour inscrire des types de fichiers d’éditeur](../extensibility/how-to-register-editor-file-types.md)|Explique comment lier une extension de nom de fichier à votre éditeur.|  
|[Procédure pas à pas : création d’un éditeur de base et inscription d’un type de fichier d’éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Explique comment créer un cœur éditeur et le lien vers une extension de nom de fichier.|  
|[Guide pratique : fournir un contexte pour les éditeurs](../extensibility/how-to-provide-context-for-editors.md)|Explique comment fournir un contexte de votre éditeur.|  
|[Services de langage et éditeur de base](../extensibility/language-services-and-the-core-editor.md)|Explique les interactions entre un service de langage et un éditeur.|  
|[Accès à la mémoire tampon de texte à l’aide de l’API héritée](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Explique comment accéder à la mémoire tampon de texte à l’aide de l’API héritée.|  
|[Accès au mode texte à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Explique comment accéder à l’affichage de texte à l’aide de l’API héritée.|  
|[Personnalisation des fenêtres Code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Explique comment personnaliser les fenêtres de code à l’aide de l’API héritée.|  
|[Accès aux calques de texte à l’aide de l’API héritée](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Explique comment accéder aux différentes couches de texte à l’aide de l’API héritée.|  
|[Utilisation de marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)|Explique comment ajouter des marqueurs de texte à l’aide de l’API héritée.|  
|[Personnalisation des menus et contrôles d’édition à l’aide de l’API héritée](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Explique comment personnaliser les contrôles d’édition à l’aide de l’API héritée.|  
|[Gestion des opérations d’annulation et de rétablissement à l’aide de l’API héritée](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Explique comment gérer l’annulation et de restauration par progression à l’aide de l’API héritée.|  
|[Guide pratique pour implémenter le mécanisme Rechercher et remplacer](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Explique comment gérer les rechercher et remplacer à l’aide de l’API héritée.|  
|[Guide pratique pour supprimer les notifications de modification de fichier](../extensibility/how-to-suppress-file-change-notifications.md)|Explique comment supprimer les notifications de modification de fichier à l’aide de l’API héritée.|  
|[Création d’éditeurs et de concepteurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)|Explique comment créer des concepteurs et éditeurs personnalisés.|  
|[Développement d’un service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)|Fournit des liens vers des documents sur les fonctionnalités qui fournissent des fonctionnalités de personnalisation à la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur principal en ajoutant la prise en charge pour un service de langage.|  
|[Utilisation des polices et des couleurs](../extensibility/using-fonts-and-colors.md)|Explique comment utiliser des polices et couleurs avec les interfaces héritées.|

