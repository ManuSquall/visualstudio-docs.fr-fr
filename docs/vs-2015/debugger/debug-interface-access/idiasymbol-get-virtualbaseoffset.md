---
title: IDiaSymbol::get_virtualBaseOffset | Microsoft Docs
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
- IDiaSymbol::get_virtualBaseOffset method
ms.assetid: 103b034f-36c4-42d5-aa34-1449a1e66d03
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea748a5b307bf0ee886681d13558d4459638b711
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508487"
---
# <a name="idiasymbolgetvirtualbaseoffset"></a>IDiaSymbol::get_virtualBaseOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaSymbol::get_virtualBaseOffset](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset).  
  
Récupère le décalage dans la table de fonctions virtuelles d’une fonction virtuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_virtualBaseOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le décalage dans la table de fonctions virtuelles d’une fonction virtuelle.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



