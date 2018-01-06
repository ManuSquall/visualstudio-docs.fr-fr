---
title: IDebugProgram2::WriteDump | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::WriteDump
helpviewer_keywords: IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 40fcd345a2a07a0ebdcf9e984b060cc81e946fc3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Écrit un fichier de vidage dans un fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `DumpType`  
 [in] Une valeur à partir de la [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) énumération qui spécifie le type d’image, par exemple, short ou long.  
  
 `pszDumpUrl`  
 [in] L’URL pour écrire le vidage d’à. En règle générale, il s’agit sous la forme de `file://c:\path\filename.ext`, mais il peut être une URL valide.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Une image de programme inclut généralement le frame de pile en cours, la pile, la liste des threads en cours d’exécution dans le programme et éventuellement de mémoire que le programme est propriétaire.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)