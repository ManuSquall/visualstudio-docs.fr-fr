---
title: IDebugPortEx2::GetPortProcessId | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d41f01727ed5ee6a1db348da1c253120b1b13c2a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122572"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Obtient l’ID de processus du port lui-même.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPortProcessId (   
   DWORD* pdwProcessId  
);  
```  
  
```csharp  
int GetPortProcessId (   
   out uint pdwProcessId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwProcessId`  
 [out] Retourne l’ID du processus physique du port lui-même.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Dans le runtime Win32, par exemple, cette méthode appelle généralement la fonction Win32 `GetCurrentProcessId` pour obtenir l’ID du processus physique.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)