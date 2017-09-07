---
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 4e1fa009437acca5fea3f2854c4cdf389b1c463a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Appelée lorsque le traitement d’une exception interceptée est terminée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInterceptCookie(  
   UINT64* pqwCookie  
);  
```  
  
```csharp  
int GetInterceptCookie(  
   out ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pqwCookie`  
 [out] Valeur unique qui est associé à l’exception qui a été interceptée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Après le [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) méthode terminée à la gestion d’une exception interceptée, elle envoie le [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) événement. Le gestionnaire peut utiliser la `GetInterceptCookie` pour récupérer la valeur unique associée à l’exception (la même valeur passée à la `InterceptCurrentException` méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
