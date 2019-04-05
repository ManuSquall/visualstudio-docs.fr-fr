---
title: IDiaEnumSectionContribs::Next | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18bee6cf8f47aeeadd41c7accc1f33566f564898
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951575"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un nombre spécifié de contributions de section dans la séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Next(   
   ULONG                celt,   
   IDiaSectionContrib** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 celt  
 [in] Le nombre de contributions de la section dans l’énumérateur à récupérer.  
  
 rgelt  
 [out] Un tableau qui doit être rempli avec le [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) objets qui représentent les contributions de la section souhaitée.  
  
 pceltFetched  
 [out] Retourne le nombre de contributions de la section dans l’énumérateur extraite.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si il n’y a aucune contribution de section plus. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
