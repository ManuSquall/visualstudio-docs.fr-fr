---
title: Méthode IJsDebugFrame::Evaluate | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b328d6071ae9dc96b8e7f62bad6d4417aa1730f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558188"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate, méthode
Évaluer une expression dans le contexte de ce frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pExpressionText`  
 [in] L’expression à évaluer.  
  
 `ppDebugProperty`  
 [out] Objet représentant l’Explorateur de propriétés.  
  
 `pError`  
 [out] Le message d’erreur si une erreur se produit.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Retourne les éléments suivants : S_OK: Évaluation a réussi, * ppDebugProperty contient le résultat de l’évaluation. S_FALSE : L’évaluation génère une erreur (ou l’opération d’évaluation n’est pas pris en charge), \*pError contient le message d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)