---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f59d86e94be5c0295786b747f6b57753aa087b07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Cette méthode crée un service de visualiseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
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
 [in] Objet implémentant le [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interface (fourni par l’évaluateur d’expression).  
  
 `ppService`  
 [out] Le service créé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le `binder`, `pSymProv`, et `pAddress` paramètres ont été passés à la `IDebugParsedExpression::EvaluateSync` (méthode). `CreateVisualizerService` doit être appelée uniquement à partir de `IDebugParsedExpression::EvaluateSync` dans le cadre de la prise en charge de l’un évaluateur d’expression de visualiseurs de types.  
  
## <a name="see-also"></a>Voir aussi  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)