---
title: IDebugPortRequest2::GetPortName | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c81bdc6586766cb4a241bf29e653cb1b10f66f2f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
 Le [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interface est généralement passée à partir d’un package de débogage (le client) à un fournisseur de port (serveur) pour obtenir une connexion à un port. Le package de débogage et le fournisseur de port connaissent les choix possibles pour le port. Si une chaîne simple peut décrire le port, puis la `IDebugPortRequest2::GetPortName` méthode possède suffisamment d’informations pour établir la connexion. Dans le cas contraire, les interfaces supplémentaires peuvent être fournies par le client, ce qui peut être obtenu par le serveur à l’aide de `IDebugPortRequest2::QueryInterface`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)