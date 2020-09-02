---
title: IDebugStackFrame2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae9cad7102fb9a82deb43b2c8820ef52e77deeed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547001"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un frame de pile unique dans une pile des appels dans un thread particulier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur DE débogage (DE) implémente cette interface pour représenter un frame de pile.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Appelez [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour récupérer une interface [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) . Appelez [Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) pour récupérer une structure [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) qui contient l' `IDebugStackFrame2` interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugStackFrame2` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtient le contexte de code pour ce frame de pile.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtient le contexte de document pour ce frame de pile.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Obtient le nom du frame de pile.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Obtient une description du frame de pile.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Obtient une représentation dépendante de l’ordinateur de la plage d’adresses physiques associée à un frame de pile.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Obtient un contexte d’évaluation pour l’évaluation de l’expression dans le contexte actuel d’un frame de pile et d’un thread.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Obtient la langue associée à un frame de pile.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Obtient une description des propriétés associées à un frame de pile.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Crée un énumérateur pour les propriétés du frame de pile.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Obtient le thread associé à un frame de pile.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est obtenue uniquement lorsque le programme en cours de débogage a été arrêté à un point d’arrêt (provoqué par un point d’arrêt défini par l’utilisateur ou une exception). À partir de cette interface, un contexte d’expression peut être obtenu pour évaluer des expressions, une liste de registres peut être retournée, ou la pile des appels peut être obtenue et examinée.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
