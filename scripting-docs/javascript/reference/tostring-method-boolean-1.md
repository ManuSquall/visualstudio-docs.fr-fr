---
title: "ToString, méthode (Boolean) 1 | Documents Microsoft"
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17dd9503e4e09aafca3d153662bf7487538cda3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-boolean-1"></a>ToString, méthode (Boolean) 1
Retourne la représentation d'un objet sous forme de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
boolean.toString()  
```  
  
## <a name="parameters"></a>Paramètres  
 `boolean`  
 Obligatoire. Objet pour lequel obtenir une représentation sous forme de chaîne.  
  
## <a name="return-value"></a>Valeur de retour  
 Si la valeur booléenne est `true`, retourne « true ». Sinon, retourne « false ».  
  
## <a name="remarks"></a>Remarques  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **toString** (méthode).  
  
```JavaScript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]