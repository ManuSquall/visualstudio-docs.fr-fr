---
title: IDebugApplication::AddStackFrameSniffer | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.AddStackFrameSniffer
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::AddStackFrameSniffer
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89faa6481bd5e5934ae2d3b85a0bade83949633a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationaddstackframesniffer"></a>IDebugApplication::AddStackFrameSniffer
Ajoute un fournisseur d’énumérateur de frame de pile pour cette application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdsfs`  
 [in] Le fournisseur d’énumérateur de frame de pile à ajouter à cette application.  
  
 `pdwCookie`  
 [out] Un cookie est utilisé pour supprimer ce fournisseur d’énumérateur de frame de pile de l’application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Bien qu’en règle générale, les moteurs de langue appellent cette méthode pour exposer leurs frames de pile dans le débogueur, il est possible pour d’autres entités exposer les frames de pile.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplication (Interface)](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)   
 [Interface IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)