---
title: Personnalisation de Code Windows à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0ea617a252d60d8e8d5810c42f7331508c28165
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708977"
---
# <a name="customize-code-windows-by-using-the-legacy-api"></a>Personnaliser les fenêtres de code à l’aide de l’API héritée
Une fenêtre de code est un objet de fenêtre de document qui prend en charge une ou plusieurs vues de texte. Les fonctionnalités exactes d’une fenêtre de code varient selon le service de langage associé. En mode d’interface multidocument (MDI), la fenêtre de code est le frame enfant MDI.

 Fenêtres de code sont contrôlées par les services de langage, et chaque service de langage peut fournir son propre gestionnaire de fenêtre de code. Ainsi, le service de langage ajouter ses propres ornements à la fenêtre de code, tels que des tildes, la colorisation et bien plus encore. Pour plus d’informations sur la création d’une fenêtre principale, consultez [instancier l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).

 Une fenêtre de code est un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objet qui a un affichage de texte et tous les ornements doit se trouver dans l’objet. Lorsque vous créez la fenêtre de code pendant votre instanciation des principales éditeur, votre service de langage peut attacher un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> à la fenêtre de code, comme est indiqué dans l’illustration suivante.

 ![Graphique de CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow") fenêtre de Code

 Le service de langage implémente le Gestionnaire de fenêtres de code et est chargé de gérer des ornements, tels que d’une barre déroulante. La fenêtre de code appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> méthode pendant l’initialisation de fenêtre de code. Lorsque cet appel est effectué, le service de langage peut ajouter une barre déroulante ou une barre de boutons (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) dans la fenêtre de code.

## <a name="in-this-section"></a>Dans cette section
 `Customizing Code Windows by Using the Legacy API` Explique comment personnaliser les fenêtres de code à l’aide de l’API héritée.

- [Guide pratique pour Héberger un éditeur dans un autre éditeur](../extensibility/how-to-host-an-editor-in-another-editor.md) explique comment héberger un second éditeur à l’intérieur d’une fenêtre d’éditeur.

- [Guide pratique pour Déclencher des événements lorsque l’éditeur perd le focus](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md) explique comment attacher une vue de document à un objet de données de document.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Instancier l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
- [Vue de theText d’accès à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)