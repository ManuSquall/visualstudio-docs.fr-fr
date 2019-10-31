---
title: Objet VSTextView | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 927bbee8bde62ff24396ea7b50e55e901b8cff06
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189011"
---
# <a name="vstextview-object"></a>Objet VSTextView

L’affichage de texte est une fenêtre qui permet aux utilisateurs d’afficher et de modifier le texte Unicode de la mémoire tampon de texte. Pour l’essentiel, la vue est ce que la plupart des utilisateurs font référence à l’éditeur. Étant donné que la vue est séparée de la mémoire tampon par différentes couches de texte (retour automatique à la ligne, texte en mode plan, etc.), il n’est pas garanti que la vue soit une représentation exacte du texte dans la mémoire tampon. Pour plus d’informations sur l’affichage de texte, consultez [accès à la vue theText à l’aide de l’API héritée](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015).

Le tableau suivant présente les interfaces de l’objet <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

|Interface|Description|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Active la création d’actions composées (autrement dit, les actions regroupées en une seule unité d’annulation/de rétablissement).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fournit les méthodes de base pour la gestion et l’accès à la vue. `IVsTextView` n’est pas thread-safe.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crée et gère un volet de fenêtre.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagit avec les couches de texte.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Effectue des opérations sur la vue à partir d’un thread différent.|

## <a name="see-also"></a>Voir aussi

- [Modifications des figures](https://www.microsoft.com/download/details.aspx?id=55984)
- [Objet VSTextBuffer](../extensibility/vstextbuffer-object.md)