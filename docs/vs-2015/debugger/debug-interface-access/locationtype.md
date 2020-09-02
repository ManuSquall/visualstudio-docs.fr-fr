---
title: LocationType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28bcaa626797313f6ea68a17da33ef9ea192a856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154200"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indique le type d’informations d’emplacement contenu dans un symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>Éléments  
 `LocIsNull`  
 Les informations d’emplacement ne sont pas disponibles.  
  
 `LocIsStatic`  
 L’emplacement est statique.  
  
 `LocIsTLS`  
 L’emplacement se trouve dans le stockage local des threads.  
  
 `LocIsRegRel`  
 L’emplacement est Register-relative.  
  
 `LocIsThisRel`  
 L’emplacement est `this` -relative.  
  
 `LocIsEnregistered`  
 L’emplacement se trouve dans un registre.  
  
 `LocIsBitField`  
 L’emplacement est un champ de bits.  
  
 `LocIsSlot`  
 L’emplacement est un emplacement MSIL (Microsoft Intermediate Language).  
  
 `LocIsIlRel`  
 L’emplacement est relatif à MSIL.  
  
 `LocInMetaData`  
 L’emplacement se trouve dans les métadonnées.  
  
 `LocIsConstant`  
 L’emplacement est dans une valeur constante.  
  
 `LocTypeMax`  
 Nombre de types d’emplacement dans cette énumération.  
  
## <a name="remarks"></a>Notes  
 Les propriétés disponibles pour l’interface [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) dépendent de l’emplacement du symbole dans le fichier image. Pour plus d’informations, consultez [emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Les valeurs de cette énumération sont retournées par un appel à la méthode [IDiaSymbol :: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst. h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol :: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)
