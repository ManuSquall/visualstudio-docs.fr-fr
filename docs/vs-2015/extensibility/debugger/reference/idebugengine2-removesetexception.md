---
title: IDebugEngine2::RemoveSetException | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53ba8c9c1934ee1c036e14fb51abd5babcf7e4c5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949783"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Supprime l’exception spécifiée, donc il n’est n’est plus géré par le moteur de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 L’exception en cours de suppression doit avoir été précédemment définie par un appel antérieur à la [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) (méthode).  
  
 Pour supprimer toutes les exceptions de jeu à la fois, appelez le [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
