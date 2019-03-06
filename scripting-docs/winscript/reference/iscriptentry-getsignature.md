---
title: IScriptEntry::GetSignature | Microsoft Docs
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
ms.openlocfilehash: 245b5806006ad94740e09e23f881e26e071a3bc1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092727"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Retourne informations de type pour un `IScriptEntry` objet de fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppti`  
 [out] Tapez les informations associées à cet `IScriptEntry` objet de fonction.  
  
 `piMethod`  
 [out] Index de la méthode dans le `ITypeInfo` objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Vous définissez des informations de type à l’aide de [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) ou [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informations de type peuvent également être générées par l’entrée en fonction de la représentation sous forme de la fonction interne.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)