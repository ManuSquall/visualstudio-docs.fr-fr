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
ms.openlocfilehash: 401eb759523ed1a33d24c3a298db0b3de2b7d5a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575877"
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
|DOCUMENTNAMETYPE_TITLE|Obtient le nom tel qu’il apparaît dans la barre de titre de la visionneuse.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Obtient le nom de fichier sans chemin d’accès.|  
|DOCUMENTNAMETYPE_URL|Obtient l’URL du document.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Obtient le titre ajouté avec l’énumération pour l’identification.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)