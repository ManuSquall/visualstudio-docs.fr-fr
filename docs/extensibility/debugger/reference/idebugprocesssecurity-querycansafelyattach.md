---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5315281b904a6a4144f8e06780048e25cd5e0221
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Cette méthode permet d’afficher un avertissement avant que l’utilisateur joint à un processus non sécurisé, le fournisseur de port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Les valeurs de retour sont comme suit :  
  
-   `S_OK`: L’attachement au processus est sécurisé et aucune boîte de dialogue d’avertissement ne s’affiche.  
  
-   `S_FALSE`: L’attachement peut être un problème de sécurité et une boîte de dialogue avec un avertissement s’affiche.  
  
-   `FAILURE`: L’attachement au processus échoue.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)