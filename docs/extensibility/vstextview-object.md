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
ms.openlocfilehash: eddd5640b2f8f073f791f6bdb4dc006f8fab0e36
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322811"
---
# <a name="vstextview-object"></a>Objet VSTextView
L’affichage de texte est une fenêtre qui permet aux utilisateurs d’afficher et modifier le texte Unicode de la mémoire tampon de texte. La vue est essentiellement ce que la plupart des utilisateurs font référence en tant que l’éditeur. Étant donné que la vue est séparée de la mémoire tampon par les différentes couches de texte (le retour automatique à texte en mode plan et ainsi de suite), la vue n’est pas garantie pour être une représentation exacte du texte dans la mémoire tampon. Pour plus d’informations sur l’affichage de texte, consultez [accès theText vue à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

 Le tableau suivant présente les interfaces dans le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objet.

|Interface|Description|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permet la création d’actions composites (autrement dit, les actions qui sont regroupées dans une unité d’annulation/de rétablissement unique).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fournit les méthodes de base pour la gestion et l’accès à la vue. `IVsTextView` est pas thread-safe.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crée et gère un volet de fenêtre.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagit avec les couches de texte.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Effectue des opérations sur la vue à partir d’un thread différent.|

## <a name="see-also"></a>Voir aussi
- [Édition de figures](https://www.microsoft.com/download/details.aspx?id=55984)
- [Objet VSTextBuffer](../extensibility/vstextbuffer-object.md)
- [L’accès aux theText vue à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)