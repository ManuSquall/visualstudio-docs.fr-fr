---
title: IDebugPortRequest2::GetPortName | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortRequest2::GetPortName
helpviewer_keywords: IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5906560574836390656254055130af3275fa4f76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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