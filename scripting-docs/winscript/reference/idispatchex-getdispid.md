---
title: 'IDispatchEx :: GetDispID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81bb33a1e793f38e15dc51b37c4fa062eb54e7fa
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144531"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Mappe un nom de membre unique à son DISPID correspondant, qui peut ensuite être utilisé lors des appels suivants à `IDispatchEx::InvokeEx` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bstrName`  
 Passé dans le nom à mapper.  
  
 `grfdex`  
 Détermine les options d’obtention de l’identificateur de membre. Il peut s’agir d’une combinaison des valeurs suivantes :  
  
|Valeur|Signification|  
|-----------|-------------|  
|fdexNameCaseSensitive|Demande que la recherche de nom s’effectue de façon sensible à la casse. Peut être ignoré par un objet qui ne prend pas en charge la recherche qui respecte la casse.|  
|fdexNameEnsure|Demande que le membre soit créé s’il n’existe pas déjà. Le nouveau membre doit être créé avec la valeur `VT_EMPTY` .|  
|fdexNameImplicit|Indique que l’appelant recherche un ou plusieurs objets d’un nom particulier lorsque l’objet de base n’est pas spécifié explicitement.|  
|fdexNameCaseInsensitive|Demande que la recherche de nom s’effectue sans respect de la casse. Peut être ignoré par un objet qui ne prend pas en charge la recherche ne respectant pas la casse.|  
  
 `pid`  
 Pointeur vers l’emplacement alloué par l’appelant pour recevoir le résultat DISPID. Si une erreur se produit, `pid` contient DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Valeur de retour  
 Renvoie l'une des valeurs suivantes :  
  
|Valeur|Signification|
|-|-|  
|`S_OK`|Réussite.|  
|`E_OUTOFMEMORY`|Mémoire insuffisante.|  
|`DISP_E_UNKNOWNNAME`|Le nom n’était pas connu.|  
  
## <a name="remarks"></a>Notes  
 `GetDispID`peut être utilisé `GetIDsOfNames` à la place de pour obtenir le DispId d’un membre donné.  
  
 Étant donné que `IDispatchEx` autorise l’ajout et la suppression de membres, l’ensemble des DISPID ne reste pas constant pour la durée de vie d’un objet.  
  
 Le paramètre inutilisé `riid` dans `IDispatch::GetIDsOfNames` a été supprimé.  
  
## <a name="example"></a>Exemple  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)