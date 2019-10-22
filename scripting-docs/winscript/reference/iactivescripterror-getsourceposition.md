---
title: 'IActiveScriptError :: GetSourcePosition | Microsoft Docs'
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
ms.openlocfilehash: 76ed307f988a3e5bf77ff978c466eda6e5dfee18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576887"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Récupère l’emplacement dans le code source où une erreur s’est produite pendant que le moteur de script exécutait un script.  
  
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
 à Adresse d’une variable qui reçoit un cookie qui identifie le contexte. L’interprétation de ce paramètre dépend de l’application hôte.  
  
 `pulLineNumber`  
 à Adresse d’une variable qui reçoit le numéro de ligne dans le fichier source où l’erreur s’est produite.  
  
 `pichCharPosition`  
 à Adresse d’une variable qui reçoit la position du caractère dans la ligne où l’erreur s’est produite.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si l’emplacement n’a pas été récupéré.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)