---
title: IDebugProcess2::Detach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 633ac46a70ffa7a6becfa0648b53e8f683f838b3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027803"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Détache le débogueur à partir de ce processus en détachant de tous les programmes dans le processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Detach(   
   void   
);  
```  
  
```csharp  
int Detach();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Tous les programmes et le processus de continuent à s’exécuter, mais ne font plus partie de la session de débogage. Une fois l’opération de détachement débogage complète, pas d’autres événements pour ce processus (et ses programmes) seront envoyés.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)