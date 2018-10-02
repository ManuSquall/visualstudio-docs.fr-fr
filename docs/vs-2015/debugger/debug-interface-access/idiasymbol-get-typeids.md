---
title: IDiaSymbol::get_typeIds | Microsoft Docs
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
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f932e5d5d2323be84163422c4f007ad60ccd90b5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504156"
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaSymbol::get_typeIds](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-typeids).  
  
Récupère un tableau de valeurs d’identificateur de type spécifique au compilateur pour ce symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cTypeIds`  
 [in] Taille de la mémoire tampon devant contenir les données.  
  
 `pcTypeIds`  
 [out] Retourne le nombre de `typeIds` écrit, ou, si `typeIds` est `NULL`, puis le nombre total d’identificateurs de type disponibles.  
  
 `typeIds[]`  
 [out] Un tableau qui doit être remplie avec les identificateurs de type.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



