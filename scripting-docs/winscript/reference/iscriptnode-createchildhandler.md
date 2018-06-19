---
title: IScriptNode::CreateChildHandler | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ff2ba40d1570e23f0256bd34ca8aff0f8d77ce5c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729559"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Ajoute un scriptlet comme une instance de l’enfant d’un `IScriptNode`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] L’adresse du nom par défaut pour associer le scriptlet.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] une liste d’identificateurs de nom qualifié complet de l’ordinateur hôte.  
  
 `cpszNames`  
 [in] Le nombre d’identificateurs dans les `prgpszNames` paramètre.  
  
 `pszEvent`  
 [in] L’adresse de mémoire tampon qui identifie le nom de l’événement associé à la scriptlet.  
  
 `pszDelimiter`  
 [in] L’adresse du délimiteur de fin du bloc de script. Pour l’analyse, l’hôte utilise généralement un délimiteur (par exemple, deux guillemets simples), pour détecter la fin du bloc de script.  
  
 Le délimiteur active par le moteur de création de script de prétraitement. Par exemple, le moteur peut remplacer un guillemet simple avec deux guillemets simples à utiliser comme délimiteur. Le moteur détermine comment le délimiteur est utilisé.  
  
 La valeur NULL si aucun délimiteur n’est utilisé pour identifier la fin du bloc de script.  
  
 `ptiSignature`  
 [in] Les informations de type pour un objet de fonction.  
  
 `iMethodSignature`  
 [in] L’index de la fonction dans le `ITypeInfo``ptiSignature` paramètre.  
  
 `isn`  
 [in] L’index de l’enfant du parent.  
  
 `dwCookie`  
 [in] Une valeur définie par l’application qui est utilisée pour associer l’entrée de l’objet hôte.  
  
 `ppse`  
 [out] L’adresse d’une variable qui reçoit un pointeur vers le `IScriptEntry` interface de l’instance enfant.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Un scriptlet spécifie un gestionnaire d’événements. Cette méthode crée un scriptlet si elle est appelée par un `IScriptNode` objet qui représente une page Web. Cette méthode ne réussit pas si elle est appelée par d’autres interfaces.  
  
## <a name="see-also"></a>Voir aussi  
 [IScriptNode (Interface)](../../winscript/reference/iscriptnode-interface.md)   
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)