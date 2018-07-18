---
title: IDiaLineNumber::get_columnNumberEnd | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3d7dd317cf24f2580d72fdc05ccbb8f60668fd1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31460158"
---
# <a name="idialinenumbergetcolumnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
Récupère le numéro de colonne source basée sur celle où l’expression ou une instruction se termine.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_columnNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le numéro de colonne où l’expression ou une instruction se termine. Si la valeur est zéro, les informations de fin de colonne ne sont pas présentes.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 La valeur de la colonne retournée par cette méthode est un octet dans la ligne à la position de décalage après le dernier caractère de l’instruction de la ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)