---
title: IDiaSymbol::get_types | Microsoft Docs
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
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c611805e2a077caec0a617deda8ac744e0b4e1a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817313"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un tableau de types spécifiques au compilateur pour ce symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cTypes`  
 [in] Taille de la mémoire tampon devant contenir les données.  
  
 `pcTypes`  
 [out] Retourne le nombre de types écrits, ou, si le `types` paramètre est `NULL`, puis le nombre total de types disponibles.  
  
 `types[]`  
 [out] Un tableau qui doit être rempli avec le [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) les objets qui représentent tous les types de ce symbole.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



