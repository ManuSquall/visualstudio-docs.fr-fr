---
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da6b3641a33a19cef01f9a6a4a9a833643169f25
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006565"
---
# <a name="parseflags"></a>PARSEFLAGS
Spécifie comment analyser une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```csharp  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>Membres  
 PARSE_EXPRESSION  
 Indique que l’expression n’est pas une instruction.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Indique que l’expression doit être analysé (et ultérieurement évaluée) en tant qu’adresse.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Indique que l’expression est en cours d’analyse au moment du design (autrement dit, lorsqu’un concepteur est ouvert).  
  
## <a name="remarks"></a>Notes  
 Passé en tant que paramètre à la [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) et [analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) méthodes.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)