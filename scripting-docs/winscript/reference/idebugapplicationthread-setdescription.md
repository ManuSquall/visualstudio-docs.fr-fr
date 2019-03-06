---
title: IDebugApplicationThread::SetDescription | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SetDescription
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SetDescription
ms.assetid: 084e5b74-af95-41b4-ae55-01f6f4d22168
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d1e1efc44b6e7f2a7d0bb3bf2de1a492c6793c8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089854"
---
# <a name="idebugapplicationthreadsetdescription"></a>IDebugApplicationThread::SetDescription
Définit la description de ce thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetDescription(  
   LPCOLESTR  pstrDescription  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrDescription`  
 [in] Description de ce thread.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode définit la description de ce thread.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)