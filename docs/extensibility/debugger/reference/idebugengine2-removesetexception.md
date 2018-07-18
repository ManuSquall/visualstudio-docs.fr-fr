---
title: IDebugEngine2::RemoveSetException | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 664111f28ef23e6bf78fc96f26808d1b7ccb7a85
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106313"
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
  
## <a name="remarks"></a>Notes  
 L’exception en cours de suppression doit avoir été précédemment définie par un appel précédent à la [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) (méthode).  
  
 Pour supprimer toutes les exceptions de jeu en une seule fois, appelez le [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)