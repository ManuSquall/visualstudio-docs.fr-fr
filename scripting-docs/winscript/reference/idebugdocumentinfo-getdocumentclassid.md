---
title: 'IDebugDocumentInfo :: GetDocumentClassId | Microsoft Docs'
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
ms.openlocfilehash: 996e6d751807bba1e1a74cbb7e579db25193c32b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569084"
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
 à @No__t_0 identifiant le type de document.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet à l’IDE du débogueur d’héberger des visionneuses personnalisées pour ce document.  
  
 Si le document n’a pas de données affichables, la valeur de retour de `pclsidDocument` est `CLSID_NULL`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)