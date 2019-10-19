---
title: 'IDebugApplication :: GetBreakFlags | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.GetBreakFlags
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::GetBreakFlags
ms.assetid: 0532ba94-f791-46ad-88ae-5f6ba220b667
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a614429ebb8cc9271a0444536d14c45b69a9588f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574975"
---
# <a name="idebugapplicationgetbreakflags"></a>IDebugApplication::GetBreakFlags
Retourne les indicateurs d’arrêt actuels de l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetBreakFlags(  
   APPBREAKFLAGS*                   pabf,  
   IRemoteDebugApplicationThread**  pprdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pabf`  
 à Indicateurs d’arrêt actuels de l’application.  
  
 `pprdatSteppingThread`  
 à Thread en cours d’exécution.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne les indicateurs d’arrêt actuels de l’application.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [Énumération APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)