---
title: IActiveScript::GetScriptDispatch | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c329a4dbf42461369441b86f6d9ba18992916366
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935596"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Récupère le `IDispatch` interface pour les méthodes et les propriétés associées avec le script en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrItemName`  
 [in] Adresse d’une mémoire tampon qui contient le nom de l’élément pour lequel l’appelant doit disposer de l’objet de répartition associée. Si ce paramètre est `NULL`, l’objet de répartition contient en tant que ses membres toutes les méthodes globales et les propriétés définies par le script. Via le `IDispatch` interface et associé `ITypeInfo` interface, l’hôte peut appeler des méthodes de script ou une vue et modifier les variables de script.  
  
 `ppdisp`  
 [out] Adresse d’une variable qui reçoit un pointeur vers l’objet associé aux propriétés et les méthodes globales du script. Si le moteur de script ne prend pas en charge ce type d’objet `NULL` est retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé).|  
|`S_FALSE`|Le moteur de script ne prend pas en charge un objet de répartition ; le `ppdisp` paramètre est défini sur NULL.|  
  
## <a name="remarks"></a>Notes  
 Étant donné que les méthodes et propriétés peuvent être ajoutées en appelant le [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) interface, le `IDispatch` interface retournée par cette méthode peut prendre dynamiquement en charge les nouvelles méthodes et propriétés. De même, le `IDispatch::GetTypeInfo` méthode doit retourner un nouveau, unique `ITypeInfo` lors de l’ajout de méthodes et propriétés de l’interface. Notez, cependant, que les moteurs de langage ne doivent pas changer le `IDispatch` interface dans une manière incompatible avec n’importe quel précédente `ITypeInfo` interface retournée. Par exemple, cela implique que DISPID ne sera jamais réutilisé.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)