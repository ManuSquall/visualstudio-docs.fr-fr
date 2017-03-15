---
title: "BP_COND_STYLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_COND_STYLE"
helpviewer_keywords: 
  - "Énumération de BP_COND_STYLE"
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie le style de condition de point d'arrêt pour les points d'arrêt en attente et liés.  
  
## Syntaxe  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```c#  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## Membres  
 BP\_COND\_NONE  
 Déclenche le point d'arrêt lorsque la position du point d'arrêt est arrêtée.  aucune condition de point d'arrêt spécifiée.  
  
 BP\_COND\_WHEN\_TRUE  
 Déclenche le point d'arrêt uniquement lorsque l'expression conditionnelle associée au point d'arrêt a la `true`.  
  
 BP\_COND\_WHEN\_CHANGED  
 Déclenche le point d'arrêt uniquement lorsque la valeur de l'expression conditionnelle associée au point d'arrêt a changé de son évaluation précédente.  
  
## Notes  
 utilisé pour le membre d' `styleCondition` de la structure de [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)