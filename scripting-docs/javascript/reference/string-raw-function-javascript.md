---
title: String.Raw, fonction (JavaScript) | Documents Microsoft
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
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53df2bf0e455da8b1ccc6de3cbf3f4e3ebee4c09
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="stringraw-function-javascript"></a>String.raw, fonction (JavaScript)
Retourne la chaîne brute d'une chaîne modèle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `templateStr`  
 Obligatoire. Chaîne de modèle.  
  
 `obj`  
 Obligatoire. Objet correct spécifié à l’aide de notation de littéral d’objet, telle que {raw: 'value'}.  
  
 `...substitutions`  
 Facultatif. Un tableau (un [paramètre rest](../../javascript/functions-javascript.md)) consistant en une ou plusieurs valeurs de substitution.  
  
## <a name="remarks"></a>Remarques  
 Le `String.raw` fonction est conçue pour une utilisation avec [chaînes modèles](../../javascript/advanced/template-strings-javascript.md). La chaîne brute inclut les caractères d'échappement et les barres obliques inverses qui sont présents dans la chaîne.  
  
 Une erreur est levée si `obj` n'est pas un objet bien formé.  
  
## <a name="example"></a>Exemple  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd   
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]