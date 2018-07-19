---
title: IActiveScript::GetScriptDispatch | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b2f09934cf6d2bb28f7dae93d0bf49c8dc7437d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641429"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Récupère le `IDispatch` interface pour les méthodes et les propriétés associées avec le script en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrItemName`  
 [in] Adresse d’une mémoire tampon qui contient le nom de l’élément pour lequel l’appelant doit l’objet de distribution associés. Si ce paramètre est `NULL`, l’objet de répartition contient en tant que ses membres toutes les méthodes globales et les propriétés définies par le script. Via le `IDispatch` interface ainsi que le `ITypeInfo` interface, l’hôte peut appeler des méthodes de script ou de la vue et modifier les variables de script.  
  
 `ppdisp`  
 [out] Adresse d’une variable qui reçoit un pointeur vers l’objet associé à des méthodes globales et les propriétés du script. Si le moteur de script ne prend pas en charge un tel objet `NULL` est retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé).|  
|`S_FALSE`|Le moteur de script ne prend pas en charge un objet de distribution ; le `ppdisp` paramètre a la valeur NULL.|  
  
## <a name="remarks"></a>Remarques  
 Étant donné que les méthodes et les propriétés peuvent être ajoutées en appelant le [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) interface, le `IDispatch` interface retournée par cette méthode peut prendre dynamiquement en charge les nouvelles méthodes et propriétés. De même, la `IDispatch::GetTypeInfo` méthode doit retourner un nouveau unique `ITypeInfo` lors de l’ajout de méthodes et propriétés de l’interface. Notez, toutefois, que les moteurs de langue ne doivent pas changer le `IDispatch` interface dans une manière incompatible avec les précédentes `ITypeInfo` interface retournée. Par exemple, qui implique que les DISPID ne seront jamais réutilisés.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)