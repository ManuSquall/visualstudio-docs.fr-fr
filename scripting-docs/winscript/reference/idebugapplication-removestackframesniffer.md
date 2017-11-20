---
title: IDebugApplication::RemoveStackFrameSniffer | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.RemoveStackFrameSniffer
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::RemoveStackFrameSniffer
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11289972dbd39d2e6221fb223a0d933ed90589c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationremovestackframesniffer"></a>IDebugApplication::RemoveStackFrameSniffer
Supprime un fournisseur d’énumérateur de frame de pile de cette application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwCookie`  
 [in] Le cookie retourné par la `AddStackFrameSniffer` méthode lors de l’ajout du fournisseur énumérateur de frame de pile.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Le `RemoveStackFrameSniffer` méthode supprime un fournisseur d’énumérateur de frame de pile de cette application.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)   
 [IDebugApplication (Interface)](../../winscript/reference/idebugapplication-interface.md)   
 [Interface IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)