---
title: CV_call_e | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d4d001b1c6c2df10b8263fa9b0c5f5be360c9e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494741"
---
# <a name="cvcalle"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CV_call_e](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/cv-call-e).  
  
Spécifie la convention d’appel pour une fonction.  
  
> [!NOTE]
>  Seules les valeurs d’énumération courants sont décrits ici. L’énumération complète est disponible dans le fichier d’en-tête cvconst.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>Éléments  
 CV_CALL_NEAR_C  
 Spécifie une convention d’appel de fonction à l’aide d’un push proche de droite à gauche. La fonction appelante efface la pile.  
  
 CV_CALL_NEAR_FAST  
 Spécifie une convention d’appel de fonction à l’aide d’un push de gauche à droite quasi avec les registres. La fonction appelée utilise la somme des octets de paramètre pour effacer la pile.  
  
 CV_CALL_NEAR_STD  
 Spécifie une convention d’appel de fonction via un appel standard quasiment (push de droite à gauche).  
  
 CV_CALL_NEAR_SYS  
 Spécifie une convention d’appel de fonction à l’aide d’un appel système proche.  
  
 CV_CALL_THISCALL  
 Spécifie une convention d’appel de fonction à l’aide `this` appeler (`this` pointeur passé dans le Registre).  
  
 CV_CALL_CLRCALL  
 Spécifie une convention d’appel de fonction utilisée par le Common Language Runtime (CLR) (également appelé un code managé convention d’appel).  
  
## <a name="remarks"></a>Notes  
 Les valeurs dans cette énumération sont retournées par un appel à la [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)



