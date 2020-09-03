---
title: IDebugDisassemblyStream2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98ba08e4ec32aceaf6c265714848939cc6ad9c66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732043"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Cette interface représente un flux d’instructions.

## <a name="syntax"></a>Syntaxe

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un moteur de débogage implémente cette interface pour prendre en charge le désassemblage du code d’un programme.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à la méthode [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) retourne cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugDisassemblyStream2` .

|Méthode|Description|
|------------|-----------------|
|[Lire](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Lit les instructions à partir de la position actuelle dans le flux de code machine.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Déplace le pointeur de lecture dans le flux de code machine un nombre d’instructions donné par rapport à une position spécifiée.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Retourne un identificateur d’emplacement du code pour un contexte de code particulier.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Retourne un objet de contexte de code correspondant à un identificateur d’emplacement de code spécifié.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Retourne un identificateur d’emplacement du code qui représente l’emplacement du code actuel.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Obtient le document source associé à ce flux de code machine.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Obtient la portée de ce flux de code machine.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Obtient la taille de ce flux de code machine.|

## <a name="remarks"></a>Notes
 Le flux de code machine peut être créé pour représenter la totalité de l’espace d’adressage ou simplement une fonction ou un module dans l’espace. Chaque instruction est représentée par une structure [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) retournée par un appel à la méthode [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
