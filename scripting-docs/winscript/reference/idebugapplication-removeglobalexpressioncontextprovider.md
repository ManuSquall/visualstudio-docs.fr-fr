---
title: 'IDebugApplication :: RemoveGlobalExpressionContextProvider | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveGlobalExpressionContextProvider
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveGlobalExpressionContextProvider
ms.assetid: ace638a3-ed34-4d20-8404-45c684aaaf1a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4b948cea02d696b6c176e925adf9c95913be2cd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571142"
---
# <a name="idebugapplicationremoveglobalexpressioncontextprovider"></a>IDebugApplication::RemoveGlobalExpressionContextProvider
Supprime un fournisseur de contexte d’expression globale de cette application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT RemoveGlobalExpressionContextProvider(  
   DWORD_PTR  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwCookie`  
 dans Cookie retourné par la méthode `AddGlobalExpressionContextProvider` lors de l’ajout du fournisseur de contexte global.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 La méthode `RemoveGlobalExpressionContextProvider` supprime un fournisseur de contexte d’expression globale de cette application.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplication :: AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)    
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)