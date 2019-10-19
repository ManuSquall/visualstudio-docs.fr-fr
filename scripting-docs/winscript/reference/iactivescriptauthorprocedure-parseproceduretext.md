---
title: IActiveScriptAuthorProcedure ::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11a34843f30274ec78f1652c5ed5cd4dbcf2884a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572820"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analyse une procédure de code, ajoute le texte de la procédure de code au moteur de création de scripts et crée un objet `IScriptEntry` qui correspond à la procédure de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszCode`  
 dans Texte de script à analyser.  
  
 `pszFormalParams`  
 dans Adresse des noms de paramètres formels pour la procédure. Les noms de paramètres doivent être séparés par les délimiteurs appropriés pour le moteur de création de script. Les noms ne doivent pas être placés entre parenthèses.  
  
 `pszProcedureName`  
 dans Adresse du nom de la procédure à analyser.  
  
 `pszItemName`  
 dans Adresse mémoire tampon qui contient le nom d’élément associé à l’objet `IScriptEntry`.  
  
 `pszDelimiter`  
 dans Adresse du délimiteur de bloc de fin de script. Lorsque `pszCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur (par exemple, deux guillemets simples) pour détecter la fin du bloc de script. Affectez à ce paramètre la valeur NULL s’il n’existe aucun délimiteur pour marquer la fin du bloc de script.  
  
 `dwCookie`  
 dans Valeur définie par l’application qui est associée au nouvel objet `IScriptEntry`.  
  
 `dwFlags`  
 dans Non utilisé.  
  
 `pdispFor`  
 dans Non utilisé.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Le moteur de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] actuel n’implémente pas cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptAuthorProcedure](../../winscript/reference/iactivescriptauthorprocedure-interface.md)