---
title: Constantes TEXT_DOC_ATTR | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: TEXT_DOC_ATTR
apilocation: scrobj.dll
helpviewer_keywords: TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130895e0e70b1044fab5d5ab406f940b036c37f0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="textdocattr-constants"></a>Constantes TEXT_DOC_ATTR
Décrit les attributs du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|Le document est en lecture seule.|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|Le document est le fichier primaire de cette arborescence du document.|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|Le document est un processus de travail.|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|Le document est un fichier de script.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)