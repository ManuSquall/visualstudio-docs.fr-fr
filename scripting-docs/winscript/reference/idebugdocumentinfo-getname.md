---
title: IDebugDocumentInfo::GetName | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentInfo.GetName
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da369c328c2f92915c60b1c50517938bf76d5202
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Retourne le nom de document spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dnt`  
 [in] Le type de nom du document à retourner.  
  
 `pbstrName`  
 [out] Chaîne contenant le nom.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Le nom de document spécifié n’est pas connu.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode retourne le nom de document spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentInfo (Interface)](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [Énumération DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)