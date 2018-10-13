---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5380df694196f8a0ec8fea11aefd429ccfeca039
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239328"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode permet le fournisseur de port afficher un avertissement avant que l’utilisateur joint à un processus non sécurisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Les valeurs de retour sont comme suit :  
  
-   `S_OK`: L’attachement au processus est sécurisé et aucune boîte de dialogue d’avertissement n’est affiché.  
  
-   `S_FALSE`: Attachement peut être un problème de sécurité et une boîte de dialogue avec un avertissement s’affiche.  
  
-   `FAILURE`: L’attachement au processus échoue.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)

