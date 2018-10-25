---
title: IDiaSymbol::get_upperBound | Microsoft Docs
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
- IDiaSymbol::get_upperBound method
ms.assetid: a77dcafa-ea3f-45da-826d-8f9b4489a03f
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f62369de4c69fcff9cf3b3af01467d51d9327bf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938290"
---
# <a name="idiasymbolgetupperbound"></a>IDiaSymbol::get_upperBound
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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



