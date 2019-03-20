---
title: IDebugDocumentHost::GetFileName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetFileName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetFileName
ms.assetid: b814a848-8a3d-468d-9282-c5c0354b22a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511cdb40a5bb0f885fed8b811a095e7a53a8bb6f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154346"
---
# <a name="idebugdocumenthostgetfilename"></a>IDebugDocumentHost::GetFileName
Retourne le nom du document sans informations de chemin d’accès.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrShortName`  
 [out] Chaîne contenant le nom court du document.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le nom court du document sans informations de chemin d’accès. Le nom court est généralement utilisé dans des situations telles que la **Enregistrer sous...**  boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)