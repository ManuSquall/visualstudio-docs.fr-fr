---
title: "toLocaleLowerCase, méthode (String) (JavaScript) | Documents Microsoft"
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
- toLocaleLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleLowerCase method
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 642ced387e0d3b4cf763767ec147d6160ed7d36b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalelowercase-method-string-javascript"></a>toLocaleLowerCase, méthode (String) (JavaScript)
Convertit tous les caractères alphabétiques en minuscules, compte tenu des paramètres régionaux de l’environnement hôte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `stringVar` référence est un `String` objet ou un littéral de chaîne.  
  
 Le `toLocaleLowerCase` méthode convertit les caractères dans une chaîne, en tenant compte des paramètres régionaux de l’environnement hôte. Dans la plupart des cas, le résultat est le même que le résultat de la `toLowerCase` (méthode). Ils diffèrent si les règles d’une langue sont en conflit avec les mappages de casse Unicode standards.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [toLocaleUpperCase, méthode (String)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [Méthode toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)