---
title: IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs
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
ms.openlocfilehash: e4fe885e116019608dd8d748c3cbdaff5d31dd2a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154411"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Retourne type d’informations et les positions d’ancrage pour un caractère donné dans un bloc de code. Fournit des informations de membre IntelliSense, des listes globales et des conseils sur les paramètres.  
  
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
 [in] L’adresse de la chaîne de bloc de code utilisée pour générer les résultats d’informations.  
  
 `cchCode`  
 [in] La longueur du bloc de code.  
  
 `ichCurrentPosition`  
 [in] La position du caractère par rapport au début du bloc.  
  
 `dwListTypesRequested`  
 [in] Les types de liste demandées. Peut être une combinaison des valeurs suivantes :  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Aucune liste.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Liste des membres.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Liste d’énumération.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Appelez la liste de paramètres de méthode.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Liste globale.|  
  
 Le type SCRIPT_CMPL_GLOBALLIST est traité comme un élément de saisie semi-automatique par défaut qui peut être combiné à l’aide de l’opérateur OR avec d’autres éléments de saisie semi-automatique. Le script du moteur de création de tout d’abord essaie de remplir les informations de type pour les autres éléments de liste de saisie semi-automatique. Si cette tentative échoue, le moteur remplit pour SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 [out] Le type de la liste fournie.  
  
 `pichListAnchorPosition`  
 [out] Index de début du contexte qui contient la position actuelle. L’index de début est par rapport au début du bloc.  
  
 Ce champ est renseigné uniquement lorsque `dwListTypesRequested` inclut SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST ou SCRIPT_CMPL_GLOBALLIST. Pour les autres types de liste demandée, le résultat est indéfini.  
  
 `pichFuncAnchorPosition`  
 [out] Index de début de l’appel de fonction qui contient la position actuelle. L’index de début est par rapport au début du bloc.  
  
 Ce champ est renseigné uniquement lorsque le contexte qui contient la position actuelle est un appel de fonction et lorsque `dwListTypesRequested` inclut SCRIPT_CMPL_PARAMLIST. Sinon, le résultat est indéfini.  
  
 `pmemid`  
 [out] L’ID de membre de la fonction, comme défini par un type dans le `IProvideMultipleClassInfo``ppunk` paramètre out.  
  
 Ce champ est renseigné uniquement lorsque `dwListTypesRequested` inclut SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 [out] L’index du paramètre qui contient la position actuelle. Si la position actuelle est sur le nom de fonction, -1 est retourné.  
  
 Le `piCurrentParameter` valeur est remplie uniquement lorsque `dwListTypesRequested` inclut SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 Les informations de type, qui sont fournies sous la forme d’un `IProvideMultipleClassInfo` objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [IProvideMultipleClassInfo Interface](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)   
 [Interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)