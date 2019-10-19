---
title: 'IActiveScriptAuthor :: AddNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d2f08a49fdc768e87152bf486ce48687c79e68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577257"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Ajoute le nom d’un élément de niveau racine à l’espace de noms du moteur de création de script. Un *élément de niveau racine* est un objet qui peut contenir des propriétés et des méthodes, et qui peut également contenir une source d’événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszName`  
 dans Nom de l’élément tel qu’il est affiché à partir du script. Le nom doit être unique et persistant.  
  
 `dwFlags`  
 dans Indicateurs associés à l’élément nommé. Peut être une combinaison des valeurs suivantes :  
  
|Constante|valeur|Description|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Indique que le nom de l’élément est disponible dans l’espace de noms du script. Cela permet d’accéder aux propriétés, méthodes et événements de l’élément.<br /><br /> Par Convention, les propriétés de l’élément incluent les membres enfants de l’élément. Par conséquent, toutes les propriétés et méthodes de l’objet enfant (et leurs membres enfants, de manière récursive) sont accessibles.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Indique les événements de la source de l’élément que le script peut avoir des gestionnaires d’événements de script.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Indique que l’élément est une collection de propriétés et de méthodes globales associées au script. Ses membres sont créés en tant que variables et méthodes globales.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Indique que l’élément doit être enregistré si le moteur de création de script est enregistré.|  
|SCRIPTITEM_CODEONLY|0x00000200|Indique que l’élément nommé représente un objet de code uniquement et qu’il n’a pas de membre à créer.|  
|SCRIPTITEM_NOCODE|0x00000400|Indique que l’élément nommé est simplement un nom qui est ajouté et qu’il n’a rien à créer.|  
  
 `pdisp`  
 dans @No__t_0 de l’objet `NamedItem` utilisé pour collecter des méthodes, des propriétés ou la source de l’événement.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)