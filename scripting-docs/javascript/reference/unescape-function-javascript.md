---
title: unescape, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: unescape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Unescape method
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96601fc21f47c86aec8c3702a6861c3676aacacf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="unescape-function-javascript"></a>unescape, fonction (JavaScript)
Décode `String` objets encodés avec la `escape` (fonction). Obsolète.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unescape(charString)   
```  
  
## <a name="remarks"></a>Remarques  
 Requis `charString` argument est un `String` objet ou littéral à décoder.  
  
 Le `unescape` fonction retourne une valeur de chaîne qui contient le contenu de `charstring`. Tous les caractères encodés :*xx* forme hexadécimale sont remplacés par leurs équivalents de jeu de caractères ASCII.  
  
 Les caractères encodés dans **%u** *xxxx* format (caractères Unicode) sont remplacés par les caractères Unicode avec codage hexadécimal *xxxx*.  
  
> [!NOTE]
>  Le `unescape` fonction ne doit pas être utilisée pour décoder des identificateurs de ressource uniforme (URI). Utilisez `decodeURI` et `decodeURIComponent` à la place des fonctions.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [objet Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [decodeURI, fonction](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent, fonction](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Fonction escape](../../javascript/reference/escape-function-javascript.md)   
 [Objet String](../../javascript/reference/string-object-javascript.md)