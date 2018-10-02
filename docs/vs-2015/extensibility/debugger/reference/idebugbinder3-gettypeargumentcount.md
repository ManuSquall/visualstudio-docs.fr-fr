---
title: IDebugBinder3::GetTypeArgumentCount | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder3::GetTypeArgumentCount
helpviewer_keywords:
- IDebugBinder3::GetTypeArgumentCount method
ms.assetid: caf68de6-6f7c-4efd-b803-121347a5032e
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: adeb207f0063d39144b076a195641de192967187
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503367"
---
# <a name="idebugbinder3gettypeargumentcount"></a>IDebugBinder3::GetTypeArgumentCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugBinder3::GetTypeArgumentCount](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder3-gettypeargumentcount).  
  
Cette méthode retourne le nombre de types d’arguments associée à cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeArgumentCount(  
   UINT* uCount  
);  
```  
  
```csharp  
int GetTypeArgumentCount(  
   out uint uCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `uCount`  
 [out] Nombre de types d’arguments associée à cet objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 La valeur retournée par cette méthode peut être utilisée pour allouer un tableau pour une utilisation avec le [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)

