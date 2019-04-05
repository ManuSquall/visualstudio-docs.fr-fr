---
title: CV_access_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ce5997555b37cf5ab30f091e7124b5025284c0e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948338"
---
# <a name="cvaccesse"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spécifie l’étendue de visibilité (niveau d’accès) des fonctions membres et des variables.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Éléments  
 CV_private  
 Membre possède un accès privé.  
  
 CV_protected  
 Membre possède un accès protégé.  
  
 CV_public  
 Membre possède un accès public.  
  
## <a name="remarks"></a>Notes  
 Le `friend` spécificateur d’accès n’est pas inclus ici, car il est généralement utilisé par des fonctions non-membres qui ont accès à des éléments à la fois privés et protégés de la classe. Utilisez le [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) méthode pour rechercher des symboles avec `SymTagFriend` accès.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
