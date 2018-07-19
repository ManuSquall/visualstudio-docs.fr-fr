---
title: LocationType | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb46eb1c7477f93ed63dfc4424d881886c8d0c8f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480002"
---
# <a name="locationtype"></a>LocationType
Indique le type d’informations d’emplacement contenues dans un symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
enum LocationType {   
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
 Emplacement est un emplacement Microsoft Intermediate Language (MSIL).  
  
 `LocIsIlRel`  
 Emplacement est relatif à la MSIL.  
  
 `LocInMetaData`  
 Se trouve dans les métadonnées.  
  
 `LocIsConstant`  
 Emplacement est une valeur constante.  
  
 `LocTypeMax`  
 Le nombre de types d’emplacement de cette énumération.  
  
## <a name="remarks"></a>Notes  
 Les propriétés disponibles pour le [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) interface dépendent d’emplacement du symbole dans le fichier image. Pour plus d’informations, consultez [emplacements de symboles](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Les valeurs de cette énumération sont retournées par un appel à la [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)