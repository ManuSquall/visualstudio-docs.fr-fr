---
title: "IActiveScriptSite::GetItemInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetItemInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetItemInfo"
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetItemInfo
Permet au moteur de script pour obtenir des informations sur un élément ajouté avec la méthode d' [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
## Syntaxe  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### Paramètres  
 `pstrName`  
 \[in\]  Le nom associé à l'élément, comme spécifié dans la méthode d' [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `dwReturnMask`  
 \[in\]  Masquer un peu spécifier les informations sur l'élément doivent être retournées.  Le moteur de script doit demander la quantité minimale des informations possible parce que certains paramètres de retour \(par exemple, `ITypeInfo`\) peuvent prendre du temps considérable de charger ou se produire.  Peut être une combinaison des valeurs suivantes :  
  
|Valeur|Signification|  
|------------|-------------------|  
|SCRIPTINFO\_IUNKNOWN|Retourne l'interface d' `IUnknown` pour cet élément.|  
|SCRIPTINFO\_ITYPEINFO|Retourne l'interface d' `ITypeInfo` pour cet élément.|  
  
 `ppunkItem`  
 \[out\]  L'adresse d'une variable qui reçoit un pointeur vers l'interface d' `IUnknown` associé à l'élément donné.  Le moteur de script peut utiliser la méthode d' `IUnknown::QueryInterface` pour obtenir l'interface d' `IDispatch` pour l'élément.  Ce paramètre accepte NULL si `dwReturnMask` n'inclut pas la valeur de SCRIPTINFO\_IUNKNOWN.  De plus, il reçoit NULL s'il n'y a aucun objet associé au nom de l'élément ; ce mécanisme est utilisé pour créer une classe simple lorsque l'élément nommé a été ajouté à la balise de SCRIPTITEM\_CODEONLY définie dans la méthode d' [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `ppTypeInfo`  
 \[out\]  L'adresse d'une variable qui reçoit un pointeur vers l'interface d' `ITypeInfo` associé à l'élément.  Ce paramètre accepte NULL si `dwReturnMask` n'inclut pas la valeur de SCRIPTINFO\_ITYPEINFO, ou si les informations de type sont pas disponibles pour cet élément.  Si les informations de type sont pas disponibles, l'objet ne peut pas des événements de source, et la liaison de nom doit être achevée avec la méthode d' `IDispatch::GetIDsOfNames` .  Notez que l'interface d' `ITypeInfo` récupérée décrit la coclasse de l'élément \(TKIND\_COCLASS\) parce que l'objet peut prendre en charge plusieurs interfaces et interfaces d'événement.  Si l'élément prend en charge l'interface d' `IProvideMultipleTypeInfo` , l'interface d' `ITypeInfo` récupérée est identique à l'index zéro `ITypeInfo` qui est obtenu à l'aide de la méthode d' `IProvideMultipleTypeInfo::GetInfoOfIndex` .  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`E_INVALIDARG`|Un argument n'était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`TYPE_E_ELEMENTNOTFOUND`|Un élément du nom spécifié est introuvable.|  
  
## Notes  
 Cette méthode récupère uniquement les informations indiquées par le paramètre d' `dwReturnMask` ; cela améliore les performances.  Par exemple, si une interface d' `ITypeInfo` n'est pas nécessaire d'un élément, il n'est pas simplement spécifié dans `dwReturnMask`.  
  
## Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)