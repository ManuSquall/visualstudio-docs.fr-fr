---
title: IDebugCanStopEvent2::GetReason | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCanStopEvent2::GetReason
helpviewer_keywords: IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 785fed3d89ab6a351a82a61acbd3f58978a690e5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Obtient la raison pour lesquelles le moteur de débogage (DE) souhaite arrêter.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 [out] Retourne une valeur de la [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) énumération qui décrit la raison de cet événement.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est généralement appelée avant la [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) méthode afin que l’appelant puisse déterminer s’il faut passer différente de zéro (`TRUE`) pour le `IDebugCanStopEvent2::CanStop` (méthode).  
  
 La raison de l’arrêt peut être `CANSTOP_ENTRYPOINT`, ce qui signifie que le D’a atteint un point d’entrée, ou `CANSTOP_STEPIN`, ce qui signifie que le D’a exécuté le code dans une fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)