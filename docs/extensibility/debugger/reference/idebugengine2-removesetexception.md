---
title: IDebugEngine2::RemoveSetException | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::RemoveSetException
helpviewer_keywords: IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba231a0545bc1e94e8cf793194efb27962d8e137
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Supprime l’exception spécifiée afin qu’il n’est n’est plus géré par le moteur de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemoveSetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```csharp  
int RemoveSetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pException`  
 [in] Un [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) structure qui décrit l’exception à supprimer.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 L’exception en cours de suppression doit avoir été précédemment définie par un appel précédent à la [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) (méthode).  
  
 Pour supprimer toutes les exceptions de jeu en une seule fois, appelez le [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)