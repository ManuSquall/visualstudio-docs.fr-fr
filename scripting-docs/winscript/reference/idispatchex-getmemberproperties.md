---
title: IDispatchEx::GetMemberProperties | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51e01ef3fa6d5e0611875f6402b79e53f8c83cac
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088190"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Récupère les propriétés d’un membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `id`  
 Identifie le membre. Utilise `GetDispID` ou `GetNextDispID` pour obtenir l’identificateur de dispatch.  
  
 `grfdexFetch`  
 Détermine les propriétés à récupérer. Cela peut être une combinaison des valeurs répertoriées sous `pgrfdex` et/ou une combinaison des valeurs suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|grfdexPropCanAll|Combine fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct et fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Combine fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct et fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Combine fdexPropNoSideEffects et fdexPropDynamicType.|  
|grfdexPropAll|Combine grfdexPropCanAll, grfdexPropCannotAll et grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Adresse d’un `DWORD` qui reçoit les propriétés demandées. Cela peut être une combinaison des valeurs suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|fdexPropCanGet|Le membre peut être obtenu à l’aide de DISPATCH_PROPERTYGET.|  
|fdexPropCannotGet|Le membre ne peut pas être obtenu à l’aide de DISPATCH_PROPERTYGET.|  
|fdexPropCanPut|Le membre peut être défini à l’aide de DISPATCH_PROPERTYGET.|  
|fdexPropCannotPut|Le membre ne peut pas être défini à l’aide de DISPATCH_PROPERTYGET.|  
|fdexPropCanPutRef|Le membre peut être défini à l’aide de DISPATCH_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|Le membre ne peut pas être défini à l’aide de DISPATCH_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|Le membre n’a pas d’effets secondaires. Par exemple, un débogueur peut en toute sécurité get/set/appel de ce membre sans modifier l’état du script en cours de débogage.|  
|fdexPropDynamicType|Le membre est dynamique et peut changer pendant la durée de vie de l’objet.|  
|fdexPropCanCall|Le membre peut être appelé comme une méthode à l’aide de DISPATCH_METHOD.|  
|fdexPropCannotCall|Le membre ne peut pas être appelé comme une méthode à l’aide de DISPATCH_METHOD.|  
|fdexPropCanConstruct|Le membre peut être appelé en tant que constructeur à l’aide de DISPATCH_CONSTRUCT.|  
|fdexPropCannotConstruct|Le membre ne peut pas être appelé en tant que constructeur à l’aide de DISPATCH_CONSTRUCT.|  
|fdexPropCanSourceEvents|Le membre peut déclencher des événements.|  
|fdexPropCannotSourceEvents|Le membre ne peut pas déclencher d’événements.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Opération réussie.|  
|`DISP_E_UNKNOWNNAME`|Le nom n’était pas connu.|  
  
## <a name="example"></a>Exemple  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)