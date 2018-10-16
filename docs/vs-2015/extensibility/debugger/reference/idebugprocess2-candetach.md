---
title: IDebugProcess2::CanDetach | Microsoft Docs
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
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 66ff1c80a8b0a82f38185e7c42fadda79a8fd63c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285595"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Détermine si le Gestionnaire de session de débogage (SDM) pouvez détacher le processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK.` retourne `S_FALSE` si le débogueur ne peut pas détacher du processus. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

