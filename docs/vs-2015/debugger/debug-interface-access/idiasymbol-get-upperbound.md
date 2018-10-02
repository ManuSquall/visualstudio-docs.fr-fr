---
title: IDiaSymbol::get_upperBound | Microsoft Docs
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
- IDiaSymbol::get_upperBound method
ms.assetid: a77dcafa-ea3f-45da-826d-8f9b4489a03f
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 03bc9920a30fccd63e6349bde45fbc52a2c54d20
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516594"
---
# <a name="idiasymbolgetupperbound"></a>IDiaSymbol::get_upperBound
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaSymbol::get_upperBound](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-upperbound).  
  
Récupère un symbole qui représente la limite supérieure d’une dimension de tableau FORTRAN.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_upperBound (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet qui représente la limite supérieure d’une dimension de tableau FORTRAN.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



