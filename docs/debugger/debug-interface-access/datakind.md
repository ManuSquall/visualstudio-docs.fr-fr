---
title: DataKind | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 8f2b46e420db8addf19ef8694112058bdb8b2f91
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867622"
---
# <a name="datakind"></a>DataKind
Indique la portée d’une valeur de données particulière.  
  
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
 Élément de données est une variable statique de classe.  
  
 DataIsConstant  
 Élément de données est une valeur constante.  
  
## <a name="remarks"></a>Notes  
 Les valeurs dans cette énumération sont retournées par la [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)