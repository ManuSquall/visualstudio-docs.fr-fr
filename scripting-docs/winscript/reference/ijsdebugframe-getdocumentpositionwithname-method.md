---
title: "Ijsdebugframe::getdocumentpositionwithname, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetDocumentPositionWithName
apilocation: jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49afb5903e190280d226a24b22dc389041861c52
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName, méthode
Retourne la position actuelle de ce frame de pile dans le document au niveau de l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pDocumentName`  
 [out] Pour les scripts statiques, une URL vers le document. Pour les scripts dynamiques, un nom contenant le type de script (par exemple, code eval, le code de fonction etc.) est retourné.  
  
 `pLine`  
 [out] position de ligne de base 1 dans le document.  
  
 `pColumn`  
 [out] position de ligne de base 1 dans le document.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)