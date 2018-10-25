---
title: IDiaSectionContrib::get_addressOffset | Microsoft Docs
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
- IDiaSectionContrib::get_addressOffset method
ms.assetid: 4d569323-0e11-456d-9f92-a218bf292ecf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5a8b4efc531691d484c9f1a4afbf4ae8ce06ae5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858782"
---
# <a name="idiasectioncontribgetaddressoffset"></a>IDiaSectionContrib::get_addressOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère la partie de l’adresse de la contribution décalage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne la partie de l’adresse de la contribution décalage.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



