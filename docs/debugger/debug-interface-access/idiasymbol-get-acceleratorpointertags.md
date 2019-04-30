---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c1724ee3e81ac00ed048f323105842361ec22bc7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827292"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Retourne toutes les valeurs de balise de pointeur accélérateur qui correspondent à une fonction de stub d’accélérateur C++ AMP.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cnt`  
 [in] La taille du tableau de sortie `pPointerTags`.  
  
 `pcnt`  
 [out] Le nombre de balises de pointeur accélérateur dans la C++ AMP accélérateur stub (fonction).  
  
 `pPointerTags`  
 [out] Un `DWORD` pointeur du tableau qui est rempli avec les valeurs de balise de pointeur accélérateur dans la C++ AMP accélérateur stub (fonction).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée sur un `IDiaSymbol` interface qui correspond à une fonction de stub d’accélérateur C++ AMP.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
