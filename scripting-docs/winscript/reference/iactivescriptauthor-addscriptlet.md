---
title: IActiveScriptAuthor::AddScriptlet | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b21f906a73a313bf775683ba63738adb25af0007
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Ajoute un scriptlet code en tant qu’enfant du niveau racine `IScriptNode` objet. Dans l’hôte, le nom qualifié complet du scriptlet est autorisé à avoir deux niveaux.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszDefaultName`  
 [in] L’adresse du nom par défaut pour associer le scriptlet.  
  
 `pszCode`  
 [in] L’adresse du texte scriptlet.  
  
 `pszItemName`  
 [in] L’adresse de la mémoire tampon de l’identificateur du nom qualifié complet scriptlet dans l’hôte de niveau supérieur.  
  
 `pszSubItemName`  
 [in] L’adresse de la mémoire tampon de l’identificateur de second niveau du nom qualifié complet scriptlet dans l’hôte. La valeur NULL si le nom comporte un seul niveau.  
  
 `pszEventName`  
 [in] L’adresse d’une mémoire tampon qui contient le nom de l’événement pour lequel le scriptlet est un gestionnaire d’événements.  
  
 `pszDelimiter`  
 [in] L’adresse du délimiteur de fin du bloc de script. Lorsque `pszCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur (par exemple, deux guillemets simples), pour détecter la fin du bloc de script. Définissez ce paramètre avec la valeur NULL si un délimiteur ne marque pas la fin du bloc de script.  
  
 `dwCookie`  
 [in] Une valeur définie par l’application qui est utilisée pour associer le scriptlet avec un objet hôte.  
  
 `dwFlags`  
 [in] Non utilisé.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)