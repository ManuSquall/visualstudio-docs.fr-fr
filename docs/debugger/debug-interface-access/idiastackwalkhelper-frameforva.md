---
title: IDiaStackWalkHelper::frameForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::frameForVA method
ms.assetid: f35fc61b-f8dd-473a-b583-82c304059422
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7756e73f7137ec18d962ff8199a3f5e339c76144
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926241"
---
# <a name="idiastackwalkhelperframeforva"></a>IDiaStackWalkHelper::frameForVA
Récupère le frame de pile qui contient l’adresse virtuelle spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT frameForVA(   
   ULONGLONG        va,  
   IDiaFrameData**  ppFrame  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `va`  
 [in] L’adresse virtuelle pour les données de trame.  
  
 `ppFrame`  
 [out] Un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objet qui représente le frame de pile à l’adresse spécifiée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)