---
title: IActiveScriptAuthor::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c5f9e4969795cedd7da80864c1ad69c0d68f8b9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091804"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analyse le texte du script, ajoute le texte pour le moteur de création de script et crée un `IScriptEntry` objet qui correspond au bloc de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszCode`  
 [in] Le texte de script à analyser.  
  
 `pszItemName`  
 [in] L’adresse de mémoire tampon qui contient le nom de l’élément associé au bloc de script.  
  
 `pszDelimiter`  
 [in] L’adresse du délimiteur de fin du bloc de script. Lorsque `pszCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un séparateur (par exemple, un double guillemet), pour détecter la fin du bloc de script. Définissez ce paramètre avec la valeur NULL s’il n’existe pas de séparateurs pour identifier la fin du bloc de script.  
  
 `dwCookie`  
 [in] Une valeur définie par l’application qui est associée au nouveau `IScriptEntry` objet.  
  
 `dwFlags`  
 [in] Non utilisé.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)