---
title: "Includes, méthode (String) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848143b64d3e32452aea41f08b6f5c57879d3e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="includes-method-string-javascript"></a>includes, méthode (String) (JavaScript)
Retourne une valeur booléenne qui indique si la chaîne passée est contenue dans l'objet String.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `stringObj`  
 Obligatoire. Objet de chaîne pour le test.  
  
 `substring`  
 Obligatoire. Chaîne à tester.  
  
 `position`  
 Facultatif. Position du premier caractère pour le test dans l'objet String, en commençant à 0.  
  
## <a name="return-value"></a>Valeur de retour  
 Si la chaîne passée est contenue dans l'objet String, la méthode `includes` retourne `true` ; sinon, elle retourne `false`.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]