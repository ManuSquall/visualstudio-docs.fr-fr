---
title: IDiaSymbol::get_length | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_length method
ms.assetid: cc62f028-d195-4fbf-93bc-10b08bef52d2
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94cdb52f21a5dd8a6bc41eaf21092013abffdc3e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetlength"></a>IDiaSymbol::get_length
Récupère le nombre de bits ou d’octets de mémoire utilisée par l’objet représenté par ce symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_length (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le nombre d’octets ou bits de mémoire utilisée par l’objet représenté par ce symbole.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Remarques  
 Si le [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md) du symbole est `LocIsBitField`, la longueur retournée par cette méthode est en bits ; sinon, la longueur est en octets pour tous les autres types d’emplacement.  
  
## <a name="example"></a>Exemple  
  
```C++  
IDiaSymbol* pSymbol;  
ULONGLONG   length;  
pSymbol->get_length( &length );  
```  
  
## <a name="requirements"></a>Spécifications  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v7.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md)