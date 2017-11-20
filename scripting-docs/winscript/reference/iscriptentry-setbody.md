---
title: IScriptEntry::SetBody | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.SetBody
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06ee232aa730366e9a23e15cdc45f6734b9ef744
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Définit le texte qui se trouve dans le corps d’une `IScriptEntry` bloc de script ou un `IScriptScriptlet` scriptlet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psz`  
 [in] Pour un `IScriptEntry` bloc de script, `psz` est le texte placé entre les balises de script.  
  
 Pour un `IScriptEntry` bloc de la fonction, `psz` est le corps de la fonction.  
  
 Pour un `IScriptScriptlet` objet (qui en dérive `IScriptEntry`), `psz` est le texte du script du scriptlet.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [IScriptEntry (Interface)](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)