---
title: 'IActiveScriptAuthor :: GetEventHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69b32f0040ea6d52e0712b8e1813cc5a0b40c58
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576227"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Retourne le scriptlet qui a les attributs spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 dans Objet `IDispatch` qui correspond au `NamedItem` auquel le scriptlet est attaché.  
  
 `pszItem`  
 dans Adresse de mémoire tampon de l’identificateur de niveau supérieur du nom du scriptlet complet dans l’hôte.  
  
 `pszSubItem`  
 dans Adresse de mémoire tampon de l’identificateur de deuxième niveau du nom du scriptlet complet dans l’hôte. Affectez la valeur NULL si le nom n’a qu’un seul niveau.  
  
 `pszEvent`  
 dans Adresse d’une mémoire tampon qui contient le nom de l’événement. Le scriptlet est un gestionnaire d’événements pour cet événement.  
  
 `ppse`  
 à Adresse d’une variable qui reçoit un pointeur vers l’interface `IScriptEntry` du scriptlet qui a les attributs spécifiés.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)