---
title: IDebugProgramPublisher2::SetDebuggerPresent | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
helpviewer_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 571da5e7baa720dc2e26fc629e2887cd0e3bdfa9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948935"
---
# <a name="idebugprogrampublisher2setdebuggerpresent"></a>IDebugProgramPublisher2::SetDebuggerPresent
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Indique le serveur de publication du programme qu’un débogueur est présent et en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetDebuggerPresent(  
   BOOL fDebuggerPresent  
);  
```  
  
```csharp  
int SetDebuggerPresent(  
   int fDebuggerPresent  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fDebuggerPresent`  
 [in] Valeur différente de zéro (`TRUE`) si un débogueur est présent, zéro (`FALSE`) si elle n’est pas.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 La présence ou l’absence d’un débogueur est reflétée dans les données retournées à partir de la [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) méthode : la valeur retournée il est définie ou désactivée par un appel antérieur à la `SetDebuggerPresent` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
