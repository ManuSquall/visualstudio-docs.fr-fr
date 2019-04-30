---
title: IScriptEntry::SetSignature | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 42740a0e6261317443b8c9cc23559a2f92f66540
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787187"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Jeux d’informations de type pour un `IScriptEntry` objet de fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Vous définissez des informations de type à l’aide de `IScriptEntry::SetSignature` ou [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informations de type peuvent également être générées par l’entrée en fonction de la représentation sous forme de la fonction interne.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)