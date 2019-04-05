---
title: Structure JS_NATIVE_FRAME | Microsoft Docs
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
ms.openlocfilehash: 9a0777cf42b9ed9412602cb34ed2d521deca1fb9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150112"
---
# <a name="jsnativeframe-structure"></a>Structure JS_NATIVE_FRAME
Représente un frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
  
## <a name="remarks"></a>Notes  
 Le `JS_NATIVE_FRAME` struct est utilisé par `IJsStackFrameEnumerator`.  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)