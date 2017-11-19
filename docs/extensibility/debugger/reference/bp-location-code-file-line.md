---
title: BP_LOCATION_CODE_FILE_LINE | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords: BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3032c914408e94f430506549ab55e04815ba456c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="bplocationcodefileline"></a>BP_LOCATION_CODE_FILE_LINE
Contient les données pour l’emplacement d’un point d’arrêt sur une ligne spécifique dans un fichier de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _BP_LOCATION_CODE_FILE_LINE {   
   BSTR                     bstrContext;  
   IDebugDocumentPosition2* pDocPos;  
} BP_LOCATION_CODE_FILE_LINE;  
```  
  
## <a name="members"></a>Membres  
 `bstrContext`  
 Le contexte du point d’arrêt, en général, un nom de méthode ou fonction vu sur une pile des appels.  
  
 `pDocPos`  
 Le [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) objet qui représente la position du document du point d’arrêt.  
  
## <a name="remarks"></a>Remarques  
 Cette structure est un membre de la [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) structure dans le cadre d’une union.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)