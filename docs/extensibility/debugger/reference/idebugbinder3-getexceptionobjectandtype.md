---
title: IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 713d0ba674fc7ab763c04a36353688e790df3924
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887696"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Cette méthode récupère l’exception associée à un objet, le cas échéant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppException`  
 [out] Retourne l’objet qui représente l’exception.  
  
 `ppField`  
 [out] Retourne l’objet qui représente un champ spécifique qui peut avoir provoqué l’exception (Cela peut être une valeur null).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
> [!NOTE]
>  Pour vérifier s’il existe une exception, vérifiez la valeur retournée par `ppException`: Si c’est une valeur null, aucune exception n’est associée à cet objet.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)