---
title: DataKind | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93c67b0199524072bf45558dc1713c760567495c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760471"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indique la portée d’une valeur de données particulière.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum DataKind {   
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



