---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42ab689c5c94fcf0200775d9fdd59ac2a0f7202c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916975"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Retourne le bloc de données PDATA associé à l’adresse virtuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `va`  
 [in] Spécifie l’adresse virtuelle des données à obtenir.  
  
 `cbData`  
 [in] La taille des données en octets à obtenir.  
  
 `pcbData`  
 [out] Retourne la taille réelle des données en octets qui ont été obtenues.  
  
 `pbData`  
 [in, out] Une mémoire tampon est remplie avec les données demandées. Ne peut pas être `NULL`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’existe aucun PDATA pour l’adresse spécifiée. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Remarques  
 PDATA (la section nommée « .pdata ») d’un module contient des informations sur la gestion des exceptions de fonctions.  
  
 L’appelant sait que la quantité de données doit être retournée afin de l’appelant n’a pas besoin de poser pour la quantité de données est disponible. Par conséquent, il est acceptable pour une implémentation de cette méthode retourne une erreur si le `pbData` paramètre est `NULL`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)