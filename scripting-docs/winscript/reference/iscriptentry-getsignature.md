---
title: IScriptEntry::GetSignature | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 062f069bb6a19c24f26a6a0bc6a9f4de2292d88f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729319"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Retourne informations de type pour un `IScriptEntry` objet de fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppti`  
 [out] Tapez les informations associées à ce `IScriptEntry` objet de fonction.  
  
 `piMethod`  
 [out] Index de la méthode dans le `ITypeInfo` objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Vous définissez des informations de type à l’aide de [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) ou [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informations de type peuvent également être générées par l’entrée en fonction de la représentation sous forme de la fonction interne.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)