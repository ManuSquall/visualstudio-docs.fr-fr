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
ms.openlocfilehash: 68eaa04da057d514a833b86efd1fd08ea807fe6e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187544"
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

