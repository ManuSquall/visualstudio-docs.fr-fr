---
title: 'IActiveScriptAuthor :: AddScriptlet | Microsoft Docs'
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
ms.openlocfilehash: 3a349a848f282e6b3a228c7b17009e0261801be5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577983"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Ajoute un scriptlet de code en tant qu’enfant du niveau racine `IScriptNode` objet. Dans l’hôte, le nom qualifié complet du scriptlet est autorisé à avoir seulement deux niveaux.  
  
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
 dans Adresse du nom par défaut à associer au scriptlet.  
  
 `pszCode`  
 dans Adresse du texte scriptlet.  
  
 `pszItemName`  
 dans Adresse de mémoire tampon de l’identificateur de niveau supérieur du nom du scriptlet complet dans l’hôte.  
  
 `pszSubItemName`  
 dans Adresse de mémoire tampon de l’identificateur de deuxième niveau du nom du scriptlet complet dans l’hôte. Affectez la valeur NULL si le nom n’a qu’un seul niveau.  
  
 `pszEventName`  
 dans Adresse d’une mémoire tampon qui contient le nom de l’événement pour lequel le scriptlet est un gestionnaire d’événements.  
  
 `pszDelimiter`  
 dans Adresse du délimiteur de bloc de fin de script. Lorsque `pszCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur (par exemple, deux guillemets simples) pour détecter la fin du bloc de script. Affectez à ce paramètre la valeur NULL si un délimiteur ne marque pas la fin du bloc de script.  
  
 `dwCookie`  
 dans Valeur définie par l’application qui est utilisée pour associer le scriptlet à un objet hôte.  
  
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