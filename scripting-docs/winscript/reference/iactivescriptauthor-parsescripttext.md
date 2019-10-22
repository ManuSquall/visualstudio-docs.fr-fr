---
title: IActiveScriptAuthor ::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 90d5ab0fa700ed29b5fb37b1c48617cedec871b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576153"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analyse le texte du script, ajoute le texte au moteur de création de scripts et crée un objet `IScriptEntry` qui correspond au bloc de script.  
  
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
 dans Texte de script à analyser.  
  
 `pszItemName`  
 dans Adresse mémoire tampon qui contient le nom d’élément associé au bloc de script.  
  
 `pszDelimiter`  
 dans Adresse du délimiteur de bloc de fin de script. Lorsque `pszCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur (par exemple, deux guillemets simples) pour détecter la fin du bloc de script. Affectez à ce paramètre la valeur NULL s’il n’existe aucun délimiteur pour identifier la fin du bloc de script.  
  
 `dwCookie`  
 dans Valeur définie par l’application qui est associée au nouvel objet `IScriptEntry`.  
  
 `dwFlags`  
 dans Non utilisé.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)