---
title: IDebugSyncOperation::InProgressAbort | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugSyncOperation.InProgressAbort
apilocation: jscript.dll
helpviewer_keywords: IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df0b0ca1d775d4d99e1da5f88a207bd4f78f99b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Annule une opération en cours d’exécution sur un autre thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|L’opération ne peut pas être annulée.|  
|`E_ABORT`|L’opération n’a pas pu aboutir.|  
  
## <a name="remarks"></a>Remarques  
 Le Gestionnaire de déboguer des processus appelle cette méthode à partir du thread de débogueur à annuler une opération est en cours d’exécution dans un autre thread.  
  
 Si le `InProgressAbort` méthode ne peut pas terminer l’opération, il retourne `E_ABORT` dès que possible. Cette méthode peut retourner `E_NOTIMPL` si l’opération ne peut pas être annulée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)