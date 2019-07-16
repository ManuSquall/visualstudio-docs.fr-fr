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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154200"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indique le type d’informations d’emplacement contenues dans un symbole.  
  
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
 Informations d’emplacement ne sont pas disponibles.  
  
 `LocIsStatic`  
 Emplacement est statique.  
  
 `LocIsTLS`  
 Se trouve dans le stockage local des threads.  
  
 `LocIsRegRel`  
 Emplacement est relative au Registre.  
  
 `LocIsThisRel`  
 Emplacement est `this`-relatif.  
  
 `LocIsEnregistered`  
 Se trouve dans un Registre.  
  
 `LocIsBitField`  
 Se trouve dans un champ de bits.  
  
 `LocIsSlot`  
 Emplacement est un emplacement de langage MSIL (Microsoft Intermediate Language).  
  
 `LocIsIlRel`  
 Emplacement est relatif à MSIL.  
  
 `LocInMetaData`  
 Se trouve dans les métadonnées.  
  
 `LocIsConstant`  
 Emplacement est une valeur constante.  
  
 `LocTypeMax`  
 Le nombre de types d’emplacement dans cette énumération.  
  
## <a name="remarks"></a>Notes  
 Les propriétés disponibles pour le [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) interface varient selon l’emplacement du symbole dans le fichier image. Pour plus d’informations, consultez [emplacements de symboles](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Les valeurs dans cette énumération sont retournées par un appel à la [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)
