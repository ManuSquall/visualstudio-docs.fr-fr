---
title: 'IScriptNode :: CreateChildHandler | Microsoft Docs'
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
ms.openlocfilehash: 9e024bb7d6a81b35994edddfe9e71666b0ee8df0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573604"
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
 dans Adresse du nom par défaut à associer au scriptlet.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] Liste d’identificateurs à partir du nom qualifié complet sur l’hôte.  
  
 `cpszNames`  
 dans Nombre d’identificateurs dans le paramètre `prgpszNames`.  
  
 `pszEvent`  
 dans Adresse tampon qui identifie le nom de l’événement associé au scriptlet.  
  
 `pszDelimiter`  
 dans Adresse du délimiteur de bloc de fin de script. Pour l’analyse, l’hôte utilise généralement un délimiteur (par exemple, deux guillemets simples) pour détecter la fin du bloc de script.  
  
 Le délimiteur permet le prétraitement par le moteur de création de script. Par exemple, le moteur peut remplacer un guillemet simple par deux guillemets simples à utiliser comme délimiteur. Le moteur détermine la façon dont le délimiteur est utilisé.  
  
 A la valeur NULL si aucun délimiteur n’est utilisé pour identifier la fin du bloc de script.  
  
 `ptiSignature`  
 dans Informations de type pour un objet de fonction.  
  
 `iMethodSignature`  
 dans Index de la fonction dans le paramètre `ITypeInfo``ptiSignature`.  
  
 `isn`  
 dans Index de l’enfant dans le parent.  
  
 `dwCookie`  
 dans Valeur définie par l’application qui est utilisée pour associer l’entrée à l’objet hôte.  
  
 `ppse`  
 à Adresse d’une variable qui reçoit un pointeur vers l’interface `IScriptEntry` de l’instance enfant.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Un scriptlet spécifie un gestionnaire d’événements. Cette méthode crée un scriptlet s’il est appelé par un objet `IScriptNode` qui représente une page Web. Cette méthode ne fonctionne pas si elle est appelée par d’autres interfaces.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)