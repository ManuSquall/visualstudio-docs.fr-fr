---
title: toLocaleUpperCase, méthode (String) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- toLocaleUpperCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleUpperCase method
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07a89560dde0319598da30fc3451524112b99eac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640429"
---
# <a name="tolocaleuppercase-method-string-javascript"></a>toLocaleUpperCase, méthode (String) (JavaScript)
Retourne une chaîne où tous les caractères alphabétiques ont été les paramètres régionaux de l’environnement converties en majuscules, en tenant compte de l’ordinateur hôte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `stringVar` référence est un `String` objet ou un littéral de chaîne.  
  
 Le `toLocaleUpperCase` méthode convertit les caractères dans une chaîne, en tenant compte des paramètres régionaux de l’environnement hôte. Dans la plupart des cas, le résultat est le même que le résultat du `toUpperCase` (méthode). Ils diffèrent si les règles d’une langue sont en conflit avec les mappages de casse Unicode standards.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [toLocaleLowerCase, méthode (String)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [Méthode toUpperCase (String)](../../javascript/reference/touppercase-method-string-javascript.md)