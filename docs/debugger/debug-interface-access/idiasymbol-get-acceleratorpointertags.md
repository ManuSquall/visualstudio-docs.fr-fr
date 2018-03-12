---
title: IDiaSymbol::get_acceleratorPointerTags | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e5190496258cfb4ed66334e10a3d727a1c9555b6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Retourne toutes les valeurs de balise de pointeur accélérateur qui correspondent à une fonction de stub d’accélérateur C++ AMP.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cnt`  
 [in] La taille du tableau de sortie `pPointerTags`.  
  
 `pcnt`  
 [out] Le nombre de balises de pointeur accélérateur dans la fonction de stub d’accélérateur C++ AMP.  
  
 `pPointerTags`  
 [out] A `DWORD` pointeur du tableau qui est rempli avec les valeurs de balise de pointeur accélérateur dans la fonction de stub d’accélérateur C++ AMP.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée sur une `IDiaSymbol` interface qui correspond à une fonction de stub d’accélérateur C++ AMP.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)