---
title: 'IDebugProcess2 :: GetPort | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetPort
helpviewer_keywords:
- IDebugProcess2::GetPort
ms.assetid: e39b6e5a-64eb-48cf-a53d-da4fdb968e2d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d77310abb6643ef6e9c17c21b5199d5889b1492
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188069"
---
# <a name="idebugprocess2getport"></a>IDebugProcess2::GetPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le port sur lequel le processus s’exécute.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetPort(   
   IDebugPort2** ppPort  
);  
```  
  
```csharp  
int GetPort(   
   out IDebugPort2 ppPort  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppPort`  
 à Retourne un objet [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) qui représente le port sur lequel le processus a été lancé.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
