---
title: IDebugDocumentInfo::GetDocumentClassId | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetDocumentClassId
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetDocumentClassId
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9e86c42954fafd4135956845f9465629cde9990
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971080"
---
# <a name="idebugdocumentinfogetdocumentclassid"></a>IDebugDocumentInfo::GetDocumentClassId
Retourne un `CLSID` identifiant le type de document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pclsidDocument`  
 [out] Un `CLSID` identifiant le type de document.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet au débogueur IDE pour les visionneuses personnalisées d’hôte pour ce document.  
  
 Si le document n’a pas de données visibles, la valeur de retour de `pclsidDocument` est `CLSID_NULL`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)