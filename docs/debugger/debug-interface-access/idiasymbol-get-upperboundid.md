---
title: IDiaSymbol::get_upperBoundId | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_upperBoundId method
ms.assetid: ddfa1617-bd0f-4187-ba77-a225bab93a95
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a08f0d6052fcdb6346faef4080f971e9c18ac51b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetupperboundid"></a>IDiaSymbol::get_upperBoundId
Récupère l’identificateur de symbole de la limite supérieure d’une dimension de tableau FORTRAN.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_upperBoundId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne l’ID de symbole qui représente la limite supérieure d’une dimension de tableau FORTRAN.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Remarques  
 L’identificateur est une valeur unique créée par le SDK DIA pour marquer tous les symboles de manière unique.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)