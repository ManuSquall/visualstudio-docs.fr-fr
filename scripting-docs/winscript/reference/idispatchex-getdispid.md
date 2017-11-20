---
title: IDispatchEx::GetDispID | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.GetDispID
apilocation: scrobj.dll
helpviewer_keywords: GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93595cd2d0f88244866ab7363ecd68c6d8073b48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Mappe un nom de membre unique à son DISPID correspondant, qui peut ensuite être utilisé sur les appels suivants à `IDispatchEx::InvokeEx`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Détermine les options permettant d’obtenir l’identificateur de membre. Cela peut être une combinaison des valeurs suivantes :  
  
|Valeur|Signification|  
|-----------|-------------|  
|fdexNameCaseSensitive|Demande que la recherche de nom faire de la casse. Peut être ignorée par l’objet qui ne prend pas en charge la recherche qui respecte la casse.|  
|fdexNameEnsure|Demande que le membre créé s’il n’existe pas. Le nouveau membre doit être créé avec la valeur `VT_EMPTY`.|  
|fdexNameImplicit|Indique que l’appelant est recherche des objets pour un membre d’un nom donné lorsque l’objet de base n’est pas explicitement spécifié.|  
|fdexNameCaseInsensitive|Demande que la recherche de nom faire respecter la casse. Peut être ignorée par l’objet qui ne prend pas en charge la recherche sans respecter la casse.|  
  
 `pid`  
 Pointeur vers alloué par l’appelant d’emplacement pour recevoir le résultat DISPID. Si une erreur se produit, `pid` contient DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Opération réussie.|  
|`E_OUTOFMEMORY`|Mémoire insuffisante.|  
|`DISP_E_UNKNOWNNAME`|Le nom n’est pas connu.|  
  
## <a name="remarks"></a>Remarques  
 `GetDispID`peut être utilisé à la place de `GetIDsOfNames` pour obtenir le DISPID d’un membre donné.  
  
 Étant donné que `IDispatchEx` permet l’ajout et la suppression de membres, le jeu de DISPID n’est pas constante pour la durée de vie d’un objet.  
  
 Non `riid` paramètre `IDispatch::GetIDsOfNames` a été supprimé.  
  
## <a name="example"></a>Exemple  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)