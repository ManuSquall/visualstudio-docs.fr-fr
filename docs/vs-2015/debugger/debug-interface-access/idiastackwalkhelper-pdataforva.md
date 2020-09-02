---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5af921caa989d7279bb9f52751c452d91045cf3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150090"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Retourne le bloc de données PDATA associé à l’adresse virtuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `va`  
 dans Spécifie l’adresse virtuelle des données à obtenir.  
  
 `cbData`  
 dans Taille des données en octets à obtenir.  
  
 `pcbData`  
 à Retourne la taille réelle des données en octets qui ont été obtenues.  
  
 `pbData`  
 [in, out] Mémoire tampon qui est remplie avec les données demandées. Ne peut pas être `NULL`.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’existe aucun pData pour l’adresse spécifiée. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Le PDATA (la section nommée « . pdata ») d’un compiland contient des informations sur la gestion des exceptions pour les fonctions.  
  
 L’appelant sait la quantité de données à retourner pour que l’appelant n’ait pas besoin de demander la quantité de données disponibles. Par conséquent, il est acceptable pour une implémentation de cette méthode de retourner une erreur si le `pbData` paramètre est `NULL` .  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
