---
title: 'IDebugProcessSecurity :: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ec541b6dc4ccae57628d4b33e7c188008da6edae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187964"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode permet au fournisseur de port d’afficher un avertissement avant que l’utilisateur ne soit attaché à un processus non sécurisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Les valeurs de retour sont les suivantes :  
  
- `S_OK`: L’attachement au processus est sécurisé et aucune boîte de dialogue d’avertissement ne s’affiche.  
  
- `S_FALSE`: L’attachement peut être un problème de sécurité et une boîte de dialogue avec un avertissement s’affiche.  
  
- `FAILURE`: L’attachement au processus échoue.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
