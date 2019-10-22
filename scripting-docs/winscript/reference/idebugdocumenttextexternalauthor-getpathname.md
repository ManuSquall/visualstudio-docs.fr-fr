---
title: 'IDebugDocumentTextExternalAuthor :: GetPathName | Microsoft Docs'
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
ms.openlocfilehash: e876b41ce1bde4defffd11267c6665f9d57da077
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575970"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Retourne le chemin d’accès complet et le nom de fichier du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrLongName`  
 à Chaîne contenant le chemin d’accès complet et le nom de fichier.  
  
 `pfIsOriginalFile`  
 à Valeur booléenne qui indique si le chemin d’accès et le nom de fichier font référence au document d’origine.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Impossible de créer ou de déterminer le fichier source.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le chemin d’accès complet et le nom de fichier du document.  
  
 Si `pfIsOriginalFile` a la valeur FALSe, le chemin d’accès et le nom de fichier dans `pbstrLongName` font référence à un fichier temporaire nouvellement créé.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)