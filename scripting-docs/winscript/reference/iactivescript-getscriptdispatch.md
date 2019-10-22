---
title: 'IActiveScript :: GetScriptDispatch | Microsoft Docs'
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
ms.openlocfilehash: ba53f2eccde18bd5b2d9c609ea680b50cb7261c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575763"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Récupère l’interface `IDispatch` pour les méthodes et les propriétés associées au script en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrItemName`  
 dans Adresse d’une mémoire tampon qui contient le nom de l’élément pour lequel l’appelant a besoin de l’objet de distribution associé. Si ce paramètre est `NULL`, l’objet de dispatch contient toutes les méthodes globales et les propriétés définies par le script. Par le biais de l’interface `IDispatch` et de l’interface `ITypeInfo` associée, l’hôte peut appeler des méthodes de script ou afficher et modifier des variables de script.  
  
 `ppdisp`  
 à Adresse d’une variable qui reçoit un pointeur vers l’objet associé aux méthodes et propriétés globales du script. Si le moteur de script ne prend pas en charge un tel objet, `NULL` est retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n’a pas encore été chargé ou initialisé).|  
|`S_FALSE`|Le moteur de script ne prend pas en charge un objet de dispatch ; le paramètre `ppdisp` a la valeur NULL.|  
  
## <a name="remarks"></a>Notes  
 Étant donné que les méthodes et les propriétés peuvent être ajoutées en appelant l’interface [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) , l’interface `IDispatch` retournée par cette méthode peut prendre en charge de manière dynamique les nouvelles méthodes et propriétés. De même, la méthode `IDispatch::GetTypeInfo` doit retourner une nouvelle interface `ITypeInfo` unique lorsque des méthodes et des propriétés sont ajoutées. Notez, toutefois, que les moteurs de langage ne doivent pas modifier l’interface `IDispatch` d’une manière incompatible avec les précédentes `ITypeInfo` interface retournées. Cela implique, par exemple, que les DISPID ne seront jamais réutilisés.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)