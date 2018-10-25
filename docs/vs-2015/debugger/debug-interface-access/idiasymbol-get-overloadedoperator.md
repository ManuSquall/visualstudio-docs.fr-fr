---
title: IDiaSymbol::get_overloadedOperator | Microsoft Docs
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
- IDiaSymbol::get_overloadedOperator method
ms.assetid: 257a9894-e980-47ae-bdc0-c5e2293ea734
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ed89f1333427cfdf2cc3c41222ed9d16fe68efa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951286"
---
# <a name="idiasymbolgetoverloadedoperator"></a>IDiaSymbol::get_overloadedOperator
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un indicateur qui spécifie si le type de données défini par l’utilisateur a des opérateurs surchargés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_overloadedOperator (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne `TRUE` si le type de données défini par l’utilisateur a surchargé opérateurs ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



