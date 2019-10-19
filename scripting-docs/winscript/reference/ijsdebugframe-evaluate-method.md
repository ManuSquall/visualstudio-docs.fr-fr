---
title: 'IJsDebugFrame :: Evaluate, méthode | Microsoft Docs'
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
ms.openlocfilehash: 6227b97c1fd5fae32db3e13ef72751726c36b043
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573497"
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
 dans Expression à évaluer.  
  
 `ppDebugProperty`  
 à Objet représentant l’Explorateur de propriétés.  
  
 `pError`  
 à Message d’erreur si une erreur se produit.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Retourne les éléments suivants : S_OK : l’évaluation aboutit, * ppDebugProperty contient le résultat de l’évaluation. S_FALSE : Evaluation génère une erreur (ou l’opération d’évaluation n’est pas prise en charge), \*pError contient le message d’erreur.  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)