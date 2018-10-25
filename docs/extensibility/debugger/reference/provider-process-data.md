---
title: PROVIDER_PROCESS_DATA | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 789385ae229214beeb6c2ab9be90a964127e5e13
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819730"
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
Cette structure fournit des informations sur les processus en cours d’exécution sur un ordinateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```csharp  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## <a name="members"></a>Membres  
 Champs  
 Une combinaison d’indicateurs de la [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) énumération, indiquant quels champs sont renseignés.  
  
 ProgramNodes  
 Un [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) structure qui contient un tableau de nœuds de programme.  
  
 fIsDebuggerPresent  
 Différent de zéro (`TRUE`) si le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] débogueur est en cours d’exécution, zéro (`FALSE`) si elle n’est pas.  
  
## <a name="remarks"></a>Notes  
 Cette structure est passée à la [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) méthode où il est renseigné.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)