---
title: IDebugExpressionEvaluator2::GetService | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0c93f7585c03b4df1e7c260b9b8e41436dcd86ee
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201667"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère un objet de service selon son identificateur unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
## <a name="remarks"></a>Notes  
 Cela peut être consommée par un évaluateur d’expression de tiers pour obtenir des services à partir d’un autre évaluateur d’expression. Par exemple, cette méthode peut être utilisée pour obtenir l’interface pour le service de visualiseur de l’évaluateur d’expression de valeur par défaut. Évaluateurs d’expression de fournisseurs tiers sont probablement pas besoin d’implémenter cette interface.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)

