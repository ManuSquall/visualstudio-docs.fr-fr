---
title: IDebugStackFrame2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: efa6c917e5a59c291d07757b52fab4fe8aa7b0ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Cette interface représente un frame de pile dans une pile des appels dans un thread particulier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter un frame de pile.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour récupérer un [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interface. Appelez [suivant](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) pour récupérer un [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structure qui contient le `IDebugStackFrame2` interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugStackFrame2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtient le contexte de code pour ce frame de pile.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtient le contexte de document pour ce frame de pile.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Obtient le nom du frame de pile.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Obtient une description du frame de pile.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Obtient une représentation sous forme de dépendantes de l’ordinateur de la plage d’adresses physiques associés à un frame de pile.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Obtient un contexte d’évaluation pour effectuer l’évaluation de l’expression dans le contexte actuel d’un frame de pile et d’un thread.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Obtient le langage associé à un frame de pile.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Obtient une description des propriétés associées à un frame de pile.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Crée un énumérateur pour la pile de propriétés du cadre.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Obtient le thread associé à un frame de pile.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est obtenue uniquement lorsque le programme débogué a été arrêté à un point d’arrêt (provoqué par un point d’arrêt défini par l’utilisateur ou d’une exception). À partir de cette interface, contexte d’une expression peut être obtenu pour évaluer des expressions, une liste de registres peut être retournée ou la pile des appels peut être obtenue et examinée.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)