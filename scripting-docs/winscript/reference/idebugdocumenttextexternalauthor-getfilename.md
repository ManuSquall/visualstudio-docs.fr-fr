---
title: 'IDebugDocumentTextExternalAuthor :: GetFileName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetFileName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetFileName
ms.assetid: 87acdce6-acb2-4936-80dd-d624bb7dbd42
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c07752d357a261fbc4800c3217a63d3de9489d55
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575975"
---
# <a name="idebugdocumenttextexternalauthorgetfilename"></a>IDebugDocumentTextExternalAuthor::GetFileName
Retourne le nom du document sans informations de chemin d’accès.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrShortName`  
 à Chaîne contenant le nom abrégé du document.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le nom du document sans informations de chemin d’accès. Le nom abrégé est généralement utilisé dans les boîtes de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)