---
title: IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950565"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie si l’exception doit être passée le programme en cours de débogage lors de l’exécution reprend, ou si l’exception doit être ignorée.  
  
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
 [in] Différent de zéro (`TRUE`) si l’exception doit être passée le programme en cours de débogage lors de l’exécution reprend, ou égale à zéro (`FALSE`) si l’exception doit être ignorée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Appel de cette méthode ne provoque pas réellement de code à exécuter dans le programme en cours de débogage. L’appel consiste simplement à définir l’état de la prochaine exécution de code. Par exemple, les appels à la [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) méthode peut retourner `S_OK` avec la [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` champ valeur `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 L’IDE peut recevoir le [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) événement et appelez le [continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md) (méthode). Le moteur de débogage (dé) doit avoir un comportement par défaut pour gérer le cas si le `PassToDebuggee` méthode n’est pas appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
