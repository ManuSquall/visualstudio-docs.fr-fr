---
title: escape, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- escape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encoding string objects
- Escape method
- hexadecimal
- String object, encoding
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b53a447ae6dde917c12a4711d9038136dc4500cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="escape-function-javascript"></a>escape, fonction (JavaScript)
Encode les chaînes afin de pouvoir être lus sur tous les ordinateurs. Obsolète.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
escape(charString)   
```  
  
## <a name="remarks"></a>Remarques  
 Requis `charString` correspond à un argument `String` objet ou littéral à encoder.  
  
 Le **échappement** fonction retourne une valeur de chaîne (au format Unicode) qui contient le contenu de `charstring`. Tous les espaces, les signes de ponctuation, les caractères accentués et d’autres caractères non ASCII sont remplacées par `%` *xx* encodage, où *xx* est équivalente à la nombre hexadécimal représentant le caractère. Par exemple, un espace est retourné en tant que « %20. »  
  
 Caractères d’une valeur supérieure à 255 sont stockés à l’aide de la **%u** *xxxx* format.  
  
> [!NOTE]
>  Le **échappement** fonction ne doit pas être utilisée pour encoder les identificateurs de ressource uniforme (URI). Utilisez `encodeURI` et `encodeURIComponent` à la place des fonctions.  
  
 **S’applique aux**: [objet Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent, fonction](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [Objet String](../../javascript/reference/string-object-javascript.md)   
 [Fonction unescape](../../javascript/reference/unescape-function-javascript.md)