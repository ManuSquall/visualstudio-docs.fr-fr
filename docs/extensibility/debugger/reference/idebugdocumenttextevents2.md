---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fc5683e39da2da190468b2cafd0d3accae9b7479
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904012"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Cette interface permet de notifier à Visual Studio les modifications apportées au document source qui sont fournies par le moteur de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour prendre en charge l’apport de modifications au code source. Cette interface est généralement implémentée sur le même objet qui implémente l’interface [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="notes-for-callers"></a>Notes pour les appelants
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Obtient cette interface via un appel à la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> méthode. L' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface est obtenue à partir d’un appel à la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> méthode. L' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface est obtenue en appelant la méthode [QueryInterface](/cpp/atl/queryinterface) sur une interface [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugDocumentTextEvents2` .

|Méthode|Description|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indique que l’intégralité du document a été détruite.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifie le package de débogage que du texte a été inséré dans le document.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifie le package de débogage que du texte a été supprimé du document.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifie le package de débogage que du texte a été remplacé dans le document.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Informe le package de débogage que des attributs de texte ont été mis à jour dans le document.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Avertit le destinataire de l’événement que les attributs du document ont été mis à jour.|

## <a name="remarks"></a>Remarques
 Seuls les moteurs de débogage qui fournissent leurs propres documents tirent parti de l' `IDebugDocumentTextEvent2` interface. Par exemple, un moteur de débogage de script. Dans le processus d’interprétation des scripts, il est possible de générer un nouveau code source qui n’est présent dans aucun fichier disque et qui est connu uniquement du DE.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
