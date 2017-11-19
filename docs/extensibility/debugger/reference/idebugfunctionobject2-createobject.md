---
title: IDebugFunctionObject2::CreateObject | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 08ae477758aabb2b65b5823a37a9c07d61d4083b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="remarks"></a>Remarques  
 Appelez cette méthode pour créer un objet qui représente une instance d’une classe ou autre type complexe qui nécessite un constructeur, qui est un paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)