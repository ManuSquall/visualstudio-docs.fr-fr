---
title: Méthode IJsDebugFrame::Evaluate | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 574af7823add67a00fc8add922b5e352fa1b369c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091921"
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
 Retourne les éléments suivants : S_OK : Évaluation a réussi, * ppDebugProperty contient le résultat de l’évaluation. S_FALSE : L’évaluation génère une erreur (ou l’opération d’évaluation n’est pas pris en charge), \*pError contient le message d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)