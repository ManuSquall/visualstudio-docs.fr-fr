---
title: IDebugFunctionObject2::Evaluate | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58c15872b035660c2e0103a1a9ff69822b250a45
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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