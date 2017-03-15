---
title: "BP_PASSCOUNT_STYLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_PASSCOUNT_STYLE"
helpviewer_keywords: 
  - "Structure BP_PASSCOUNT_STYLE"
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie la condition associée au nombre de passage de point d'arrêt qui provoque le point d'arrêt au demande.  
  
## Syntaxe  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```c#  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## Membres  
 BP\_PASSCOUNT\_NONE  
 Ne spécifie pas de style de nombre de passage de point d'arrêt.  
  
 BP\_PASSCOUNT\_EQUAL  
 Définit le style de nombre de passage de point d'arrêt pour qu'elles correspondent à.  Le point d'arrêt se déclenche lorsque le nombre de fois le point d'arrêt est equals de correspondance le nombre de passage.  
  
 BP\_PASSCOUNT\_EQUAL\_OR\_GREATER  
 Définit le style de nombre de passage de point d'arrêt pour être égal ou supérieur.  Le point d'arrêt se déclenche lorsque le nombre de fois où le point d'arrêt est atteint est égale ou supérieure au nombre de passage.  
  
 BP\_PASSCOUNT\_MOD  
 spécifie un nombre de passage de modulo.  Par exemple, si le nombre de passage est du type `BP_PASSCOUNT_MOD` et la valeur du nombre de exécution est 4, le point d'arrêt se déclenche à chaque fois que le nombre d'accès est un multiple de 4.  
  
## Notes  
 utilisé pour le membre d' `stylePassCount` de la structure de [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) qui est ensuite un membre des structures de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)