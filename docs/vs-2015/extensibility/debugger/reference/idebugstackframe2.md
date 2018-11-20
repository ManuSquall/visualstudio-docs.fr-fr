---
title: IDebugStackFrame2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bc6a6ea1b1d864c3f14158b9687181e6bdb6bc4a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816663"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un frame de pile dans une pile des appels dans un thread particulier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le moteur de débogage (dé) implémente cette interface pour représenter un frame de pile.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
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
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Obtient un contexte d’évaluation qui permet d’effectuer l’évaluation de l’expression dans le contexte actuel d’un frame de pile et le thread.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Obtient la langue associée à un frame de pile.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Obtient une description des propriétés associées à un frame de pile.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Crée un énumérateur pour la pile de propriétés du cadre.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Obtient le thread associé à un frame de pile.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est obtenue uniquement lorsque le programme en cours de débogage a été arrêté à un point d’arrêt (soit provoqué par un point d’arrêt défini par l’utilisateur ou une exception). À partir de cette interface, un contexte de l’expression peut être obtenu pour évaluer des expressions, une liste de registres peut être retournée ou la pile des appels peut être obtenue et examinée.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)

