---
title: 'IScriptEntry :: GetRange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 0a6e1b1600c93aa05bbe9669fb57a23a8c9344a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575431"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Retourne la position de départ et la longueur d’une entrée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pichMin`  
 à Pour les objets `IScriptEntry` qui spécifient un bloc de script, retourne 0.  
  
 Pour les objets `IScriptEntry` qui spécifient un objet de fonction, retourne la position de départ de la fonction dans le bloc de script actuel.  
  
 Pour les objets `IScriptScriptlet`, retourne 0.  
  
 `pcch`  
 à Pour les objets `IScriptEntry` qui spécifient un bloc de script, retourne la longueur du texte.  
  
 Pour les objets `IScriptEntry` qui spécifient un objet de fonction, retourne la longueur de la définition de fonction.  
  
 Pour les objets `IScriptScriptlet`, retourne la longueur de l’entrée.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)