---
title: IDebugProgram2::Terminate | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5eb14280947ff93a4a0c2ab6d2cf025037fc06aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115835"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Termine le programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Si possible, le programme sera arrêté et déchargé du processus ; dans le cas contraire, le moteur de débogage (DE) effectue tout nettoyage nécessaire.  
  
 Cette méthode ou la [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) méthode est appelée par l’IDE, généralement en réponse à l’utilisateur d’arrêter le débogage de tous les. L’implémentation de cette méthode doit terminer dans l’idéal, le programme au sein du processus. Si ce n’est pas possible, le DE doit empêcher le programme en cours d’exécution d’autres dans ce processus (et effectuer tout nettoyage nécessaire). Si le `IDebugProcess2::Terminate` méthode a été appelée par l’IDE, la totalité du processus va se terminer après le `IDebugProgram2::Terminate` méthode est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Arrêter](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)