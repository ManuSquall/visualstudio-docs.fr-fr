---
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6069b7c77995a855bfa47d1d369203f386b0302c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686871"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Cette interface représente un document texte.

## <a name="syntax"></a>Syntaxe

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Un moteur de débogage (dé) implémente cette interface lorsque le code source, qu'il doit fournir se présente sous forme de texte. Puisqu’il s’agit du cas le plus classique, si un D’implémente le [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface, elle doit également implémenter le `IDebugDocumentText2` interface.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Utilisez le `QueryInterface` méthode pour obtenir cette interface à partir d’un `IDebugDocument2` interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes sur le `IDebugDocument2` interface, cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Récupère la taille du texte à cette position dans le document.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Récupère le texte à partir de la position spécifiée dans le document.|

## <a name="remarks"></a>Notes
 Un objet qui implémente cette interface doit également implémenter le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface, qui fournit le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface pour un [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) objet.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)