---
title: CV_access_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 373149884078b58926493fd7f37756ddb4eb8829
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838753"
---
# <a name="cvaccesse"></a>CV_access_e
Spécifie l’étendue de visibilité (niveau d’accès) des fonctions membres et des variables.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
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
  
## <a name="requirements"></a>Spécifications  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)