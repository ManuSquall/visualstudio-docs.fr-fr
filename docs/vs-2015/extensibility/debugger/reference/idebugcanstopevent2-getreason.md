---
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
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
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d34802ccf4abe16d4fc6b7428405dd89558b5f6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795282"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient la raison pour laquelle le moteur de débogage (dé) veut arrêter de raison.  
  
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
 [out] Retourne une valeur de la [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) énumération qui décrit la raison de cet événement.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est généralement appelée avant la [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) méthode afin que l’appelant puisse déterminer s’il faut passer zéro (`TRUE`) pour le `IDebugCanStopEvent2::CanStop` (méthode).  
  
 La raison de l’arrêt peut être `CANSTOP_ENTRYPOINT`, ce qui signifie que l’Allemagne a atteint un point d’entrée, ou `CANSTOP_STEPIN`, ce qui signifie que l’Allemagne a exécuté le code dans une fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)

