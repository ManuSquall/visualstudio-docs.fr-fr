---
title: 'IDebugFunctionObject2 :: CreateObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b60801f5288e88795ab75145b9c6120d4308d1c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202993"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée un objet qui utilise un constructeur donné des paramètres d’indicateur d’évaluation et une valeur de délai d’attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 dans Objet [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) qui représente le constructeur de l’objet à créer.  
  
 `dwArgs`  
 dans Nombre de paramètres dans le `pArg` tableau. Représente le nombre de paramètres passés au constructeur.  
  
 `pArgs`  
 dans Tableau d’objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente les paramètres passés au constructeur.  
  
 `dwEvalFlags`  
 dans Combinaison d’indicateurs de l’énumération [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui spécifie le mode d’exécution de l’évaluation.  
  
 `dwTimeout`  
 dans Durée d’attente maximale, en millisecondes, avant le retour de cette méthode. Utilisez **infinite** pour attendre indéfiniment.  
  
 `ppObject`  
 à Retourne un **IDebugObject** représentant l’objet nouvellement créé.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Appelez cette méthode pour créer un objet qui représente une instance d’une classe ou un autre type complexe qui requiert un constructeur, c’est-à-dire un paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
