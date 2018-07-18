---
title: IDiaStackWalkHelper::frameForVA | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::frameForVA method
ms.assetid: f35fc61b-f8dd-473a-b583-82c304059422
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1191727d407f8c50f3e7901f3137f54f63770639
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468448"
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