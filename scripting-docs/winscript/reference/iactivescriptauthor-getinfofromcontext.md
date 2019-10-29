---
title: 'IActiveScriptAuthor :: GetInfoFromContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8b9ad4677d580d495c72866be57712476d6a9c7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985322"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Retourne des informations de type et des positions d’ancrage pour un caractère donné dans un bloc de code. Il fournit des informations sur IntelliSense, les listes globales et les conseils sur les paramètres de membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszCode`  
 dans Adresse de la chaîne de bloc de code utilisée pour générer les résultats des informations.  
  
 `cchCode`  
 dans Longueur du bloc de code.  
  
 `ichCurrentPosition`  
 dans Position du caractère par rapport au début du bloc.  
  
 `dwListTypesRequested`  
 dans Types de liste demandés. Peut être une combinaison des valeurs suivantes :  
  
|Constante|valeur|Description|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Aucune liste.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Liste des membres.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Liste d’énumération.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Liste des paramètres de la méthode d’appel.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Liste globale.|  
  
 Le type SCRIPT_CMPL_GLOBALLIST est traité comme un élément de saisie semi-automatique par défaut qui peut être combiné à l’aide de l’opérateur OR avec d’autres éléments de saisie semi-automatique. Le moteur de création de script tente d’abord de remplir les informations de type pour d’autres éléments de la liste de saisie semi-automatique. En cas d’échec, le moteur remplit SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 à Type de liste fourni.  
  
 `pichListAnchorPosition`  
 à Index de début du contexte qui contient la position actuelle. L’index de début est relatif au début du bloc.  
  
 Elle est remplie uniquement lorsque `dwListTypesRequested` comprend SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST ou SCRIPT_CMPL_GLOBALLIST. Pour les autres types de listes demandés, le résultat n’est pas défini.  
  
 `pichFuncAnchorPosition`  
 à Index de début de l’appel de fonction qui contient la position actuelle. L’index de début est relatif au début du bloc.  
  
 Cela est rempli uniquement lorsque le contexte qui contient la position actuelle est un appel de fonction et lorsque `dwListTypesRequested` inclut SCRIPT_CMPL_PARAMLIST. Dans le cas contraire, le résultat n’est pas défini.  
  
 `pmemid`  
 à MEMBERID de la fonction, tel que défini par un type dans le paramètre `IProvideMultipleClassInfo``ppunk` out.  
  
 Elle est remplie uniquement lorsque `dwListTypesRequested` comprend SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 à Index du paramètre qui contient la position actuelle. Si la position actuelle est sur le nom de la fonction,-1 est retourné.  
  
 La valeur `piCurrentParameter` est remplie uniquement lorsque `dwListTypesRequested` comprend SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 Informations de type, fournies sous la forme d’un objet `IProvideMultipleClassInfo`.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
   de l' [interface IProvideMultipleClassInfo](/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)  
 [Interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)