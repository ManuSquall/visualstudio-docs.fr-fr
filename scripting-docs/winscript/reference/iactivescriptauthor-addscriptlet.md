---
title: IActiveScriptAuthor::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64df7bd4c0d0dde303cdc15d7111688d14c7dc49
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935456"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Ajoute un scriptlet de code en tant qu’enfant du niveau racine `IScriptNode` objet. Dans l’hôte, le nom qualifié complet du scriptlet est autorisé à avoir des deux niveaux.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 [in] L’adresse du nom par défaut à associer le scriptlet.  
  
 `pszCode`  
 [in] L’adresse du texte de scriptlet.  
  
 `pszItemName`  
 [in] L’adresse du tampon de l’identificateur du nom qualifié complet de scriptlet dans l’hôte de niveau supérieur.  
  
 `pszSubItemName`  
 [in] L’adresse du tampon de l’identificateur de second niveau du nom qualifié complet de scriptlet dans l’hôte. La valeur NULL si le nom comporte un seul niveau.  
  
 `pszEventName`  
 [in] L’adresse d’une mémoire tampon qui contient le nom de l’événement pour lequel le scriptlet est un gestionnaire d’événements.  
  
 `pszDelimiter`  
 [in] L’adresse du délimiteur de fin du bloc de script. Lorsque `pszCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un séparateur (par exemple, un double guillemet), pour détecter la fin du bloc de script. Définissez ce paramètre avec la valeur NULL si un délimiteur ne marque pas la fin du bloc de script.  
  
 `dwCookie`  
 [in] Une valeur définie par l’application qui est utilisée pour associer le scriptlet à un objet hôte.  
  
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