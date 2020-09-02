---
title: 'IDebugEngine2 :: CauseBreak | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b6e52e4885a61c3fe04fff5bdcca08fd00cf460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198485"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Demande que tous les programmes débogués par ce moteur de débogage (DE) interrompent l’exécution lors de la prochaine tentative d’exécution de l’un de leurs threads.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est asynchrone : un événement [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) est envoyé lorsque le programme tente ensuite de s’exécuter après l’appel de cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
