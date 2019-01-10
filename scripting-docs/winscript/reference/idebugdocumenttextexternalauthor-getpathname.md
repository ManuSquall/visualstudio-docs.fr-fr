---
title: IDebugDocumentTextExternalAuthor::GetPathName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e17d27a320eac95445c083c718f5abcebbbc46cf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088840"
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