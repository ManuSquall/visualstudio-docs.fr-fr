---
title: IDebugExpressionEvaluator2::GetService | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d907bdd93d2c17eb86ae07f9c9cfa3034fa3c09d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Récupère un objet de service donné son identificateur unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```csharp  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `uid`  
 [in] Identificateur unique du service à récupérer.  
  
 `ppService`  
 [out] Retourne un objet qui représente le service.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Cela peut être consommé par un évaluateur d’expression de tiers pour obtenir des services à partir d’un autre évaluateur d’expression. Par exemple, cette méthode peut être utilisée pour obtenir l’interface pour le service de visualiseur de l’évaluateur d’expression de valeur par défaut. Évaluateurs d’expression de tiers sont peu susceptibles d’avoir besoin d’implémenter cette interface.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)