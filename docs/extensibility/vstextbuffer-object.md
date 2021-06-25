---
title: Objet VSTextBuffer | Microsoft Docs
description: L’objet VSTextBuffer représente un flux de texte Unicode, qui est généralement associé à un fichier. Cet article répertorie les interfaces de VSTextBuffer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3660a8dbb4a0a1280d5a3f428f73f3498244af7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905174"
---
# <a name="vstextbuffer-object"></a>Objet VSTextBuffer
L’objet de mémoire tampon de texte représente un flux de texte Unicode, qui est généralement associé à un fichier. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet peut être utilisé en dehors du contexte de l’éditeur de base, comme dans, un Assistant.

 Le tableau suivant répertorie les interfaces de `VSTextBuffer` .

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

## <a name="remarks"></a>Remarques
 `VSTextBuffer`Est généralement trouvé par un `QueryInterface` appel sur `IVsTextBuffer` . Pour plus d’informations, consultez [mémoire tampon de texte](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Modifications des figures](https://www.microsoft.com/download/details.aspx?id=55984)