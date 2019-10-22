---
title: 'IJsDebugFrame :: GetDocumentPositionWithName, méthode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithName
apilocation:
- jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b818ca4dc1ec4402973026668972507861c86f22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575120"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName, méthode
Retourne la position actuelle de ce frame de pile dans le document au niveau de l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pDocumentName`  
 à Pour les scripts statiques, URL à documenter. Pour les scripts dynamiques, un nom contenant le type de script (par exemple, le code d’évaluation, le code de fonction, etc.) est retourné.  
  
 `pLine`  
 [out] position de ligne de base 1 dans le document.  
  
 `pColumn`  
 [out] position de ligne de base 1 dans le document.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)