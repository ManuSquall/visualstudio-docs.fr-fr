---
title: IActiveScriptAuthor::GetEventHandler | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2e7f6cc265815db4acd847270b28c3e744257fa0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086682"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Retourne le scriptlet qui possède les attributs spécifiés.  
  
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
 [in] Le `IDispatch` objet qui correspond à la `NamedItem` auquel est joint le scriptlet.  
  
 `pszItem`  
 [in] L’adresse du tampon de l’identificateur du nom qualifié complet de scriptlet dans l’hôte de niveau supérieur.  
  
 `pszSubItem`  
 [in] L’adresse du tampon de l’identificateur de second niveau du nom qualifié complet de scriptlet dans l’hôte. La valeur NULL si le nom comporte un seul niveau.  
  
 `pszEvent`  
 [in] L’adresse d’une mémoire tampon qui contient le nom de l’événement. Le scriptlet est un gestionnaire d’événements pour cet événement.  
  
 `ppse`  
 [out] L’adresse d’une variable qui reçoit un pointeur vers le `IScriptEntry` interface du scriptlet qui possède les attributs spécifiés.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptAuthor (Interface)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)