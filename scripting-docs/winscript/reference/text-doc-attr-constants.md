---
title: Constantes TEXT_DOC_ATTR | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- TEXT_DOC_ATTR
apilocation:
- scrobj.dll
helpviewer_keywords:
- TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3604c06b6cb36cc4ff7ef6c76348b5ece53bed61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572982"
---
# <a name="text_doc_attr-constants"></a>Constantes TEXT_DOC_ATTR
Décrit les attributs du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|valeur|Description|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|Le document est en lecture seule.|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|Le document est le fichier principal de cette arborescence de documents.|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|Le document est un Worker.|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|Le document est un fichier de script.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)