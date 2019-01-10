---
title: IDebugSyncOperation::InProgressAbort | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab8bae7f131d24c1a2c7272dc8d1178e12bf0e6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095522"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Annule une opération en cours d’exécution sur un autre thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|L’opération ne peut pas être annulée.|  
|`E_ABORT`|L’opération n’a pas pu être effectuée.|  
  
## <a name="remarks"></a>Notes  
 Le Gestionnaire de débogage de processus appelle cette méthode à partir du thread de débogueur à annuler une opération qui est en cours dans un autre thread.  
  
 Si le `InProgressAbort` méthode ne peut pas terminer l’opération, elle retourne `E_ABORT` dès que possible. Cette méthode peut retourner `E_NOTIMPL` si l’opération ne peut pas être annulée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)