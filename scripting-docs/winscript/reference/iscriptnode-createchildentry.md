---
title: 'IScriptNode :: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c58ff83c43a1418e6fb7bd8945afa181af60c68a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573613"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
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
 dans Index de l’enfant dans le parent.  
  
 `dwCookie`  
 dans Valeur définie par l’application utilisée pour associer l’entrée enfant à l’objet hôte.  
  
 `pszDelimiter`  
 dans Adresse du délimiteur de bloc de fin de script. Pour l’analyse, l’hôte utilise généralement un délimiteur (par exemple, deux guillemets simples) pour détecter la fin du bloc de script.  
  
 Le délimiteur permet au moteur de création de script de fournir le prétraitement. Par exemple, le moteur peut remplacer un guillemet simple par deux guillemets simples à utiliser comme délimiteur. Le moteur détermine la façon dont le délimiteur est utilisé.  
  
 Affectez la valeur NULL si un délimiteur ne marque pas la fin du bloc de script.  
  
 `ppse`  
 à Adresse d’une variable qui reçoit un pointeur vers l’interface `IScriptEntry` de l’instance enfant.  
  
 Pour les objets `IScriptNode` qui représentent une page Web, ce paramètre retourne une `IScriptEntry` instance qui spécifie un bloc de script.  
  
 Pour les objets `IScriptEntry` qui représentent un bloc de script, ce paramètre retourne une `IScriptEntry` instance qui spécifie un objet de fonction.  
  
 Pour `IScriptEntry` objets qui représentent un objet de fonction, cette méthode échoue.  
  
 Pour les objets `IScriptScriptlet`, cette méthode échoue.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 L’interface `IScriptNode` représente une page Web ou ses éléments. L’interface `IScriptEntry` (dérivée de `IScriptNode`) représente un bloc de script ou un objet de fonction. L’interface `IScriptScriptlet` (dérivée de `IScriptEntry`) représente un gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)