---
title: IScriptEntry::SetSignature | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9ff480f8e5c3192a7e2b355d39825cc3a084370
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729339"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Jeux de saisir des informations pour un `IScriptEntry` objet de fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pti`  
 [in] Les informations de type.  
  
 `iMethod`  
 [in] L’index de la méthode dans le `ITypeInfo` objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Vous définissez des informations de type à l’aide de `IScriptEntry::SetSignature` ou [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informations de type peuvent également être générées par l’entrée en fonction de la représentation sous forme de la fonction interne.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)