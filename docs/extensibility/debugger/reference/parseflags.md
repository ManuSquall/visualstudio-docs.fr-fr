---
title: PARSEFLAGS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 04cf02cc21fd6ae7324267805e89b1454566b9b6
ms.lasthandoff: 02/22/2017

---
# <a name="parseflags"></a>PARSEFLAGS
Indique comment analyser une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```c#  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>Membres  
 PARSE_EXPRESSION  
 Indique que l’expression n’est pas une instruction.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Indique que l’expression doit être analysée (et ultérieurement évaluée) en tant qu’adresse.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Indique que l’expression est analysée au moment du design (autrement dit, lorsqu’un concepteur est ouvert).  
  
## <a name="remarks"></a>Remarques  
 Passé en tant que paramètre à la [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) et [analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) méthodes.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Analyse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
