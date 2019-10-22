---
title: TEXT_DOCUMENT_ARRAY, structure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- TEXT_DOCUMENT_ARRAY Structure
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b52b382aa1e91e509672728a3c8f931bfeae27a9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572971"
---
# <a name="text_document_array-structure"></a>TEXT_DOCUMENT_ARRAY (structure)
Tableau d’objets d' [interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md) . Les membres sont alloués avec CoTaskMemAlloc.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef struct tagTEXT_DOCUMENT_ARRAY{    DWORD dwCount;    [size_is(dwCount)] IDebugDocumentText **Members;} TEXT_DOCUMENT_ARRAY;  
```  
  
## <a name="members"></a>Membres  
 `dwCount`  
 Nombre de documents.  
  
 `Members`  
 Ensemble de documents.  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)