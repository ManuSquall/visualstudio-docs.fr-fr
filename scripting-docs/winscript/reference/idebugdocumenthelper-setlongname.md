---
title: IDebugDocumentHelper::SetLongName | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.SetLongName
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::SetLongName
ms.assetid: b6199e5d-9b54-43a2-9775-214b8d022607
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 153655966f3be59f1d01fd375b8669fb7207e2d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelpersetlongname"></a>IDebugDocumentHelper::SetLongName
Définit le nom long du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetLongName(  
   LPCOLESTR  pszLongName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszLongName`  
 [in] Chaîne terminée par le caractère null qui contient le nom long du document.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode définit un nouveau nom long pour le document.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)