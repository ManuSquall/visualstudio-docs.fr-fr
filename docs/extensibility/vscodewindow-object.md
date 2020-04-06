---
title: Objet VSCodeWindow (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55739b1ef577123ac0395b4c5cfb1e3c5dbc779f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697958"
---
# <a name="vscodewindow-object"></a>Objet VSCodeWindow
Une fenêtre de code est une fenêtre de document spécialisée <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> qui peut inclure une ou plusieurs vues de texte, généralement l’objet.

 Architecturalement, la fenêtre de code est une fenêtre de document qui est dans un cadre de fenêtre. Fonctionnellement, la fenêtre de code est simplement une fenêtre de document avec des fonctionnalités supplémentaires. Dans le mode interface multi-documents (MDI), la fenêtre de code est le cadre pour enfant MDI. Pour plus d’informations, voir [Personnaliser les fenêtres de code en utilisant l’API hérité](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

 Le tableau suivant comprend les <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> interfaces de l’objet.

|Méthode|Description|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fournit un mécanisme d’accès générique pour localiser un service qu’un identifiant unique à l’échelle mondiale (GUID) identifie.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Représente un enfant à interface documentaire multiple (MDI) contenant une ou plusieurs vues de code.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Remplit un cadre de fenêtre.|

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Modification des chiffres](https://www.microsoft.com/download/details.aspx?id=55984)
