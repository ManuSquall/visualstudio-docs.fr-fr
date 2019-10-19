---
title: JS_NATIVE_FRAME, structure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_NATIVE_FRAME
apilocation:
- jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0b624229a96cfc2a2d2044a926f45fa91a1c76c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571767"
---
# <a name="js_native_frame-structure"></a>Structure JS_NATIVE_FRAME
Représente un frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef struct {  
    UINT64 InstructionOffset;    UINT64 ReturnOffset;    UINT64 FrameOffset;    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## <a name="members"></a>Membres  
 `InstructionOffset`  
 Pointeur d’instruction.  
  
 `ReturnOffset`  
 Adresse de retour.  
  
 `FrameOffset`  
 Pointeur de frame.  
  
 `StackOffset`  
 Pointeur de pile.  
  
## <a name="remarks"></a>Notes  
 Le struct `JS_NATIVE_FRAME` est utilisé par `IJsStackFrameEnumerator`.  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)