---
title: DUMPTYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5e886649a7eaa5f9f99eb2e2bfcc48985f12a5e4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949550"
---
# <a name="dumptype"></a>DUMPTYPE
Spécifie la quantité d’état d’un programme (par exemple, les threads en cours d’exécution, les frames de pile et adresse d’instruction en cours) pour vider.  
  
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
 Spécifie un fichier de vidage petit, plus compact.  
  
 DUMP_FULLDUMP  
 Spécifie un vidage volumineux et complet.  
  
## <a name="remarks"></a>Notes  
 Passé en tant qu’argument à la [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)