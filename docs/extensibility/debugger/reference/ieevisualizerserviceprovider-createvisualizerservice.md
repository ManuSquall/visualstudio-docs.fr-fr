---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a67f4ee41bdc256b94a8e12bf1570ea1f1a2a197
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992943"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Cette méthode crée un service de visualiseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `binder`  
 [in] Le [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objet passé à [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 [in] Le [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objet passé à `IDebugParsedExpression::EvaluateSync`.  
  
 `pAddress`  
 [in] Le [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objet passé à `IDebugParsedExression::EvaluateSync`.  
  
 `dataProvider`  
 [in] Objet qui implémente le [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interface (fourni par l’évaluateur d’expression).  
  
 `ppService`  
 [out] Le service créé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le `binder`, `pSymProv`, et `pAddress` paramètres ont été passés à la `IDebugParsedExpression::EvaluateSync` (méthode). `CreateVisualizerService` doit être appelée uniquement à partir de `IDebugParsedExpression::EvaluateSync` dans le cadre de la prise en charge de l’un évaluateur d’expression des visualiseurs de type.  
  
## <a name="see-also"></a>Voir aussi  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)