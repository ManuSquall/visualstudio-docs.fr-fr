---
title: IDebugDocumentInfo::GetName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9975563c27b986190fbd2731c3f36b1e32719c0b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160324"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Retourne le nom de document spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Le nom de document spécifié n’est pas connu.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le nom de document spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentInfo Interface](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [Énumération DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)