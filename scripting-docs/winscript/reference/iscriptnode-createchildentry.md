---
title: "IScriptNode :: CreateChildEntry | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fcc010efe8fcf30a8f467dd94befff54bc5fac5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Ajoute une instance enfant de `IScriptEntry`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `isn`  
 [in] L’index de l’enfant du parent.  
  
 `dwCookie`  
 [in] Une valeur définie par l’application est utilisée pour associer l’entrée enfant de l’objet hôte.  
  
 `pszDelimiter`  
 [in] L’adresse du délimiteur de fin du bloc de script. Pour l’analyse, l’hôte utilise généralement un délimiteur (par exemple, deux guillemets simples), pour détecter la fin du bloc de script.  
  
 Le délimiteur permet le script de création de moteur pour fournir le prétraitement. Par exemple, le moteur peut remplacer un guillemet simple avec deux guillemets simples à utiliser comme délimiteur. Le moteur détermine comment le délimiteur est utilisé.  
  
 La valeur NULL si un délimiteur ne marque pas la fin du bloc de script.  
  
 `ppse`  
 [out] L’adresse d’une variable qui reçoit un pointeur vers le `IScriptEntry` interface de l’instance enfant.  
  
 Pour `IScriptNode` les objets qui représentent une page Web, ce paramètre retourne une `IScriptEntry` instance qui spécifie un bloc de script.  
  
 Pour `IScriptEntry` les objets qui représentent un bloc de script, ce paramètre retourne une `IScriptEntry` instance qui spécifie un objet de fonction.  
  
 Pour `IScriptEntry` les objets qui représentent une fonction de l’objet, cette méthode échoue.  
  
 Pour `IScriptScriptlet` des objets, cette méthode échoue.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Le `IScriptNode` interface représente une page Web ou ses éléments. Le `IScriptEntry` interface (qui est dérivée de `IScriptNode`) représente un bloc de script ou d’un objet de fonction. Le `IScriptScriptlet` interface (qui est dérivée de `IScriptEntry`) représente un gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi  
 [IScriptNode (Interface)](../../winscript/reference/iscriptnode-interface.md)   
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)