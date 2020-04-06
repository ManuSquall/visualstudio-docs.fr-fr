---
title: IDebugDisassemblyStream2 - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732043"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Cette interface représente un flux d’instructions.

## <a name="syntax"></a>Syntaxe

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un moteur de débogé implémente cette interface pour soutenir le démontage du code d’un programme.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à la méthode [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) renvoie cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugDisassemblyStream2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Lire](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Lit les instructions à partir de la position actuelle dans le flux de démontage.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Déplace le pointeur de lecture dans le flux démontage un nombre donné d’instructions par rapport à une position spécifiée.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Renvoie un identifiant de localisation de code pour un contexte de code particulier.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Renvoie un objet de contexte de code correspondant à un identifiant de localisation de code spécifié.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Renvoie un identifiant de localisation de code qui représente l’emplacement actuel du code.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Obtient le document source associé à ce flux de démontage.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Obtient la portée de ce flux démonté.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Obtient la taille de ce flux démonté.|

## <a name="remarks"></a>Notes
 Le flux démontage peut être créé pour représenter l’espace d’adresse entier ou simplement une fonction ou un module dans l’espace. Chaque instruction est représentée par une structure [de démonmblyData](../../../extensibility/debugger/reference/disassemblydata.md) retournée par un appel à la méthode [Lire.](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
