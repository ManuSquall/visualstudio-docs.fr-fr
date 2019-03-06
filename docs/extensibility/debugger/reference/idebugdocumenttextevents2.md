---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e24568d307db694d30a5e87630f47f764a036427
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681723"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Cette interface est utilisée pour notifier Visual Studio sur les modifications apportées au document source qui sont fournies par le moteur de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le D’implémente cette interface pour prendre en charge d’apporter des modifications au code source. Cette interface est généralement implémentée sur le même objet qui implémente le [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Obtient cette interface via un appel à la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> (méthode). Le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface est obtenue à partir d’un appel à la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> (méthode). Le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface est obtenue en appelant le [QueryInterface](/cpp/atl/queryinterface) méthode sur un [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugDocumentTextEvents2`.

|Méthode|Description|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indique que la totalité du document a été détruit.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Informe le package de débogage que le texte a été inséré dans le document.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Informe le package de débogage que le texte a été supprimé à partir du document.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Informe le package de débogage que le texte a été remplacé dans le document.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Informe le package de débogage que les attributs de texte ont été mis à jour dans le document.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifie le récepteur de l’événement que les attributs de document ont été mis à jour.|

## <a name="remarks"></a>Notes
 Uniquement les moteurs de débogage qui fournissent leurs propres documents bénéficie de la `IDebugDocumentTextEvent2` interface. Un exemple de ce serait un moteur de débogage de script. En cours d’interprétation des scripts, nouveau code source peut être générée qui n’est pas présent dans n’importe quel fichier de disque et est connue uniquement de l’Allemagne.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)