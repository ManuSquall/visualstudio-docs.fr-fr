---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 893dc36c066426ad1de7346c7ce1fea24b191ba3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090686"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analyse un code de procédure, ajoute du texte de la procédure code pour le moteur de création de script et crée un `IScriptEntry` objet qui correspond à la procédure de code.  
  
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
 [in] Le texte de script à analyser.  
  
 `pszFormalParams`  
 [in] L’adresse des noms de paramètre formel pour la procédure. Les noms de paramètres doivent être séparés par des délimiteurs appropriés pour le moteur de création de script. Les noms ne doivent pas être placées entre parenthèses.  
  
 `pszProcedureName`  
 [in] L’adresse du nom de procédure à analyser.  
  
 `pszItemName`  
 [in] L’adresse de la mémoire tampon qui contient le nom de l’élément associé à la `IScriptEntry` objet.  
  
 `pszDelimiter`  
 [in] L’adresse du délimiteur de fin du bloc de script. Lorsque `pszCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un séparateur (par exemple, un double guillemet), pour détecter la fin du bloc de script. Définissez ce paramètre avec la valeur NULL s’il n’existe aucun délimiteur pour marquer la fin du bloc de script.  
  
 `dwCookie`  
 [in] Une valeur définie par l’application qui est associée au nouveau `IScriptEntry` objet.  
  
 `dwFlags`  
 [in] Non utilisé.  
  
 `pdispFor`  
 [in] Non utilisé.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Actuel [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur n’implémente pas cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptAuthorProcedure](../../winscript/reference/iactivescriptauthorprocedure-interface.md)