---
title: IDebugDocument2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c959c018dd4da0ff088c4fb52c0420de83b4eac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731991"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Cette interface représente un document source.

## <a name="syntax"></a>Syntaxe

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]implémente généralement cette interface. Un moteur de débogé (DE) peut également implémenter cette interface lorsqu’il a besoin de fournir le code source et la source n’existe pas sur le disque.  Dans de tels cas, le DE implémenterait également les interfaces [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) et [IDebugActivateDocumentEvent2,](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) ainsi que quelques méthodes supplémentaires sur les interfaces [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) et [IDebugDocumentPosition2.](../../../extensibility/debugger/reference/idebugdocumentposition2.md)

## <a name="notes-for-callers"></a>Notes pour les appelants
 Méthodes sur `IDebugDocumentContext2` `IDebugDisassemblyStream2`le `IDebugDocumentPosition2`, `IDebugActivateDocumentEvent2` , et les interfaces retournent cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugDocument2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Obtient le nom du document sous l’une de plusieurs formes.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Obtient l’identifiant de classe du document.|

## <a name="remarks"></a>Notes
 Cette interface n’est implémentée que lorsque le DE fournit le code source. Par exemple, lorsque vous débogagez le script sur une page HTML, le DE fournit le code source parce que la source est téléchargée ou générée de manière dynamique et n’existe pas sous forme de fichier disque. Lors de la débogage des langues traditionnelles, telles que le C, cette interface n’a pas besoin d’être implémentée.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
