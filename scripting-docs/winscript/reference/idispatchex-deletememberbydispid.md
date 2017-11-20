---
title: IDispatchEx::DeleteMemberByDispID | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.DeleteMemberByDispID
apilocation: scrobj.dll
helpviewer_keywords: DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 573eb60dc901e43706835c4d627b25bd54bbe751
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Supprime un membre par DISPID.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `id`  
 Identificateur de membre. Utilise `GetDispID` ou `GetNextDispID` pour obtenir l’identificateur de dispatch.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Opération réussie.|  
|`S_FALSE`|Membre existe mais ne peut pas être supprimé.|  
  
## <a name="remarks"></a>Remarques  
 Si le membre est supprimé, le DISPID doit rester valide pour `GetNextDispID`.  
  
 Si un membre avec un nom donné est supprimé, et par la suite un membre portant le même nom est recréé, le DISPID doit être le même. (Si les noms de membre qui diffèrent uniquement par leur casse sont « même » sont dépendant de l’objet.)  
  
## <a name="example"></a>Exemple  
  
```  
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDispatchEx (Interface)](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)