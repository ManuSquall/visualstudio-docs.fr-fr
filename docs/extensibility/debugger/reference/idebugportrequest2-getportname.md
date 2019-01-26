---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd5033926987ef1a2673380a4f7d76dc1b0cb0c0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962730"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Obtient le nom du port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrPortName`  
 [out] Retourne le nom du port.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interface est généralement passée à partir d’un package de débogage (le client) à un fournisseur de port (le serveur) pour obtenir une connexion à un port. Le package de débogage et le fournisseur de port connaissent les choix possibles pour le port. Si une chaîne simple peut décrire le port, puis la `IDebugPortRequest2::GetPortName` méthode possède suffisamment d’informations pour établir la connexion. Sinon, les interfaces supplémentaires peuvent être fournies par le client, ce qui peut être obtenu par le serveur à l’aide `IDebugPortRequest2::QueryInterface`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)