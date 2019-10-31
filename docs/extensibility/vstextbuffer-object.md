---
title: Objet VSTextBuffer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1895efa9ef10e1e554b98844619507224f09126
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189028"
---
# <a name="vstextbuffer-object"></a>Objet VSTextBuffer
L’objet de mémoire tampon de texte représente un flux de texte Unicode, qui est généralement associé à un fichier. Un objet <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> peut être utilisé en dehors du contexte de l’éditeur de base, comme dans, un Assistant.

 Le tableau suivant répertorie les interfaces de `VSTextBuffer`.

|Méthode|Description|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interface OLE standard. Utilisé pour la gestion des opérations d’annulation et de rétablissement dans la mémoire tampon.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Interface OLE standard.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Active la création d’actions de composants (c’est-à-dire des actions regroupées en une seule unité d’annulation ou de restauration par progression).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Active la persistance des données de document gérées par la mémoire tampon de texte.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fournit des services de base. utilisé par de nombreux clients.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Utilisé pour rechercher une mémoire tampon.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fournit des fonctionnalités de lecture et d’écriture à l’aide de coordonnées à deux dimensions. Hérite de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fournit des fonctionnalités de lecture et d’écriture à l’aide de coordonnées unidimensionnelles. Hérite de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Fournit un accès séquentiel rapide et orienté flux à du texte dans la mémoire tampon.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fournit l’accès à une collection générique de propriétés. La propriété la plus importante est le nom ou le moniker de la mémoire tampon. Vous pouvez stocker vos propres données aléatoires dans la mémoire tampon avec cette interface en créant un GUID et en l’utilisant comme clé.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Prend en charge les points de connexion pour les événements.|

## <a name="remarks"></a>Notes
 Le `VSTextBuffer` est généralement trouvé par un appel de `QueryInterface` sur `IVsTextBuffer`. Pour plus d’informations, consultez [mémoire tampon de texte](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Modifications des figures](https://www.microsoft.com/download/details.aspx?id=55984)