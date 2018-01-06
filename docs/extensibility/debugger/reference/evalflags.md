---
title: EVALFLAGS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EVALFLAGS
helpviewer_keywords: EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 62b372daffee279c3e36efde53a8b002c8b9b73a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="evalflags"></a>EVALFLAGS
Spécifie des indicateurs qui contrôlent l’évaluation de l’expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```csharp  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>Membres  
 EVAL_RETURNVALUE  
 Spécifie que la valeur renvoyée, le cas échéant, être évaluées.  
  
 EVAL_NOSIDEEFFECTS  
 Spécifie que les effets secondaires ne seront ne pas autorisées.  
  
 EVAL_ALLOWBPS  
 Spécifie l’arrêt sur les points d’arrêt.  
  
 EVAL_ALLOWERRORREPORT  
 Spécifie le rapport d’erreurs à l’hôte pour être autorisée. Principalement utilisé pour l’évaluation d’expression dans le script dans Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Fonctions de force à évaluer en tant qu’adresses, au lieu d’appeler la fonction.  
  
 EVAL_NOFUNCEVAL  
 Fonction empêche d’en cours d’évaluation. Par exemple, considérez la `int` jeton dans l’expression `myExpression(int) + 10`. Cette fonction peut être évaluée correctement en tant qu’adresse, mais pas en tant que valeur.  
  
 EVAL_NOEVENTS  
 Indicateur pour indiquer que les événements qui se produisent pendant l’évaluation d’expression ne doivent pas être envoyées vers le Gestionnaire de session de débogage (SDM) ou à l’IDE.  
  
## <a name="remarks"></a>Notes  
 Ces indicateurs sont passés en tant qu’argument à la [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) et [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) méthodes.  
  
 Ces indicateurs peuvent être combinées avec une opération OR au niveau du bit.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)