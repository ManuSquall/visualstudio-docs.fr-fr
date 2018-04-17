---
title: IDebugFunctionObject2::CreateObject | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5283d72972e1ba579cafa82648cbf0ec0fcf80c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Crée un objet qui utilise un constructeur de fonction de paramètres d’évaluation de l’indicateur et une valeur de délai d’attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pConstructor`  
 [in] Un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objet qui représente le constructeur de l’objet à créer.  
  
 `dwArgs`  
 [in] Le nombre de paramètres dans le `pArg` tableau. Représente le nombre de paramètres transmis au constructeur.  
  
 `pArgs`  
 [in] Un tableau de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) les objets qui représente les paramètres passés au constructeur.  
  
 `dwEvalFlags`  
 [in] Une combinaison d’indicateurs à partir de la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) énumération qui spécifie la manière dont l’évaluation doit être effectuée.  
  
 `dwTimeout`  
 [in] Temps maximal, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez **infinie** pour attendre indéfiniment.  
  
 `ppObject`  
 [out] Retourne un **IDebugObject** représentant l’objet qui vient d’être créé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Appelez cette méthode pour créer un objet qui représente une instance d’une classe ou autre type complexe qui nécessite un constructeur, qui est un paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)