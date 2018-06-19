---
title: IDiaSymbol::get_typeIds | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f1ad4aae54096ea2fdcbcac1a68d32fc3b386ad
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470668"
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
Récupère un tableau de valeurs d’identificateur de type spécifique du compilateur pour ce symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cTypeIds`  
 [in] Taille de la mémoire tampon pour stocker les données.  
  
 `pcTypeIds`  
 [out] Retourne le nombre de `typeIds` écrit, ou, si `typeIds` est `NULL`, puis le nombre total d’identificateurs de type disponibles.  
  
 `typeIds[]`  
 [out] Tableau qui doit être remplie avec les identificateurs de type.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)