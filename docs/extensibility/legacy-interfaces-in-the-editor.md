---
title: "Les Interfaces héritées dans l’éditeur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e6f4c118ac9306bc533ba7cf62037a8255e9c42f
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-interfaces-in-the-editor"></a>Interfaces héritées dans l’éditeur
Vous pouvez accéder à l’éditeur Visual Studio à partir des interfaces héritées. Le Kit de développement logiciel Visual Studio inclut des adaptateurs appelés *shims*, qui permettent à ces interfaces interagir avec le nouvel éditeur. Néanmoins, nous vous recommandons de vous mettre à jour votre code hérité pour utiliser l’éditeur de nouvelles API. Votre code sera plus performant et vous pouvez utiliser les nouvelles technologies telles que Windows Presentation Foundation (WPF) et Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Adaptation de l’éditeur de Code hérité](../extensibility/adapting-legacy-code-to-the-editor.md)|Explique comment adapter votre code pour le nouvel éditeur.|  
|[Comportement nouveau ou modifié avec les cartes d’éditeur](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Explique comment le comportement de l’éditeur de cartes diffère de celui des versions précédentes de l’éditeur.|  
|[Dans l’éditeur de base](../extensibility/inside-the-core-editor.md)|Décrit les différents composants des versions antérieures de l’éditeur.|  
|[L’instanciation de l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Explique comment utiliser l’API héritée pour instancier l’éditeur principal.|  
|[Fabriques d’éditeur](../extensibility/editor-factories.md)|Explique comment utiliser des fabriques d’éditeur avec l’API héritée.|  
|[Comment : enregistrer des Types de fichiers de l’éditeur](../extensibility/how-to-register-editor-file-types.md)|Explique comment associer une extension de nom de fichier dans votre éditeur.|  
|[Procédure pas à pas : Création d’un éditeur de base et l’inscription d’un Type de fichier de l’éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Explique comment créer une base éditeur et lier une extension de nom de fichier.|  
|[Comment : fournir un contexte pour les éditeurs](../extensibility/how-to-provide-context-for-editors.md)|Explique comment fournir un contexte pour votre éditeur.|  
|[Services de langage et de l’éditeur de base](../extensibility/language-services-and-the-core-editor.md)|Explique les interactions entre un service de langage et un éditeur.|  
|[L’accès à la mémoire tampon de texte à l’aide de l’API héritée](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Explique comment accéder à la mémoire tampon de texte à l’aide de l’API héritée.|  
|[L’accès à theText vue à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Explique comment accéder à la vue de texte à l’aide de l’API héritée.|  
|[Personnalisation des fenêtres de Code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Explique comment personnaliser des fenêtres de code à l’aide de l’API héritée.|  
|[L’accès à des calques de texte à l’aide de l’API héritée](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Explique comment accéder aux différentes couches de texte à l’aide de l’API héritée.|  
|[À l’aide de marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)|Explique comment ajouter des marqueurs de texte à l’aide de l’API héritée.|  
|[Personnalisation des Menus et contrôles d’édition à l’aide de l’API héritée](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Explique comment personnaliser les contrôles d’édition à l’aide de l’API héritée.|  
|[Gestion Annuler et rétablir à l’aide de l’API héritée](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Explique comment gérer les annuler et rétablir à l’aide de l’API héritée.|  
|[Comment : implémenter la rechercher et remplacer le mécanisme](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Explique comment gérer les rechercher et remplacer à l’aide de l’API héritée.|  
|[Comment : supprimer les Notifications de modification de fichier](../extensibility/how-to-suppress-file-change-notifications.md)|Explique comment supprimer les notifications de modification de fichier à l’aide de l’API héritée.|  
|[Création de concepteurs et éditeurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)|Explique comment créer des concepteurs et éditeurs personnalisés.|  
|[Développement d’un Service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)|Fournit des liens vers des documents sur les fonctionnalités qui fournissent des fonctionnalités de personnalisation pour les [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal en ajoutant la prise en charge pour un service de langage.|  
|[Utilisation de polices et couleurs](../extensibility/using-fonts-and-colors.md)|Explique comment utiliser des polices et couleurs avec les interfaces héritées.|
