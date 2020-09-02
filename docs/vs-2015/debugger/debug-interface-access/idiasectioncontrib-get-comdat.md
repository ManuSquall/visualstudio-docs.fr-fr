---
title: IDiaSectionContrib::get_comdat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ddf479a2da74803916b7afc1945eb610d6b0e668
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576631"
---
# <a name="idiasectioncontribget_comdat"></a>IDiaSectionContrib::get_comdat
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un indicateur qui signale si la section est un enregistrement COMDAT.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_comdat (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Retourne `TRUE` si la section est un enregistrement COMDAT ; sinon, retourne `FALSE` .  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Un enregistrement COMDAT est un enregistrement COFF (Common Object File Format) qui rend les fonctions empaquetées visibles à l’éditeur de liens.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
