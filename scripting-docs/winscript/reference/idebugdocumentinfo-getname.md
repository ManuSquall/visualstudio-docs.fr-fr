---
title: IDebugDocumentInfo::GetName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f3ecde4fbde1a265596a01d7f0f953763363e797
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097693"
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
 [IDebugDocumentInfo (Interface)](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [Énumération DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)