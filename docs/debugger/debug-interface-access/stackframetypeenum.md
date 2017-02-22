---
title: "StackFrameTypeEnum | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "StackFrameTypeEnum (énumération)"
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Spécifie le type du frame de pile.  
  
## Syntaxe  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## Éléments  
 `FrameTypeFPO`  
 pointeur de frame omis ; Les informations de FPO.  
  
 `FrameTypeTrap`  
 Frame d'interruption du noyau.  
  
 `FrameTypeTSS`  
 Frame d'interruption du noyau.  
  
 `FrameTypeStandard`  
 Frame de pile standard EBP.  
  
 `FrameTypeFrameData`  
 pointeur de frame omis ; Les informations sur les données du mode disponibles.  
  
 `FrameTypeUnknown`  
 Vue qui n'a pas d'informations de débogage.  
  
## Notes  
 Les valeurs de cette énumération sont retournées par un appel à la méthode d' [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .  
  
## Configuration requise  
 en\-tête : cvconst.h  
  
## Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)