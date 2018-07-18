---
title: IDebugFunctionObject2::Evaluate | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8196eb45b2fe7eccbff5c23a7ffc58fd3eb59282
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112699"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Appelle la fonction et retourne la valeur obtenue en tant qu’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppParams`  
 [in] Un tableau de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) les objets qui représente les paramètres d’entrée. Chacun de ces paramètres a été créé en utilisant l’une des méthodes de création de cette interface.  
  
 `dwParams`  
 [in] Le nombre de paramètres dans le `ppParams` tableau.  
  
 `dwEvalFlags`  
 [in] Une combinaison d’indicateurs à partir de la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) énumération qui spécifie la manière dont l’évaluation doit être effectuée.  
  
 `dwTimeout`  
 [in] Spécifie la durée maximale, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez **infinie** pour attendre indéfiniment.  
  
 `ppResult`  
 [out] Retourne un **IDebugObject** qui représente la valeur de la fonction en tant qu’objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)