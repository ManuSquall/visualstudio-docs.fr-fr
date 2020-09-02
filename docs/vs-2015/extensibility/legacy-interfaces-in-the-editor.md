---
title: Interfaces héritées dans l’éditeur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8483068ae03c9a57fc67b528393e5d6830c3ec33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180291"
---
# <a name="legacy-interfaces-in-the-editor"></a>Interfaces héritées dans l’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez accéder à l’éditeur Visual Studio à partir d’interfaces héritées. Le kit de développement logiciel (SDK) Visual Studio comprend des adaptateurs appelés *shims*, qui permettent à ces interfaces d’interagir avec le nouvel éditeur. Néanmoins, nous vous recommandons de mettre à jour votre code hérité pour utiliser la nouvelle API Editor. Votre code sera plus performant et vous pourrez utiliser de nouvelles technologies telles que le Windows Presentation Foundation (WPF) et le Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Adaptation du code hérité dans l’éditeur](../extensibility/adapting-legacy-code-to-the-editor.md)|Explique comment adapter votre code au nouvel éditeur.|  
|[Comportement nouveau ou modifié avec les adaptateurs de l’éditeur](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Explique comment le comportement des adaptateurs de l’éditeur diffère de celui des versions antérieures de l’éditeur.|  
|[À l’intérieur de l’éditeur de base](../extensibility/inside-the-core-editor.md)|Décrit les différents composants des versions antérieures de l’éditeur.|  
|[Instanciation de l’éditeur de base à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Explique comment utiliser l’API héritée pour instancier l’éditeur principal.|  
|[Fabriques d’éditeur](../extensibility/editor-factories.md)|Explique comment utiliser les fabriques d’éditeur avec l’API héritée.|  
|[Guide pratique pour inscrire des types de fichiers d’éditeur](../extensibility/how-to-register-editor-file-types.md)|Explique comment lier une extension de nom de fichier à votre éditeur.|  
|[Procédure pas à pas : création d’un éditeur de base et inscription d’un type de fichier d’éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Explique comment créer un éditeur principal et lui associer une extension de nom de fichier.|  
|[Guide pratique : fournir un contexte pour les éditeurs](../extensibility/how-to-provide-context-for-editors.md)|Explique comment fournir un contexte à votre éditeur.|  
|[Services linguistiques et éditeur de base](../extensibility/language-services-and-the-core-editor.md)|Explique les interactions entre un service de langage et un éditeur.|  
|[Accès à la mémoire tampon du texte à l’aide de l’API héritée](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Explique comment accéder à la mémoire tampon de texte à l’aide de l’API héritée.|  
|[Accès à la vue texte à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Explique comment accéder à l’affichage de texte à l’aide de l’API héritée.|  
|[Personnalisation des fenêtres de code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Explique comment personnaliser les fenêtres de code à l’aide de l’API héritée.|  
|[Accès aux couches de texte à l’aide de l’API héritée](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Explique comment accéder à différentes couches de texte à l’aide de l’API héritée.|  
|[Utilisation de marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)|Explique comment ajouter des marqueurs de texte à l’aide de l’API héritée.|  
|[Personnalisation des contrôles et menus de l’éditeur à l’aide de l’API héritée](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Explique comment personnaliser les contrôles d’éditeur à l’aide de l’API héritée.|  
|[Gestion de l’annulation et du rétablissement à l’aide de l’API héritée](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Explique comment gérer les opérations d’annulation et de rétablissement à l’aide de l’API héritée.|  
|[Guide pratique pour implémenter le mécanisme Rechercher et remplacer](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Explique comment gérer la recherche et le remplacement à l’aide de l’API héritée.|  
|[Guide pratique pour supprimer les notifications de modification de fichier](../extensibility/how-to-suppress-file-change-notifications.md)|Explique comment supprimer les notifications de modification de fichier à l’aide de l’API héritée.|  
|[Création d’éditeurs et de concepteurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)|Explique comment créer des éditeurs et des concepteurs personnalisés.|  
|[Développement d’un service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)|Fournit des liens vers des documents sur les fonctionnalités qui fournissent des fonctionnalités de personnalisation à l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur principal en ajoutant la prise en charge d’un service de langage.|  
|[Utilisation des polices et couleurs](../extensibility/using-fonts-and-colors.md)|Explique comment utiliser les polices et les couleurs avec les interfaces héritées.|
