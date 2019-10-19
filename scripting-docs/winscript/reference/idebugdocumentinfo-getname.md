---
title: 'IDebugDocumentInfo :: GetName | Microsoft Docs'
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
ms.openlocfilehash: bc098da29367a322bd93b4f60ba0e090aee9ee91
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570960"
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
 dans Type de nom de document à retourner.  
  
 `pbstrName`  
 à Chaîne contenant le nom.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Le nom de document spécifié n’est pas connu.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le nom de document spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)  
 [Énumération DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)