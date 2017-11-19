---
title: IScriptEntry::GetText | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetText
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetText
ms.assetid: 105b8244-1972-4b39-ac18-965f1f345ef2
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 548b26be48766fa4eb6c6eba16ae3bca2847a322
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygettext"></a>IScriptEntry::GetText
Retourne le texte qui correspond à la `IScriptEntry` bloc de script ou le code source qui est contenu dans le `IScriptScriptlet` Gestionnaire d’événements.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetText(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstr`  
 [out] Le texte dans le `IScriptEntry` bloc de script ou le code source qui est contenu dans le `IScriptScriptlet` Gestionnaire d’événements.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)