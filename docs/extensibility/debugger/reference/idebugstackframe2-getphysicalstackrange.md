---
title: IDebugStackFrame2::GetPhysicalStackRange | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e90137ada43a127dc3c7eac3c98620f3a846d024
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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
 [out] Retourne l’adresse physique le plus bas associé à ce frame de pile.  
  
 `paddrMax`  
 [out] Retourne l’adresse physique le plus élevé associé à ce frame de pile.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les informations retournées par cette méthode sont utilisées par le Gestionnaire de session de débogage (SDM) pour trier les frames de pile.  
  
 Il est supposé que la pile des appels se développe vers le bas, autrement dit, que des frames de pile sont ajoutés à des adresses mémoire plus en plus bas. Une architecture d’exécution doit fournir des plages de pile correspondant à cette hypothèse.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)