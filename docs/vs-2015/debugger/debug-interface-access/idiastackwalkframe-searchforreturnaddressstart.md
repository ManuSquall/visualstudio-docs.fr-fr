---
title: IDiaStackWalkFrame::searchForReturnAddressStart | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddressStart method
ms.assetid: 47660b9b-6e4f-4dfa-88ab-63dce28f7412
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4156e22e32eaa5d79da0df8942a0ef082eb6c41
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755111"
---
# <a name="idiastackwalkframesearchforreturnaddressstart"></a>IDiaStackWalkFrame::searchForReturnAddressStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recherche dans le frame de pile spécifié pour une adresse de retour à ou près de l’adresse spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT searchForReturnAddressStart (   
   IDiaFrameData* frame,  
   ULONGLONG      startAddress,  
   ULONGLONG*     returnAddress  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `frame`  
 [in] Un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objet qui représente le frame de pile actuel.  
  
 `startAddress`  
 [in] Une adresse de mémoire virtuelle à partir duquel commencer la recherche.  
  
 `returnAddress`  
 [out] Retourne la fonction le plus proche de retour adresse `startAddress`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



