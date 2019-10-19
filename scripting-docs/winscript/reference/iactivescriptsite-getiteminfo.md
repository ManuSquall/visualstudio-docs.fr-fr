---
title: 'IActiveScriptSite :: GetItemInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c0458f42466a264c30a440b1b14a028a2457f12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570916"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Permet au moteur de script d’obtenir des informations sur un élément ajouté avec la méthode [IActiveScript :: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrName`  
 dans Nom associé à l’élément, tel que spécifié dans la méthode [IActiveScript :: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `dwReturnMask`  
 dans Masque de bits spécifiant les informations relatives à l’élément à retourner. Le moteur de script doit demander la quantité minimale d’informations possible, car certains des paramètres de retour (par exemple, `ITypeInfo`) peuvent prendre beaucoup de temps pour le chargement ou la génération. Peut être une combinaison des valeurs suivantes :  
  
|valeur|Signification|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Retourne l’interface `IUnknown` pour cet élément.|  
|SCRIPTINFO_ITYPEINFO|Retourne l’interface `ITypeInfo` pour cet élément.|  
  
 `ppunkItem`  
 à Adresse d’une variable qui reçoit un pointeur vers l’interface `IUnknown` associée à l’élément donné. Le moteur de script peut utiliser la méthode `IUnknown::QueryInterface` pour obtenir l’interface `IDispatch` pour l’élément. Ce paramètre reçoit la valeur NULL si `dwReturnMask` n’inclut pas la valeur SCRIPTINFO_IUNKNOWN. En outre, elle reçoit la valeur NULL si aucun objet n’est associé au nom de l’élément ; ce mécanisme est utilisé pour créer une classe simple lorsque l’élément nommé a été ajouté avec l’indicateur SCRIPTITEM_CODEONLY défini dans la méthode [IActiveScript :: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `ppTypeInfo`  
 à Adresse d’une variable qui reçoit un pointeur vers l’interface `ITypeInfo` associée à l’élément. Ce paramètre reçoit la valeur NULL si `dwReturnMask` n’inclut pas la valeur SCRIPTINFO_ITYPEINFO, ou si les informations de type ne sont pas disponibles pour cet élément. Si les informations de type ne sont pas disponibles, l’objet ne peut pas utiliser d’événements sources et la liaison de nom doit être réalisée avec la méthode `IDispatch::GetIDsOfNames`. Notez que l’interface `ITypeInfo` Récupérée décrit la coclasse de l’élément (TKIND_COCLASS), car l’objet peut prendre en charge plusieurs interfaces et interfaces d’événements. Si l’élément prend en charge l’interface `IProvideMultipleTypeInfo`, l’interface `ITypeInfo` Récupérée est la même que l’index zéro `ITypeInfo` qui serait obtenu à l’aide de la méthode `IProvideMultipleTypeInfo::GetInfoOfIndex`.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`TYPE_E_ELEMENTNOTFOUND`|Un élément portant le nom spécifié est introuvable.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode récupère uniquement les informations indiquées par le paramètre `dwReturnMask` ; Cela améliore les performances. Par exemple, si une interface `ITypeInfo` n’est pas nécessaire pour un élément, elle n’est tout simplement pas spécifiée dans `dwReturnMask`.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)