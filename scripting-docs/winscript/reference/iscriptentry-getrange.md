---
title: IScriptEntry::GetRange | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ae0ee34298e03fdd2e9c6bc841d9fbe90967e8f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729039"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Retourne la position de début et la longueur d’une entrée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pichMin`  
 [out] Pour `IScriptEntry` objets qui spécifient un bloc de script, retourne 0.  
  
 Pour `IScriptEntry` objets qui spécifient un objet de fonction, retourne la position de début de la fonction dans le bloc de script actuel.  
  
 Pour `IScriptScriptlet` des objets, retourne 0.  
  
 `pcch`  
 [out] Pour `IScriptEntry` objets qui spécifient un bloc de script, retourne la longueur du texte.  
  
 Pour `IScriptEntry` objets qui spécifient un objet de fonction retourne la longueur de la définition de fonction.  
  
 Pour `IScriptScriptlet` des objets, retourne la longueur de l’entrée.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)