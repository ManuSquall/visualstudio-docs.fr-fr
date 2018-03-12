---
title: IActiveScriptSite::GetItemInfo | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccb898c14571d1f1fd1fcae7cb0b9a6d322f2754
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Permet au moteur de script obtenir des informations sur un élément ajouté avec le [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrName`  
 [in] Le nom associé à l’élément, comme spécifié dans le [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) (méthode).  
  
 `dwReturnMask`  
 [in] Un masque de bits spécifiant les informations relatives à l’élément doivent être retournées. Le moteur de script doit demander la quantité minimale d’informations possible, car certains des paramètres de retour (par exemple, `ITypeInfo`) peut prendre beaucoup de temps de chargement ou de générer. Peut être une combinaison des valeurs suivantes :  
  
|Valeur|Signification|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Retourne le `IUnknown` interface pour cet élément.|  
|SCRIPTINFO_ITYPEINFO|Retourne le `ITypeInfo` interface pour cet élément.|  
  
 `ppunkItem`  
 [out] Adresse d’une variable qui reçoit un pointeur vers le `IUnknown` interface associée à l’élément donné. Le moteur de script peut utiliser le `IUnknown::QueryInterface` méthode pour obtenir le `IDispatch` interface pour l’élément. Ce paramètre reçoit la valeur NULL si `dwReturnMask` n’inclut pas la valeur SCRIPTINFO_IUNKNOWN. En outre, il reçoit NULL si aucun objet associé au nom de l’élément ; Ce mécanisme est utilisé pour créer une classe simple lorsque l’élément nommé a été ajouté avec l’indicateur SCRIPTITEM_CODEONLY défini dans le [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) (méthode).  
  
 `ppTypeInfo`  
 [out] Adresse d’une variable qui reçoit un pointeur vers le `ITypeInfo` interface associée à l’élément. Ce paramètre reçoit la valeur NULL si `dwReturnMask` n’inclut pas la valeur SCRIPTINFO_ITYPEINFO, ou si les informations de type ne sont pas disponibles pour cet élément. Si les informations de type ne sont pas disponibles, l’objet ne peut pas source d’événements et la liaison de nom doit être réalisée avec la `IDispatch::GetIDsOfNames` (méthode). Notez que le `ITypeInfo` interface récupérée décrit coclasse de l’élément (TKIND_COCLASS), car l’objet peut prendre en charge plusieurs interfaces et les interfaces d’événements. Si l’élément prend en charge la `IProvideMultipleTypeInfo` interface, le `ITypeInfo` interface récupéré est le même que l’index zéro `ITypeInfo` qui serait obtenue à l’aide de la `IProvideMultipleTypeInfo::GetInfoOfIndex` (méthode).  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`TYPE_E_ELEMENTNOTFOUND`|Un élément portant le nom spécifié est introuvable.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode récupère uniquement les informations indiquées par le `dwReturnMask` paramètre ; cela améliore les performances. Par exemple, si un `ITypeInfo` interface n’est pas nécessaire pour un élément, il est tout simplement pas spécifié dans `dwReturnMask`.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)