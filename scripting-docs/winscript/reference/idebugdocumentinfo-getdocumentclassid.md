---
title: IDebugDocumentInfo::GetDocumentClassId | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetDocumentClassId
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetDocumentClassId
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be3d29cf19752da18b76f31b4d12cecb05592c00
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentinfogetdocumentclassid"></a>IDebugDocumentInfo::GetDocumentClassId
Retourne un `CLSID` identifiant le type de document.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pclsidDocument`  
 [out] A `CLSID` identifiant le type de document.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode permet au débogueur IDE de visionneuses personnalisées d’hôte pour ce document.  
  
 Si le document n’a pas de données visibles, la valeur de retour de `pclsidDocument` est `CLSID_NULL`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)