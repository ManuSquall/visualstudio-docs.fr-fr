---
title: DUMPTYPE | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DUMPTYPE
helpviewer_keywords: DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 26e2836215ac5563a6ebaefb9d31d682348c7e89
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="dumptype"></a>DUMPTYPE
Spécifie la quantité d’état d’un programme (par exemple, les threads en cours d’exécution, les frames de pile et adresse d’instruction en cours) pour faire un dump.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
typedef DWORD DUMPTYPE;  
```  
  
```csharp  
public enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
```  
  
## <a name="members"></a>Membres  
 DUMP_MINIDUMP  
 Spécifie un fichier de vidage de petite taille, compact.  
  
 DUMP_FULLDUMP  
 Spécifie un vidage volumineux, terminé.  
  
## <a name="remarks"></a>Remarques  
 Est passé comme argument à la [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)