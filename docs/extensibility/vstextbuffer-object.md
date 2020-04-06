---
title: Objet VSTextBuffer (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ea44d2b22c96d49f334f2ea33f9db8d69b5eb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697723"
---
# <a name="vstextbuffer-object"></a>Objet VSTextBuffer
L’objet tampon de texte représente un flux de texte Unicode, qui est généralement associé à un fichier. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet peut être utilisé en dehors du contexte de l’éditeur de base, comme dans, un assistant.

 Le tableau suivant montre `VSTextBuffer`les interfaces de .

|Méthode|Description|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interface OLE standard. Utilisé pour annuler /refaire la manipulation dans le tampon.|
|[IPersistFile (en)](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Interface OLE standard.|
|[IPersistStream (en)](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Interface OLE standard.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permet la création d’actions composées (c’est-à-dire des actions regroupées en une seule unité dédo/redo).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Permet la persistance des données de documents gérées par le tampon texte.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fournit des services de base; utilisé par de nombreux clients.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Utilisé pour rechercher un tampon.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fournit des capacités de lecture et d’écriture à l’aide de coordonnées bidimensionnelles. Hérite de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fournit des capacités de lecture et d’écriture à l’aide de coordonnées unidimensionnelles. Hérite de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Fournit un accès rapide, orienté flux et séquentiel au texte dans le tampon.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Donne accès à une collection générique de propriétés. La propriété la plus importante est le nom, ou surnom, du tampon. Vous pouvez stocker vos propres données aléatoires dans le tampon avec cette interface en créant un GUID et en l’utilisant comme clé.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Prend en charge les points de connexion pour les événements.|

## <a name="remarks"></a>Notes
 Le `VSTextBuffer` se trouve `QueryInterface` généralement `IVsTextBuffer`par un appel sur . Pour plus d’informations, voir [Tampon texte](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Modification des chiffres](https://www.microsoft.com/download/details.aspx?id=55984)
