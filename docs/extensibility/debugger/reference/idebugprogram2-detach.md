---
title: IDebugProgram2::Detach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Detach
helpviewer_keywords:
- IDebugProgram2::Detach
ms.assetid: 5e8d88b0-a8d4-4746-88c0-ad332ee73f33
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 44ad03f53e6bc8e96f762d83a0b0968ecb028184
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880232"
---
# <a name="idebugprogram2detach"></a>IDebugProgram2::Detach
Détache un moteur de débogage à partir du programme.  
  
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
 Un programme détaché continue à s’exécuter, mais il ne fait plus partie de la session de débogage. Aucun événement de débogage de programme plus n’est envoyés une fois que le moteur de débogage est détaché.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)