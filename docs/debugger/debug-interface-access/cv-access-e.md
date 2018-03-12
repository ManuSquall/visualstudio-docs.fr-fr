---
title: CV_access_e | Documents Microsoft
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
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 30914c63f5577519a7451cb6d1aee6d651161678
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cvaccesse"></a>CV_access_e
Spécifie l’étendue de visibilité (niveau d’accès) des variables et fonctions membres.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Éléments  
 CV_private  
 Membre possède un accès privé.  
  
 CV_protected  
 Membre avec accès protégé.  
  
 CV_public  
 Membre possède un accès public.  
  
## <a name="remarks"></a>Notes  
 Le `friend` spécificateur d’accès n’est pas inclus ici, car il est généralement utilisée par les fonctions non membres qui ont accès aux éléments privés et protégés de la classe. Utilisez le [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) méthode pour rechercher des symboles avec `SymTagFriend` accès.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)