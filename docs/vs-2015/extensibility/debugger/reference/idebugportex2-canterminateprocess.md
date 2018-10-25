---
title: IDebugPortEx2::CanTerminateProcess | Microsoft Docs
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
- IDebugPortEx2::CanTerminateProcess
helpviewer_keywords:
- IDebugPortEx2::CanTerminateProcess
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a27a07aac6ee74e6f22cbc9a8881d97e0ac19f1b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865119"
---
# <a name="idebugportex2canterminateprocess"></a>IDebugPortEx2::CanTerminateProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Détermine si un processus peut être arrêté.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CanTerminateProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```csharp  
HRESULT CanTerminateProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pPortProcess`  
 [in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objet représentant la fin du processus.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` si le processus peut être arrêté ; sinon, retourne `S_FALSE`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

