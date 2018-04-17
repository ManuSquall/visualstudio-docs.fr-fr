---
title: DataKind | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 508058a85d60645fca5e50bc1e6c456da7df7b26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
## <a name="requirements"></a>Spécifications  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)