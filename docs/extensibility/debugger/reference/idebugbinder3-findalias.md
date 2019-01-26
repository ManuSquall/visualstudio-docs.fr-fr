---
title: IDebugBinder3::FindAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee84291be79127af4ded052f9c16e17f426bd134
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026435"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Cette méthode localise un alias, étant donné un nom. Il recherche tous les alias dans le programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcstrName`  
 [in] Nom d’alias à rechercher.  
  
 `ppAlias`  
 [out] Alias trouvé (le cas échéant) représenté par le [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interface.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` (si l’alias n’est pas trouvée) ou un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode initialise l’objet de destination à null avant d’appeler ; Il vérifie ensuite une valeur null par la suite déterminer si l’alias a été trouvé.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)