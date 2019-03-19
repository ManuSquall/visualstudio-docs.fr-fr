---
title: IScriptNode::CreateChildHandler | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bca8b30021d39638f3755bace2625bb38a44242d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149245"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Ajoute un scriptlet comme une instance enfant d’un `IScriptNode`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszDefaultName`  
 [in] L’adresse du nom par défaut à associer le scriptlet.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] liste des identificateurs à partir du nom qualifié complet sur l’ordinateur hôte.  
  
 `cpszNames`  
 [in] Le nombre d’identificateurs dans les `prgpszNames` paramètre.  
  
 `pszEvent`  
 [in] L’adresse de mémoire tampon qui identifie le nom d’événement associé au scriptlet.  
  
 `pszDelimiter`  
 [in] L’adresse du délimiteur de fin du bloc de script. Pour l’analyse, l’hôte utilise généralement un délimiteur (par exemple, un double guillemet), pour détecter la fin du bloc de script.  
  
 Le délimiteur permet par le moteur de création de script de prétraitement. Par exemple, le moteur peut remplacer un guillemet simple avec deux guillemets simples à utiliser comme délimiteur. Le moteur détermine comment le délimiteur est utilisé.  
  
 La valeur NULL si aucun délimiteur n’est utilisé pour identifier la fin du bloc de script.  
  
 `ptiSignature`  
 [in] Les informations de type pour un objet de fonction.  
  
 `iMethodSignature`  
 [in] L’index de la fonction dans le `ITypeInfo``ptiSignature` paramètre.  
  
 `isn`  
 [in] L’index de l’enfant de la page parente.  
  
 `dwCookie`  
 [in] Une valeur définie par l’application qui est utilisée pour associer l’entrée de l’objet hôte.  
  
 `ppse`  
 [out] L’adresse d’une variable qui reçoit un pointeur vers le `IScriptEntry` interface de l’instance enfant.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Un scriptlet spécifie un gestionnaire d’événements. Cette méthode crée un scriptlet si elle est appelée par un `IScriptNode` objet qui représente une page Web. Cette méthode ne réussit pas si elle est appelée par d’autres interfaces.  
  
## <a name="see-also"></a>Voir aussi  
 [IScriptNode (Interface)](../../winscript/reference/iscriptnode-interface.md)   
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)