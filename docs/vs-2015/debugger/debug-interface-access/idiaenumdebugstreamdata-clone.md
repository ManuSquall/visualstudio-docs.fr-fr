---
title: IDiaEnumDebugStreamData::Clone | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Clone method
ms.assetid: e7f17750-0694-4634-bf34-c821cd265c2f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0c97018adad246674c672fc1b081944f05e5913c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198577"
---
# <a name="idiaenumdebugstreamdataclone"></a>IDiaEnumDebugStreamData::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Crée un énumérateur qui contient la même séquence énumérée que l’énumérateur actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumDebugStreamData** ppenum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 ppenum  
 à Retourne un objet [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) qui contient la séquence dupliquée des enregistrements de flux de données de débogage.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
