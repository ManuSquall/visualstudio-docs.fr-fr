---
title: IDispatchEx::GetNextDispID | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ece7bde3230da370c8434cef7f780a92604df34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID
Énumère les membres de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `grfdex`  
 Détermine le jeu d’éléments à énumérer. Cela peut être une combinaison des valeurs suivantes :  
  
|Valeur|Signification|  
|-----------|-------------|  
|fdexEnumDefault|Demande que l’objet énumère les éléments de la valeur par défaut. L’objet est autorisé à énumérer un jeu d’éléments.|  
|fdexEnumAll|Demande que l’objet énumère tous les éléments. L’objet est autorisé à énumérer un jeu d’éléments.|  
  
 `id`  
 Identifie le membre actuel. GetNextDispID récupère l’élément dans l’énumération après celui-ci. Utilise les GetDispID ou un appel précédent à GetNextDispID pour obtenir cet identificateur. Utilise la valeur DISPID_STARTENUM pour obtenir le premier identificateur du premier élément.  
  
 `pid`  
 Adresse d’une variable DISPID qui reçoit l’identificateur de l’élément suivant dans l’énumération.  
  
 Si un membre est supprimé par `DeleteMemberByName` ou `DeleteMemberByDispID`, le `DISPID` doit rester valide pour `GetNextDispID`.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Opération réussie.|  
|`S_FALSE`|L’énumération est effectuée.|  
  
## <a name="example"></a>Exemple  
  
```  
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
      SysFreeString(bstrName);  
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDispatchEx (Interface)](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)