---
title: IDispatchEx::GetDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c466ec767be53d100b970314bf0d81d5dd9dfb20
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097537"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Mappe un nom de membre unique à son DISPID correspondant, qui peut ensuite être utilisé sur les appels suivants à `IDispatchEx::InvokeEx`.  
  
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
 Détermine les options permettant d’obtenir l’identificateur de membre. Cela peut être une combinaison des valeurs suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|fdexNameCaseSensitive|Demande que la recherche de nom faire de la casse. Peut être ignoré par l’objet qui ne prend pas en charge la recherche respectant la casse.|  
|fdexNameEnsure|Demande que le membre créé s’il n’existe pas déjà. Le nouveau membre doit être créé avec la valeur `VT_EMPTY`.|  
|fdexNameImplicit|Indique que l’appelant est recherche ou des objets pour un membre d’un nom particulier lorsque l’objet de base n’est pas explicitement spécifié.|  
|fdexNameCaseInsensitive|Demande que la recherche de nom être effectuées de façon non-respect de la casse. Peut être ignoré par l’objet qui ne prend pas en charge la recherche de non-respect de la casse.|  
  
 `pid`  
 Pointeur vers allouée par l’appelant d’emplacement pour recevoir le résultat DISPID. Si une erreur se produit, `pid` contient DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Opération réussie.|  
|`E_OUTOFMEMORY`|Mémoire insuffisante.|  
|`DISP_E_UNKNOWNNAME`|Le nom n’était pas connu.|  
  
## <a name="remarks"></a>Notes  
 `GetDispID` peut être utilisé au lieu de `GetIDsOfNames` pour obtenir le DISPID d’un membre donné.  
  
 Étant donné que `IDispatchEx` permet l’ajout et la suppression de membres, l’ensemble de DISPID n’est pas constante pour la durée de vie d’un objet.  
  
 Non `riid` paramètre dans `IDispatch::GetIDsOfNames` a été supprimé.  
  
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