---
title: IActiveScriptError::GetSourcePosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourcePosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4446235a9584bc45fad84b6f92ecc02592e554f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009622"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Récupère l’emplacement dans le code source où une erreur s’est produite pendant que le moteur de script a été exécutant un script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwSourceContext`  
 [out] Adresse d’une variable qui reçoit un cookie qui identifie le contexte. L’interprétation de ce paramètre dépend de l’application hôte.  
  
 `pulLineNumber`  
 [out] Adresse d’une variable qui reçoit le numéro de ligne dans le fichier source où l’erreur s’est produite.  
  
 `pichCharPosition`  
 [out] Adresse d’une variable qui reçoit la position du caractère dans la ligne où l’erreur s’est produite.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si l’emplacement n’a pas été récupéré.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)