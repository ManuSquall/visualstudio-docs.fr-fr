---
title: IDebugDocumentTextEvents2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a1736890ac78e7aaf20b4a639b1794fc63b5ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731367"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Cette interface est utilisée pour informer Visual Studio des modifications apportées au document source qui sont fournis par le moteur de débogé.

## <a name="syntax"></a>Syntaxe

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour prendre en charge l’apport de modifications au code source. Cette interface est généralement implémentée sur le même objet qui implémente l’interface [IDebugDocument2.](../../../extensibility/debugger/reference/idebugdocument2.md)

## <a name="notes-for-callers"></a>Notes pour les appelants
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]obtient cette interface par un <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> appel à la méthode. L’interface <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> est obtenue à <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> partir d’un appel à la méthode. L’interface <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> est obtenue en appelant la méthode [QueryInterface](/cpp/atl/queryinterface) sur une interface [IDebugDocument2.](../../../extensibility/debugger/reference/idebugdocument2.md)

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugDocumentTextEvents2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indique que l’ensemble du document a été détruit.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Informe le paquet de déboise que le texte a été inséré dans le document.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Informe le paquet de débogé que le texte a été supprimé du document.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Informe le paquet de déboise que le texte a été remplacé dans le document.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Informe le paquet de débogé que les attributs de texte ont été mis à jour dans le document.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Informe le destinataire de l’événement que les attributs du document ont été mis à jour.|

## <a name="remarks"></a>Notes
 Seuls les moteurs débbug qui fournissent leurs `IDebugDocumentTextEvent2` propres documents profiteraient de l’interface. Un exemple de ceci serait un moteur de débogé de script. Dans le processus d’interprétation des scripts, nouveau code source peut être généré qui n’est pas présent dans n’importe quel fichier de disque et est connu uniquement de la DE.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
