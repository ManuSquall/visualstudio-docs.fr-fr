---
title: IDebugProgram2::EnumCodePaths | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56cc9580ec2e434066d1c0a3ce674a4111e433af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Récupère une liste des chemins de code pour une position donnée dans un fichier source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```csharp  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszHint`  
 [in] Le mot sous le curseur dans la **Source** ou **code machine** vue dans l’IDE.  
  
 `pStart`  
 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objet représentant le contexte de code actuel.  
  
 `pFrame`  
 [in] Un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) de l’objet qui représente le frame de pile associées avec le point d’arrêt en cours.  
  
 `fSource`  
 [in] Différent de zéro (`TRUE`) dans le cas le **Source** vue, ou zéro (`FALSE`) dans le cas le **code machine** vue.  
  
 `ppEnum`  
 [out] Retourne un [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) objet contenant la liste des chemins de code.  
  
 `ppSafety`  
 [out] Retourne un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) de l’objet qui représente un contexte de code supplémentaire à définir comme un point d’arrêt en cas de chemin d’accès du code sélectionné est ignoré. Cela peut se produire dans le cas d’une expression booléenne court-circuitée, par exemple.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Un chemin d’accès du code décrit le nom d’une méthode ou une fonction qui a été appelée pour atteindre le point actuel de l’exécution du programme. Une liste de chemins d’accès du code représente la pile des appels.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)