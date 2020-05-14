---
title: Objet VSTextView (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81d5e02d6ec18f8561a83b414532a4b78def5c09
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697713"
---
# <a name="vstextview-object"></a>Objet VSTextView

La vue de texte est une fenêtre qui permet aux utilisateurs d’afficher et de modifier le texte Unicode du tampon de texte. Essentiellement, la vue est ce que la plupart des utilisateurs appellent l’éditeur. Étant donné que la vue est séparée du tampon par diverses couches de texte (enveloppement de mots, texte décrivant, etc.), la vue n’est pas garantie d’être une représentation exacte du texte dans le tampon. Pour plus d’informations sur la vue de texte, voir [Accéder à la vueText en utilisant l’API hérité](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015).

Le tableau suivant affiche les <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> interfaces de l’objet.

|Interface|Description|
|---------------|-----------------|
|[IDropSource (en)](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permet la création d’actions composées (c’est-à-dire des actions regroupées en une seule unité dédo/redo).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fournit les méthodes de base pour gérer et accéder à la vue. `IVsTextView`n’est pas enfilé sûr.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crée et gère une vitre.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagit avec les couches de texte.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Effectue des opérations sur la vue à partir d’un thread différent.|

## <a name="see-also"></a>Voir aussi

- [Modification des chiffres](https://www.microsoft.com/download/details.aspx?id=55984)
- [Objet VSTextBuffer](../extensibility/vstextbuffer-object.md)
