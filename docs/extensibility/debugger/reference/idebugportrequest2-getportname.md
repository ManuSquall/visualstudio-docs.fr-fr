---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
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
ms.openlocfilehash: 490381f183a19e33fd391b133562fc2a463c6ee9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920844"
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