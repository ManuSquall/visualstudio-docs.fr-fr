---
title: 'IScriptEntry :: SetSignature | Microsoft Docs'
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
ms.openlocfilehash: e381e642462fe56e661de9da0d8974dc7bf18b18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575337"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Définit des informations de type pour un objet de fonction `IScriptEntry`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pti`  
 dans Informations de type.  
  
 `iMethod`  
 dans Index de méthode dans l’objet `ITypeInfo`.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Vous définissez les informations de type à l’aide de `IScriptEntry::SetSignature` ou [IScriptNode :: CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Les informations de type peuvent également être générées par l’entrée en fonction de la représentation interne de la fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)