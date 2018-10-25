---
title: IDebugProgram2::Terminate | Microsoft Docs
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
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15dcab4ac15a8059d9ca569478957c3a66e277d3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906154"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Met fin au programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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

