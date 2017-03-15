---
title: "IDebugStackFrame2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2"
helpviewer_keywords: 
  - "Interface de IDebugStackFrame2"
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente un frame de pile unique dans une pile des appels dans un thread particulier.  
  
## Syntaxe  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 le moteur de débogage \(DE\) implémente cette interface pour représenter un frame de pile.  
  
## Remarques pour les appelants  
 appel [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour extraire une interface d' [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) .  Appel [Suivant](../Topic/IEnumDebugFrameInfo2::Next.md) pour récupérer une structure de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) contenant l'interface d' `IDebugStackFrame2` .  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugStackFrame2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)|obtient le contexte de code pour ce frame de pile.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtient le contexte de le document pour ce frame de pile.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|obtient le nom du frame de pile.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|obtient une description du frame de pile.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Obtient la représentation d'ordinateur\-dépendant de la plage d'adresses physiques associées à un frame de pile.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Obtient un contexte d'évaluation pour effectuer l'évaluation d'une expression dans le contexte actuel d'un frame de pile et d'un thread.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Obtient la langue associé à un frame de pile.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Obtient une description des propriétés associées à un frame de pile.|  
|[EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)|Crée un énumérateur pour les propriétés du frame de pile.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Obtient le thread associé à un frame de pile.|  
  
## Notes  
 Cette interface est obtenue uniquement lorsque le programme débogué a été arrêté par un point d'arrêt \(provoqué par un point d'arrêt utilisateur\-défini ou une exception\).  De cette interface, un contexte d'expression peut être obtenu pour évaluer des expressions, une liste de registres peut être retournée, ou la pile des appels peut être obtenue et analysé.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)