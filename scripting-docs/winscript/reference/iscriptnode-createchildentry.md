---
title: 'IScriptNode :: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8ca4ab504a9da2a63d5c70330d50e2c97e09817
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088229"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode :: CreateChildEntry
Ajoute une instance enfant de `IScriptEntry`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `isn`  
 [in] L’index de l’enfant de la page parente.  
  
 `dwCookie`  
 [in] Une valeur définie par l’application est utilisée pour associer l’entrée de l’enfant à l’objet hôte.  
  
 `pszDelimiter`  
 [in] L’adresse du délimiteur de fin du bloc de script. Pour l’analyse, l’hôte utilise généralement un délimiteur (par exemple, un double guillemet), pour détecter la fin du bloc de script.  
  
 Le délimiteur permet le script de création de moteur pour fournir le prétraitement. Par exemple, le moteur peut remplacer un guillemet simple avec deux guillemets simples à utiliser comme délimiteur. Le moteur détermine comment le délimiteur est utilisé.  
  
 La valeur NULL si un délimiteur ne marque pas la fin du bloc de script.  
  
 `ppse`  
 [out] L’adresse d’une variable qui reçoit un pointeur vers le `IScriptEntry` interface de l’instance enfant.  
  
 Pour `IScriptNode` les objets qui représentent une page Web, ce paramètre retourne une `IScriptEntry` instance qui spécifie un bloc de script.  
  
 Pour `IScriptEntry` les objets qui représentent un bloc de script, ce paramètre retourne une `IScriptEntry` instance qui spécifie un objet de fonction.  
  
 Pour `IScriptEntry` les objets qui représentent une fonction de l’objet, cette méthode échoue.  
  
 Pour `IScriptScriptlet` objets, cette méthode échoue.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Le `IScriptNode` interface représente une page Web ou ses éléments. Le `IScriptEntry` interface (qui est dérivée de `IScriptNode`) représente un bloc de script ou un objet de fonction. Le `IScriptScriptlet` interface (qui est dérivée de `IScriptEntry`) représente un gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi  
 [IScriptNode (Interface)](../../winscript/reference/iscriptnode-interface.md)   
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)