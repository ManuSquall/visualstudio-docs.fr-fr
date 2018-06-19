---
title: constructor, propriété (Boolean) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091da5342c4713c8eba646a8bd78c315a6a0fa48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636009"
---
# <a name="constructor-property-boolean"></a>constructor, propriété (Boolean)
Spécifie la fonction qui crée une valeur booléenne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
boolean.constructor([[value])  
```  
  
#### <a name="parameters"></a>Paramètres  
 `boolean`  
 Le nom de la valeur booléenne.  
  
 `value`  
 Facultatif. Spécifie la valeur booléenne. Il peut s’agir les numéros 1 ou 0, ou la chaîne « true » ou « false ».  
  
## <a name="remarks"></a>Remarques  
 Le `constructor` propriété contient une référence à la fonction qui crée les instances de l’objet Boolean.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la propriété de constructeur.  
  
```JavaScript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]