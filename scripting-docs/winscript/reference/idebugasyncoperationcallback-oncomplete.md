---
title: 'IDebugAsyncOperationCallBack :: onComplete | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperationCallBack.onComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugAsyncOperationCallBack::onComplete
ms.assetid: d4023f5a-41f9-4948-b0dc-3317d61bb783
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a15ae57d64d2b1e7be867c20e9683e4aaa415974
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573233"
---
# <a name="idebugasyncoperationcallbackoncomplete"></a>IDebugAsyncOperationCallBack::onComplete
Signale qu’un résultat est disponible à partir d’une opération de débogage asynchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode signale qu’un résultat est disponible à partir d’un objet `IDebugAsyncOperation`. L’événement se déclenche dans le thread du débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugAsyncOperationCallBack](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
 [Interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)