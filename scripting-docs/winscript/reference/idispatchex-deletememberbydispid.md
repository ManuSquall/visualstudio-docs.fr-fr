---
title: IDispatchEx::DeleteMemberByDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ead33fb51caff1103ca9abe6bc01f3e0aa6aa3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576639"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Supprime un membre par DISPID.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
|`S_FALSE`|Le membre existe mais ne peut pas être supprimé.|  
  
## <a name="remarks"></a>Notes  
 Si le membre est supprimé, le DISPID doit rester valide pour `GetNextDispID`.  
  
 Si un membre avec un nom donné est supprimé et qu’un membre du même nom est recréé, le DISPID doit être le même. (Si les noms de membres qui diffèrent uniquement par la casse sont « identiques » dépend de l’objet).  
  
## <a name="example"></a>Exemple  
  
```cpp
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>Voir aussi  
   de l' [interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)  
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)