---
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28334cc7aa0c8a5587a20d6c9dfdee3133d9ea7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62921788"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Cette interface représente un document source.

## <a name="syntax"></a>Syntaxe

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] en général implémente cette interface. Un moteur de débogage (dé) peut également implémenter cette interface quand il doit fournir le code source et la source n’existe pas sur le disque.  Dans ce cas, le D’implémenterait également [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) et [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) interfaces, ainsi que des méthodes supplémentaires sur le [ IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) et [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) interfaces.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Les méthodes sur le `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, et `IDebugActivateDocumentEvent2` interfaces retournent cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugDocument2`.

|Méthode|Description|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Obtient le nom du document sous plusieurs formes.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Obtient l’identificateur de classe du document.|

## <a name="remarks"></a>Notes
 Cette interface est implémentée uniquement lorsque le DE fournit le code source. Par exemple, lorsque vous déboguez un script sur une page HTML, l’Allemagne fournit le code source, car la source est téléchargée ou générée dynamiquement et n’existe pas comme un fichier de disque. Lors du débogage des langages traditionnels, tels que C++, cette interface est inutile à implémenter.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)