---
title: PARSEFLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27f0c32c8a432a6aaa0ef83b06d6b424486ce29b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898354"
---
# <a name="parseflags"></a>PARSEFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie comment analyser une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```csharp  
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
 Indique que l’expression doit être analysé (et ultérieurement évaluée) en tant qu’adresse.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Indique que l’expression est en cours d’analyse au moment du design (autrement dit, lorsqu’un concepteur est ouvert).  
  
## <a name="remarks"></a>Notes  
 Passé en tant que paramètre à la [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) et [analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) méthodes.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

