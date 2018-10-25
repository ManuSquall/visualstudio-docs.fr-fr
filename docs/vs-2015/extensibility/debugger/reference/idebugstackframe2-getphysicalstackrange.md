---
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73024b173eb3cacd3bd75e703225bc3bc6b1eb33
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918556"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient une représentation sous forme de dépendantes de l’ordinateur de la plage d’adresses physiques associés à un frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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

