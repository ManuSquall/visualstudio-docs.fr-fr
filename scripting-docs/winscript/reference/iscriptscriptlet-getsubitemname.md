---
title: IScriptScriptlet::GetSubItemName | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptScriptlet.GetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: IScriptScriptlet::GetSubItemName
ms.assetid: 9ad963fc-9ce8-4b77-92c1-fb90d6307801
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43b8483e8a61c25a3911a35d4721c51f7b558530
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptscriptletgetsubitemname"></a>IScriptScriptlet::GetSubItemName
Retourne l’identificateur de la dernière dans le nom qualifié complet de l’hôte de l’objet d’un scriptlet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSubItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstr`  
 [out] Si l’ordinateur hôte pleinement qualifié du scriptlet nom a plusieurs niveaux, `pbstr` renvoie l’adresse de la mémoire tampon de l’identificateur au deuxième niveau.  
  
 Si l’ordinateur hôte pleinement qualifié du scriptlet nom a un niveau, `pbstr` renvoie l’adresse de la mémoire tampon de l’identificateur du premier niveau.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)