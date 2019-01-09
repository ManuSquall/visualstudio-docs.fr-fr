---
title: IScriptEntry::GetRange | Microsoft Docs
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
ms.openlocfilehash: 6a4e053817ed4c503ebb41e2f3828da421e69ec7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088736"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Retourne la position de début et la longueur d’une entrée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pichMin`  
 [out] Pour `IScriptEntry` objets qui spécifient un bloc de script, retourne 0.  
  
 Pour `IScriptEntry` objets qui spécifient un objet de fonction retourne la position de début de la fonction dans le bloc de script actuel.  
  
 Pour `IScriptScriptlet` des objets, retourne 0.  
  
 `pcch`  
 [out] Pour `IScriptEntry` objets qui spécifient un bloc de script, retourne la longueur du texte.  
  
 Pour `IScriptEntry` objets qui spécifient un objet de fonction retourne la longueur de la définition de fonction.  
  
 Pour `IScriptScriptlet` des objets, retourne la longueur de l’entrée.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)