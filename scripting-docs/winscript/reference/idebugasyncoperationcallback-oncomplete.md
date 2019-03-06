---
title: IDebugAsyncOperationCallBack::onComplete | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4909f469b558ef4664a74c4a7926001d20adc40e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089399"
---
# <a name="idebugasyncoperationcallbackoncomplete"></a>IDebugAsyncOperationCallBack::onComplete
Signale qu’un résultat est disponible à partir d’une opération de débogage asynchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode signale qu’un résultat est disponible à partir d’un `IDebugAsyncOperation` objet. L’événement est déclenché dans le thread de débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAsyncOperationCallBack (Interface)](../../winscript/reference/idebugasyncoperationcallback-interface.md)   
 [Interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)