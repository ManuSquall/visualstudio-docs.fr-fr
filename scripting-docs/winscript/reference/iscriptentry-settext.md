---
title: IScriptEntry::SetText | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.SetText
apilocation: scrobj.dll
helpviewer_keywords: ISetEntry::SetText
ms.assetid: 4605481b-7707-43d1-ab78-a9207d0cf6fe
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62f1d113dc23dca85db02bf23b2c79551108f3b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrysettext"></a>IScriptEntry::SetText
Définit le texte qui correspond à un `IScriptEntry` bloc de script ou le code source qui est contenu dans un `IScriptScriptlet` Gestionnaire d’événements.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetText(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psz`  
 [in] Le texte de la `IScriptEntry` bloc de script ou le code source de la `IScriptScriptlet` Gestionnaire d’événements.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)