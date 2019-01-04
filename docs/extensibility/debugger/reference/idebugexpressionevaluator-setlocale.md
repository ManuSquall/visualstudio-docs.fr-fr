---
title: IDebugExpressionEvaluator::SetLocale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 128e00db6f648185c0404de3eddd4387c4067e8a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922349"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
Cette méthode définit la langue à utiliser pour créer des résultats imprimables.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `wLangID`  
 [in] L’identificateur de langue.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut être appelée plusieurs fois pendant que l’évaluateur d’expression (EE) est chargé, le EE doit donc être en mesure de changer de langue à la volée. Le EE utilise ces paramètres régionaux pour renvoyer des messages d’erreur et les chaînes dans la langue appropriée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)