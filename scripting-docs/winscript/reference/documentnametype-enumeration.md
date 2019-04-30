---
title: Énumération DOCUMENTNAMETYPE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 5ee258602c47951f4731dc1378542cc83d57d72b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955210"
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