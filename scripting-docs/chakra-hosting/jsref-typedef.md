---
title: Jsref, Typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9d4c478a45f53e83dfa59fdde21cfa4c988c92e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsref-typedef"></a>JsRef, typedef
Une référence à un objet détenu par le récupérateur de mémoire Chakra.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef void *JsRef;  
```  
  
## <a name="remarks"></a>Remarques  
 Un runtime Chakra fera automatiquement le suivi des références JsRef dès lors qu’elles sont stockées dans des variables locales ou dans des paramètres (c’est-à-dire sur la pile). Le stockage d'une référence JsRef ailleurs que sur la pile nécessite l'appel de JsAddRef et de JsRelease pour gérer le cycle de vie de l'objet, sans quoi le récupérateur de mémoire est susceptible de libérer l'objet alors qu'il est encore utilisé.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)