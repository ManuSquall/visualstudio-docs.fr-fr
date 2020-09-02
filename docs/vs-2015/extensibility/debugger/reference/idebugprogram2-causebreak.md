---
title: 'IDebugProgram2 :: CauseBreak | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5520d624b2789488c7ab6a5cab353d78d2cd69ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555707"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Demande que le programme arrête l’exécution la prochaine fois qu’un de ses threads tente de s’exécuter.  
  
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
 Un événement [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) est envoyé lorsque le programme tente ensuite d’exécuter du code après l’appel de cette méthode.  
  
 Cette méthode est asynchrone en ce que la méthode retourne immédiatement une valeur sans nécessairement attendre l’arrêt du programme.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
