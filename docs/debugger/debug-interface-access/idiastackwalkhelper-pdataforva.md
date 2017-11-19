---
title: IDiaStackWalkHelper::pdataForVA | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4925a4a37395dd53fabb1d8d7ba7f80bc5cc6c93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
 [dans, out] Une mémoire tampon est remplie avec les données demandées. Ne peut pas être `NULL`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’existe aucun PDATA pour l’adresse spécifiée. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Remarques  
 PDATA (la section nommée « .pdata ») d’un module contient des informations sur la gestion des exceptions de fonctions.  
  
 L’appelant sait que la quantité de données doit être retourné pour l’appelant n’a pas besoin pour poser pour la quantité de données est disponible. Par conséquent, il est acceptable pour une implémentation de cette méthode pour retourner une erreur si le `pbData` paramètre est `NULL`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)