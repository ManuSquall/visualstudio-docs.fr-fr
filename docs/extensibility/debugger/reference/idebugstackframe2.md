---
title: IDebugStackFrame2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37acb9f2984c36130de494108ef4b76a59cc74e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719514"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Cette interface représente un cadre de pile unique dans une pile d’appels dans un thread particulier.

## <a name="syntax"></a>Syntaxe

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface pour représenter un cadre de pile.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour récupérer une interface [IEnumDebugFrameInfo2.](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) Appelez [ensuite](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) pour récupérer une structure `IDebugStackFrame2` [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) qui contient l’interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugStackFrame2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtient le contexte de code pour ce cadre de pile.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtient le contexte de document pour ce cadre de pile.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Obtient le nom du cadre de pile.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Obtient une description du cadre de pile.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Obtient une représentation dépendante de la machine de la gamme d’adresses physiques associées à un cadre de pile.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Obtient un contexte d’évaluation pour faire l’évaluation d’expression dans le contexte actuel d’un cadre et d’un thread de pile.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Obtient la langue associée à un cadre de pile.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Obtient une description des propriétés associées à un cadre de pile.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Crée un enumérateur pour les propriétés de cadre de pile.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Obtient le fil associé à un cadre de pile.|

## <a name="remarks"></a>Notes
 Cette interface n’est obtenue que lorsque le programme en cours de débopoint a été arrêté à un point d’arrêt (soit causé par un point de rupture de l’utilisateur ou une exception). À partir de cette interface, un contexte d’expression peut être obtenu pour évaluer les expressions, une liste de registres peut être retournée, ou la pile d’appel peut être obtenue et examinée.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
