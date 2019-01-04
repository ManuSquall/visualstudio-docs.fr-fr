---
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56121c7a0e58d90fd3ab0384a39916c102056c50
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958694"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Obtient une représentation sous forme de dépendantes de l’ordinateur de la plage d’adresses physiques associés à un frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `paddrMin`  
 [out] Retourne l’adresse physique la plus faible associée à ce frame de pile.  
  
 `paddrMax`  
 [out] Retourne l’adresse physique le plus élevé associé à ce frame de pile.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les informations retournées par cette méthode sont utilisées par le Gestionnaire de session de débogage (SDM) pour trier les frames de pile.  
  
 Il est supposé que la pile des appels se développe vers le bas, autrement dit, que des frames de pile sont ajoutés à des adresses de mémoire inférieures de plus en plus. Une architecture d’exécution doit fournir les plages de pile physique qui correspondent à cette hypothèse.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)