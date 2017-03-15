---
title: "IDebugReference2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2"
helpviewer_keywords: 
  - "Interface de IDebugReference2"
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugReference2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente une référence à une propriété de frame de pile ou une autre propriété.  
  
> [!NOTE]
>  `IDebugReference2` est réservé à une utilisation ultérieure, et toutes ses méthodes doivent retourner `E_NOTIMPL`.  
  
## Syntaxe  
  
```  
IDebugReference2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface pour représenter une référence à un type particulier de valeur.  Par exemple, la valeur peut être une valeur numérique à la suite d'une évaluation de l'expression, d'un contexte de mémoire utilisé pour restituer la mémoire, ou d'une liste de registres et de leurs valeurs.  
  
## Remarques pour les appelants  
 appel [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) pour obtenir cette interface.  [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) et [GetDerivedMostReference](../Topic/IDebugReference2::GetDerivedMostReference.md) retournent également cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugReference2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|obtient la structure de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) qui décrit cette référence.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|définit la valeur de cette référence d'une chaîne.|  
|[SetValueAsReference](../Topic/IDebugReference2::SetValueAsReference.md)|définit la valeur de cette référence d'une autre référence.|  
|[EnumChildren](../Topic/IDebugReference2::EnumChildren.md)|énumère les enfants de cette référence.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|obtient le parent de cette référence.|  
|[GetDerivedMostReference](../Topic/IDebugReference2::GetDerivedMostReference.md)|Obtient la référence la plus dérivée de cette référence.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Obtient les octets de mémoire auxquels cette référence fait référence.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|obtient un contexte de mémoire pour cette référence.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|obtient la taille, en octets, de cette référence.|  
|[SetReferenceType](../Topic/IDebugReference2::SetReferenceType.md)|définit ce type référence.|  
|[Comparer](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Compare cette référence avec les autres.|  
  
## Notes  
  
> [!NOTE]
>  Cette utilisation de « propriété » ne doit pas être confondue avec cette signification une variable membre d'une classe, bien qu' `IDebugReference2` puisse représenter une telle entité.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) représente une propriété, tandis que `IDebugReference2` représente une référence à une propriété, en général une référence à un objet dans le programme débogué.  
  
 La différence entre une propriété et une référence est qu'une propriété fait référence à une instance nommée d'un objet, tandis que une référence fait référence à une instance sans nom.  Par exemple, une propriété peut faire référence à un objet dans le tas du programme par `"a.b"`.  Une autre propriété peut faire référence au même objet qu' `"c.d"`.  La façon dont de référence à cette propriété nécessite cet `"a.b"` ou `"c.d"` est placé dans la portée.  Une référence à l'objet en question est inconnue ; l'objet peut être désigné comme la mémoire pour cet objet est valide.  
  
 une interface d' `IDebugProperty2` peut être considérée comme valeur avec un nom, un type, et une adresse.  `IDebugReference2`, en revanche, peut être considéré comme un type et une adresse.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)