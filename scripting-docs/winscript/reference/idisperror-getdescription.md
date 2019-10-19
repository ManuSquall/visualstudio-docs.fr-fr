---
title: 'IDispError :: GetDescription | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetDescription
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetDescription
ms.assetid: 04deaea6-0265-4e34-952e-634edba0e923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d1bb1c3516c2601707e1a0bcd69f4f8409514fe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573143"
---
# <a name="idisperrorgetdescription"></a>IDispError::GetDescription
Retourne une description textuelle de l’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrDescription`  
 à Chaîne contenant une brève description de l’erreur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Le texte est retourné dans la langue spécifiée par l’identificateur de paramètres régionaux (LCID) qui a été passé à `IDispatchEx::InvokeEx` pour la méthode qui a rencontré l’erreur.  
  
> [!NOTE]
> Cette méthode n’est pas implémentée.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDispError](../../winscript/reference/idisperror-interface.md)  
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)