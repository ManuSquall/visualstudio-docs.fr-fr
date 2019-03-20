---
title: IDebugDocumentTextExternalAuthor::GetPathName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5739e7cb0cb12661ee5683051fb7b687e62dfde4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156292"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Retourne le chemin d’accès et le nom complet du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrLongName`  
 [out] Chaîne contenant le chemin d’accès et le nom complet.  
  
 `pfIsOriginalFile`  
 [out] Valeur booléenne qui indique si le chemin d’accès et nom de fichier fait référence au document d’origine.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Le fichier source ne peut pas être créé ou déterminé.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le chemin d’accès et le nom complet du document.  
  
 Si `pfIsOriginalFile` est FALSE, le chemin d’accès et nom de fichier dans `pbstrLongName` font référence à un fichier temporaire qui vient d’être créé.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)