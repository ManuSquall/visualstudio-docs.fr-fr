---
title: Les Interfaces héritées dans l’éditeur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 340156463d2c4ec194ed70c0c8d74232574917ee
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842643"
---
# <a name="legacy-interfaces-in-the-editor"></a>Interfaces héritées dans l’éditeur
Vous pouvez accéder à l’éditeur Visual Studio à partir des interfaces héritées. Le SDK Visual Studio inclut des adaptateurs appelés *shims*, qui activent ces interfaces interagir avec le nouvel éditeur. Néanmoins, nous recommandons que vous mettez à jour votre code hérité pour utiliser l’éditeur de nouvelles API. Votre code sera plus performant, et vous pouvez utiliser les nouvelles technologies telles que Windows Presentation Foundation (WPF) et de Managed Extensibility Framework (MEF).  

## <a name="related-topics"></a>Rubriques connexes  

| Titre | Description |
| - | - |
| [Adapter le code hérité vers l’éditeur](../extensibility/adapting-legacy-code-to-the-editor.md) | Explique comment adapter votre code vers le nouvel éditeur. |
| [Comportement nouveau ou modifié avec les adaptateurs de l’éditeur](../extensibility/new-or-changed-behavior-with-editor-adapters.md) | Explique comment le comportement des adaptateurs éditeur diffère de celui des versions antérieures de l’éditeur. |
| [À l’intérieur de l’éditeur principal](../extensibility/inside-the-core-editor.md) | Décrit les différents composants de versions antérieures de l’éditeur. |
| [Instancier l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md) | Explique comment utiliser l’API héritée pour instancier l’éditeur principal. |
| [Fabriques d’éditeur](../extensibility/editor-factories.md) | Explique comment utiliser des fabriques d’éditeur avec l’API héritée. |
| [Guide pratique pour Inscrire des types de fichiers de l’éditeur](../extensibility/how-to-register-editor-file-types.md) | Explique comment lier une extension de nom de fichier à votre éditeur. |
| [Procédure pas à pas : Créer un cœur éditeur et enregistrer un type de fichier de l’éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md) | Explique comment créer un cœur éditeur et le lien vers une extension de nom de fichier. |
| [Guide pratique pour Fournir un contexte pour les éditeurs](../extensibility/how-to-provide-context-for-editors.md) | Explique comment fournir un contexte de votre éditeur. |
| [Services de langage et de l’éditeur principal](../extensibility/language-services-and-the-core-editor.md) | Explique les interactions entre un service de langage et un éditeur. |
| [Accéder à la mémoire tampon de texte à l’aide de l’API héritée](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) | Explique comment accéder à la mémoire tampon de texte à l’aide de l’API héritée. |
| [Vue de theText d’accès à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) | Explique comment accéder à l’affichage de texte à l’aide de l’API héritée. |
| [Personnaliser les fenêtres de code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md) | Explique comment personnaliser les fenêtres de code à l’aide de l’API héritée. |
| [Couches de texte de l’accès à l’aide de l’API héritée](../extensibility/accessing-text-layers-by-using-the-legacy-api.md) | Explique comment accéder aux différentes couches de texte à l’aide de l’API héritée. |
| [Utiliser des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md) | Explique comment ajouter des marqueurs de texte à l’aide de l’API héritée. |
| [Personnaliser des menus et contrôles d’édition à l’aide de l’API héritée](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md) | Explique comment personnaliser les contrôles d’édition à l’aide de l’API héritée. |
| [Gérer l’annulation et de restauration par progression à l’aide de l’API héritée](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md) | Explique comment gérer l’annulation et de restauration par progression à l’aide de l’API héritée. |
| [Guide pratique pour Implémenter la rechercher et remplacer le mécanisme](../extensibility/how-to-implement-the-find-and-replace-mechanism.md) | Explique comment gérer les rechercher et remplacer à l’aide de l’API héritée. |
| [Guide pratique pour Supprimer les notifications de modification de fichier](../extensibility/how-to-suppress-file-change-notifications.md) | Explique comment supprimer les notifications de modification de fichier à l’aide de l’API héritée. |
| [Créer des concepteurs et éditeurs personnalisés](../extensibility/creating-custom-editors-and-designers.md) | Explique comment créer des concepteurs et éditeurs personnalisés. |
| [Développer un service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md) | Fournit des liens vers des documents sur les fonctionnalités qui fournissent des fonctionnalités de personnalisation à la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal en ajoutant la prise en charge pour un service de langage. |
| [Utiliser des polices et couleurs](../extensibility/using-fonts-and-colors.md) | Explique comment utiliser des polices et couleurs avec les interfaces héritées. |
