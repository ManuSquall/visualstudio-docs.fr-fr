---
title: IDiaFrameData::get_allocatesBasePointer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3aa3150efe4dffb1df2090e8381d471c720c690
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009776"
---
# <a name="idiaframedatagetallocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Récupère un indicateur qui indique si le pointeur de base est alloué pour le code dans cette plage d’adresses. Cette méthode est dépréciée.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne `TRUE` si un pointeur de base est alloué ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette propriété doit être utilisée uniquement par le code dont l’accès est anciennement FPO_DATA, ou lorsque la chaîne de programme retournée par la [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) méthode est `NULL`. Sinon, la chaîne de programme contient toutes les informations nécessaires pour calculer les valeurs de Registre précédentes.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)