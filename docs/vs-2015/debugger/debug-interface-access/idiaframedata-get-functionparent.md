---
title: IDiaFrameData::get_functionParent | Microsoft Docs
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
- IDiaFrameData::get_functionParent method
ms.assetid: f00b9ab1-d4da-4818-973a-58f8f0e66769
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f54f157503997f693a4333e3d364b722cf75707
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922066"
---
# <a name="idiaframedatagetfunctionparent"></a>IDiaFrameData::get_functionParent
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Extrait une interface de données de frame de la fonction englobante.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_functionParent (   
   IDiaFrameData** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objet pour la fonction englobante.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



