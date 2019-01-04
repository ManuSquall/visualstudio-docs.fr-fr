---
title: IDebugProgram2::Terminate | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: c4ef57e3cbc11eb6e1b8e266d1a0799ef46ba406
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872094"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Met fin au programme.  
  
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
 Si possible, le programme sera terminé et déchargé du processus ; Sinon, le moteur de débogage (dé) sera effectuer tout nettoyage nécessaire.  
  
 Cette méthode ou la [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) méthode est appelée par l’IDE, généralement en réponse à l’utilisateur d’arrêter le débogage de tous les. L’implémentation de cette méthode doit, terminer dans l’idéal, le programme au sein du processus. Si ce n’est pas possible, l’Allemagne doit empêcher le programme en cours d’exécution d’autres dans ce processus (et effectuer tout nettoyage nécessaire). Si le `IDebugProcess2::Terminate` méthode a été appelée par l’IDE, l’ensemble du processus va être interrompue après le `IDebugProgram2::Terminate` méthode est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)