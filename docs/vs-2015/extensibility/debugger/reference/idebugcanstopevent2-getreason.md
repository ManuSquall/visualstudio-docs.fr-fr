---
title: 'IDebugCanStopEvent2 :: GetReason | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 707488abed004adaa75c84f16358bdd8a979eb71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191155"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient la raison pour laquelle le moteur DE débogage (DE) souhaite s’arrêter.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcr`  
 à Retourne une valeur de l’énumération [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) qui décrit la raison de cet événement.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est généralement appelée avant la méthode [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) , de sorte que l’appelant peut déterminer s’il faut passer une valeur différente de zéro ( `TRUE` ) à la `IDebugCanStopEvent2::CanStop` méthode.  
  
 La raison de l’arrêt peut être `CANSTOP_ENTRYPOINT` , ce qui signifie que le de a atteint un point d’entrée, ou `CANSTOP_STEPIN` , ce qui signifie que le de a effectué un pas à pas détaillé dans une fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
