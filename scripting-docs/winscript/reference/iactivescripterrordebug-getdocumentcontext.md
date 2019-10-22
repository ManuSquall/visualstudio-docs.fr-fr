---
title: 'IActiveScriptErrorDebug :: GetDocumentContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptErrorDebug.GetDocumentContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptErrorDebug::GetDocumentContext
ms.assetid: 567601a1-551a-4905-bda1-1f54610174f4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e1a6e2502e9329a7a56a7359e11a934f0ae5985
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576331"
---
# <a name="iactivescripterrordebuggetdocumentcontext"></a>IActiveScriptErrorDebug::GetDocumentContext
Fournit le contexte du document pour cette erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppssc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppssc`  
 à Contexte du document pour cette erreur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 La plage de la position des caractères du contexte de document doit inclure tous les caractères correspondant à l’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)