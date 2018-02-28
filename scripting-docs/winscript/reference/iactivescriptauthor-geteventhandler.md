---
title: IActiveScriptAuthor::GetEventHandler | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b09f900162b6dba82696c946b53ab131691530c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Retourne le scriptlet qui possède les attributs spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdisp`  
 [in] Le `IDispatch` objet qui correspond à la `NamedItem` à laquelle le scriptlet est associé.  
  
 `pszItem`  
 [in] L’adresse de la mémoire tampon de l’identificateur du nom qualifié complet scriptlet dans l’hôte de niveau supérieur.  
  
 `pszSubItem`  
 [in] L’adresse de la mémoire tampon de l’identificateur de second niveau du nom qualifié complet scriptlet dans l’hôte. La valeur NULL si le nom comporte un seul niveau.  
  
 `pszEvent`  
 [in] L’adresse d’une mémoire tampon qui contient le nom de l’événement. Le scriptlet est un gestionnaire d’événements pour cet événement.  
  
 `ppse`  
 [out] L’adresse d’une variable qui reçoit un pointeur vers le `IScriptEntry` interface du scriptlet qui possède les attributs spécifiés.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptAuthor (Interface)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)