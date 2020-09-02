---
title: 'IDebugPortRequest2 :: GetPortName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: afed0bb700f41f7c39551f1a9bc7779f36b0ae57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188366"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le nom du port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 à Retourne le nom du port.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 L’interface [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) est généralement passée d’un package de débogage (le client) à un fournisseur de port (serveur) pour obtenir une connexion à un port. Le package de débogage et le fournisseur de ports prennent en charge les choix possibles pour le port. Si une chaîne simple peut décrire le port, la `IDebugPortRequest2::GetPortName` méthode a suffisamment d’informations pour établir la connexion. Dans le cas contraire, des interfaces supplémentaires peuvent être fournies par le client, qui peut être obtenu par le serveur à l’aide de `IDebugPortRequest2::QueryInterface` .  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
