---
title: IDiaStackWalkHelper::searchForReturnAddressStart | Microsoft Docs
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
- IDiaStackWalkHelper::searchForReturnAddressStart method
ms.assetid: 0a33142e-5d31-44ea-874a-a2e94d95cbd2
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e00afc5468cf7bc9fc499a055683bd27775332f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907558"
---
# <a name="idiastackwalkhelpersearchforreturnaddressstart"></a>IDiaStackWalkHelper::searchForReturnAddressStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recherche dans le frame de pile spécifié pour une adresse de retour à ou près de l’adresse de pile spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT searchForReturnAddressStart(   
   IDiaFrameData*  frame,  
   ULONGLONG       startAddress,  
   ULONGLONG*      returnAddress  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `frame`  
 [in] Un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objet qui représente le frame de pile actuel.  
  
 `startAddress`  
 [in] Une adresse de mémoire virtuelle à partir duquel commencer la recherche.  
  
 `ReturnAddress`  
 [out] Retourne la fonction le plus proche de retour adresse `startAddress`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



