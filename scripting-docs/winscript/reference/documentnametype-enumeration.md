---
title: Énumération DOCUMENTNAMETYPE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31e304cfbb0ed7cd19b832d7ed7c33ccc2c930c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094768"
---
# <a name="documentnametype-enumeration"></a>Énumération DOCUMENTNAMETYPE
Décrit le type à obtenir pour un document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|Obtient le nom tel qu’il apparaît dans l’arborescence de l’application.|  
|DOCUMENTNAMETYPE_TITLE|Obtient le nom tel qu’il apparaît dans la barre de titre.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Obtient le nom de fichier sans un chemin d’accès.|  
|DOCUMENTNAMETYPE_URL|Obtient l’URL du document.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Obtient le titre ajouté avec énumération pour l’identification.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)