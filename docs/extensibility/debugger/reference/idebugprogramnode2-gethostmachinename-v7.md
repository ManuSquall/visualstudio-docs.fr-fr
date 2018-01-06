---
title: IDebugProgramNode2::GetHostMachineName_V7 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
ms.assetid: a992f2c9-f68b-4146-8cc2-027753bf7ce6
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 89d88203f4306971128a233237f4d8c7d56054d6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7
DÉCONSEILLÉE. N’UTILISEZ PAS.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHostMachineName_V7 (   
   BSTR* pbstrHostMachineName  
);  
```  
  
```csharp  
int GetHostMachineName_V7 (   
   out string pbstrHostMachineName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrHostMachineName`  
 [out] Retourne le nom de l’ordinateur dans lequel le programme est en cours d’exécution.  
  
## <a name="return-value"></a>Valeur de retour  
 Une implémentation doit toujours renvoyer `E_NOTIMPL`.  
  
## <a name="remarks"></a>Notes  
  
> [!WARNING]
>  En tant que de [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], cette méthode n’est plus utilisée et doit toujours renvoyer `E_NOTIMPL`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)