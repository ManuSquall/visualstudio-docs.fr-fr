---
title: Structure JS_NATIVE_FRAME | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: JS_NATIVE_FRAME
apilocation: jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7e93041a6dec767cb3bb11382abfb562068c925
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsnativeframe-structure"></a>Structure JS_NATIVE_FRAME
Représente un frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct {  
    UINT64 InstructionOffset;    UINT64 ReturnOffset;    UINT64 FrameOffset;    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## <a name="members"></a>Membres  
 `InstructionOffset`  
 Le pointeur d’instruction.  
  
 `ReturnOffset`  
 L’adresse de retour.  
  
 `FrameOffset`  
 Le pointeur de frame.  
  
 `StackOffset`  
 Le pointeur de pile.  
  
## <a name="remarks"></a>Remarques  
 Le `JS_NATIVE_FRAME` struct est utilisé par `IJsStackFrameEnumerator`.  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)