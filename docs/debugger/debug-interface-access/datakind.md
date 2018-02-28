---
title: DataKind | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7fecbec475aee44efd9a91a24ec933dbbbcb17e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="datakind"></a>DataKind
Indique l’étendue spécifique d’une valeur de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>Éléments  
 DataIsUnknown  
 Symbole de données ne peut pas être déterminé.  
  
 DataIsLocal  
 Élément de données est une variable locale.  
  
 DataIsStaticLocal  
 Élément de données est une variable locale statique.  
  
 DataIsParam  
 Élément de données est un paramètre formel.  
  
 DataIsObjectPtr  
 Élément de données est un pointeur d’objet (`this`).  
  
 DataIsFileStatic  
 Élément de données est une variable de portée de fichier.  
  
 DataIsGlobal  
 Élément de données est une variable globale.  
  
 DataIsMember  
 Élément de données est une variable de membre d’objet.  
  
 DataIsStaticMember  
 Élément de données est une variable de classe statique.  
  
 DataIsConstant  
 Élément de données est une valeur constante.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de cette énumération sont retournées par la [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)