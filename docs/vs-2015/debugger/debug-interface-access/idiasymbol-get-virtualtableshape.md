---
title: IDiaSymbol::get_virtualTableShape | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualTableShape method
ms.assetid: 92360cbd-0761-446e-93f9-04dc8f4b66c6
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8dfc91a63634f47cc2a8bc16d0dfbede1e14abf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839905"
---
# <a name="idiasymbolget_virtualtableshape"></a>IDiaSymbol::get_virtualTableShape
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère l’interface de symboles du type de la table virtuelle pour un type défini par l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_virtualTableShape (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Retourne un objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant la table virtuelle pour un type défini par l’utilisateur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou code d’erreur.  
  
> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
