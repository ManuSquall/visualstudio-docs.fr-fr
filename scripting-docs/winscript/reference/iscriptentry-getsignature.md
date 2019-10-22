---
title: 'IScriptEntry :: GetSignature | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e7b07ac64ce7e427a793f0af0db9a7905441d39b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575420"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Retourne des informations de type pour un objet de fonction `IScriptEntry`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppti`  
 à Informations de type associées à cet objet de fonction `IScriptEntry`.  
  
 `piMethod`  
 à Index de méthode dans l’objet `ITypeInfo`.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Vous définissez les informations de type à l’aide de [IScriptEntry :: SetSignature](../../winscript/reference/iscriptentry-setsignature.md) ou [IScriptNode :: CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Les informations de type peuvent également être générées par l’entrée en fonction de la représentation interne de la fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)