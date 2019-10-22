---
title: 'IDebugApplication :: AddGlobalExpressionContextProvider | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.AddGlobalExpressionContextProvider
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::AddGlobalExpressionContextProvider
ms.assetid: 35db7124-6970-4e45-8f00-ecdf21e9f5cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 429e87def1e17a6abac92ce2d3538960659cfaeb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573475"
---
# <a name="idebugapplicationaddglobalexpressioncontextprovider"></a>IDebugApplication::AddGlobalExpressionContextProvider
Ajoute un fournisseur de contexte d’expression globale à cette application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddGlobalExpressionContextProvider(  
   IProvideExpressionContexts*  pdsfs,  
   DWORD_PTR*                   pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdsfs`  
 dans Fournisseur de contexte global à ajouter à cette application.  
  
 `pdwCookie`  
 à Cookie utilisé pour supprimer ce fournisseur de contexte d’expression globale de l’application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode ajoute un fournisseur de contexte d’expression global à cette application.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)