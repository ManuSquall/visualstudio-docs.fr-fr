---
title: "stacktracelimit, propriété (Error) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Error.stackTraceLimit
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error stack track limit [JavaScript]
- JavaScript error stack
- error stack [JavaScript]
- JavaScript stack trace limit
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af736ee8b385f93b761f1dfa021c23ee5376292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="stacktracelimit-property-error-javascript"></a>stackTraceLimit, propriété (Error) (JavaScript)
Obtient ou définit la limite de trace de pile, qui est équivalente au nombre de trames d’erreur à afficher. La limite par défaut est 10.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez définir le `stackTraceLimit` propriété à une valeur positive comprise entre 0 et `Infinity`. Si la `stackTraceLimit` est définie à 0 au moment où une erreur est levée, aucune trace de la pile n’est indiqué. Si la propriété est définie à une valeur négative ou une valeur non numérique, la valeur est convertie en 0. Si la stackTraceLimit est définie sur `Infinity`, la pile entière est indiquée. Sinon, `ToUint32` est utilisée pour convertir la valeur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment définir, puis d’obtenir la limite de trace de pile.  
  
```JavaScript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## <a name="requirements"></a>Spécifications  
 Prise en charge dans Internet Explorer 10 et [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] applications.  
  
 **S’applique aux**: [objet Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, propriété (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [message, propriété (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Name, propriété (Error)](../../javascript/reference/name-property-error-javascript.md)   
 [Propriété stack (Error)](../../javascript/reference/stack-property-error-javascript.md)