---
title: IDebugExceptionEvent2 ::P assToDebuggee | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecc7eb3830522cdee0022f4193482daab3780230
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150397"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie si l’exception doit être passée au programme en cours de débogage au moment de la reprise de l’exécution ou si l’exception doit être ignorée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fPass`  
 dans Différent de zéro ( `TRUE` ) si l’exception doit être passée au programme en cours de débogage au moment de la reprise de l’exécution, ou zéro ( `FALSE` ) si l’exception doit être ignorée.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 L’appel de cette méthode n’entraîne en fait pas l’exécution du code dans le programme en cours de débogage. L’appel consiste simplement à définir l’État pour la prochaine exécution du code. Par exemple, les appels à la méthode [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) peuvent retourner `S_OK` avec l' [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` champ défini sur `EXCEPTION_STOP_SECOND_CHANCE` .  
  
 L’IDE peut recevoir l’événement [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) et appeler la méthode [continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) . Le moteur DE débogage (DE) doit avoir un comportement par défaut pour gérer le cas si la `PassToDebuggee` méthode n’est pas appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
