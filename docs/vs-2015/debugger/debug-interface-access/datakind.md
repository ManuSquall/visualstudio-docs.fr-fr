---
title: DataKind | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6a72d1093bc8acd9aae788ff357aee2efeb9e52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197636"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indique l’étendue particulière d’une valeur de données.  
  
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
 Impossible de déterminer le symbole de données.  
  
 DataIsLocal  
 L’élément de données est une variable locale.  
  
 DataIsStaticLocal  
 Data Item est une variable locale statique.  
  
 DataIsParam  
 L’élément de données est un paramètre formel.  
  
 DataIsObjectPtr  
 L’élément de données est un pointeur d’objet ( `this` ).  
  
 DataIsFileStatic  
 L’élément de données est une variable de portée de fichier.  
  
 DataIsGlobal  
 L’élément de données est une variable globale.  
  
 DataIsMember  
 L’élément de données est une variable membre de l’objet.  
  
 DataIsStaticMember  
 Data Item est une variable statique de classe.  
  
 DataIsConstant  
 L’élément de données est une valeur constante.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de cette énumération sont retournées par la méthode [IDiaSymbol :: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst. h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
