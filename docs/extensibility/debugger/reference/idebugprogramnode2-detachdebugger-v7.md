---
title: IDebugProgramNode2::DetachDebugger_V7 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: af2f9e5851e53c86fb5466e7fc2cdfe515b5fb21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
DÉCONSEILLÉE. N’UTILISEZ PAS.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Une implémentation doit toujours renvoyer `E_NOTIMPL`.  
  
## <a name="remarks"></a>Notes  
  
> [!WARNING]
>  En tant que de [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], cette méthode n’est plus utilisée et doit toujours renvoyer `E_NOTIMPL`.  
  
 Cette méthode est appelée lorsque le débogueur se ferme de façon inattendue. Lorsque cette méthode est appelée, le DE reprendre le programme comme si l’utilisateur détachée à partir de celui-ci. Plus aucun événement de débogage ne doit être envoyé. Le programme doit être dans un état où il pouvant être attaché à partir d’une autre instance du débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)