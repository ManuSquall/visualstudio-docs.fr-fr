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
ms.openlocfilehash: 84110c4e7d6a3e940df587811c24d4316f786cf4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="remarks"></a>Remarques  
  
> [!WARNING]
>  En tant que de [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], cette méthode n’est plus utilisée et doit toujours renvoyer `E_NOTIMPL`.  
  
 Cette méthode est appelée lorsque le débogueur se ferme de façon inattendue. Lorsque cette méthode est appelée, le DE reprendre le programme comme si l’utilisateur détachée à partir de celui-ci. Plus aucun événement de débogage ne doit être envoyé. Le programme doit être dans un état où il pouvant être attaché à partir d’une autre instance du débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)