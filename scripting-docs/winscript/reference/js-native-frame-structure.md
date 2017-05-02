---
title: "Structure JS_NATIVE_FRAME | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_NATIVE_FRAME
apilocation: jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Structure JS_NATIVE_FRAME
Représente un frame de pile.  
  
## Syntaxe  
  
```  
typedef struct {  
    UINT64 InstructionOffset;  
    UINT64 ReturnOffset;  
    UINT64 FrameOffset;  
    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## Membres  
 `InstructionOffset`  
 Le pointeur d'instruction.  
  
 `ReturnOffset`  
 L'adresse de retour.  
  
 `FrameOffset`  
 Le pointeur de frame.  
  
 `StackOffset`  
 Le pointeur de pile.  
  
## Notes  
 La structure `JS_NATIVE_FRAME` est utilisée par `IJsStackFrameEnumerator`.  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)