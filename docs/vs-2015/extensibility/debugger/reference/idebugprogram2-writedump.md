---
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8708751820ca70386e6c9927105384eee9a96a15
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505253"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProgram2::WriteDump](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-writedump).  
  
Écrit un fichier de vidage dans un fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in] Une valeur comprise entre le [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) énumération qui spécifie le type d’image, par exemple, short ou long.  
  
 `pszDumpUrl`  
 [in] L’URL pour l’écriture de l’image mémoire. En règle générale, il s’agit dans le formulaire de `file://c:\path\filename.ext`, mais il peut être n’importe quelle URL valide.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Un vidage de programme inclut généralement le frame de pile actuel, la pile proprement dit, une liste des threads en cours d’exécution dans le programme et éventuellement de mémoire qui possède le programme.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

