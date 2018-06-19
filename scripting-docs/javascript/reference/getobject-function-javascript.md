---
title: GetObject, fonction (JavaScript) | Documents Microsoft
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
- GetObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetObject function
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d8bad127a0f260395a1ec19f44ff2d495006024
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637459"
---
# <a name="getobject-function-javascript"></a>GetObject, fonction (JavaScript)
Retourne une référence à un objet Automation à partir d’un fichier.  
  
> [!NOTE]
>  Cette fonction n’est pas pris en charge dans Internet Explorer 9 (mode normes) ou version ultérieure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GetObject([pathname] [, class])  
```  
  
## <a name="parameters"></a>Paramètres  
 `pathname`  
 Facultatif. Chemin d’accès complet et nom du fichier contenant l’objet à récupérer. Si `pathname` est omis, `class` est requis.  
  
 `class`  
 Facultatif. Classe de l’objet.  
  
 Le `class` argument utilise la syntaxe `appname.objectype` et comprend les éléments suivants :  
  
 `appname`  
 Obligatoire. Nom de l’application qui fournit l’objet.  
  
 `objectype`  
 Obligatoire. Type ou classe d’objet à créer.  
  
## <a name="remarks"></a>Remarques  
 Le `GetObject` fonction n’est pas prise en charge dans [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] ou version ultérieure.  
  
 Utilisez le `GetObject` (fonction) pour accéder à un objet Automation à partir d’un fichier. Assignez l’objet retourné par `GetObject` à la variable objet. Exemple :  
  
```JavaScript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 Lorsque ce code est exécuté, l’application associée spécifiée `pathname` est démarré, et l’objet dans le fichier spécifié est activé. Si `pathname` est une chaîne de longueur nulle (" »), `GetObject` retourne une nouvelle instance d’objet du type spécifié. Si le `pathname` argument est omis, `GetObject` retourne un objet actuellement actif du type spécifié. Si aucun objet du type spécifié n’existe, une erreur se produit.  
  
 Certaines applications permettent d’activer une partie d’un fichier. Pour ce faire, ajoutez un point d’exclamation ( !) à la fin du nom de fichier et suivez avec une chaîne qui identifie la partie du fichier que vous souhaitez activer. Pour plus d’informations sur la façon de créer cette chaîne, consultez la documentation de l’application qui a créé l’objet.  
  
 Par exemple, dans une application de dessin, vous pouvez avoir plusieurs couches de dessin stockées dans un fichier. Le code suivant vous permet d’activer une couche d’un dessin nommé `SCHEMA.CAD`:  
  
```JavaScript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 Si vous ne spécifiez pas de classe de l’objet, Automation détermine l’application à démarrer et l’objet à activer, basé sur le nom de fichier que vous fournissez. Toutefois, certains fichiers peuvent prendre en charge plusieurs classes d’objet. Par exemple, un dessin peut prendre en charge trois types d’objets différents : un objet d’Application, un objet de dessin et un objet de barre d’outils, qui font partie du même fichier. Pour spécifier quel objet d’un fichier que vous souhaitez activer, utilisez le paramètre facultatif `class` argument. Exemple :  
  
```JavaScript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 Dans l’exemple précédent, `FIGMENT` est le nom d’une application de dessin et `DRAWING` est un des types d’objets il prend en charge. Une fois qu’un objet est activé, vous le référencez dans le code à l’aide de la variable objet que vous avez défini. Dans l’exemple précédent, vous accéder aux propriétés et méthodes du nouvel objet à l’aide de la variable objet `MyObject`. Exemple :  
  
```JavaScript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  Utilisez le `GetObject` fonctionne quand il existe une instance en cours de l’objet, ou si vous souhaitez créer l’objet avec un fichier déjà chargé. S’il n’existe aucune instance en cours, et vous ne souhaitez pas démarrer l’objet avec un fichier chargé, utilisez la `ActiveXObject` objet.  
  
 Si un objet s’est inscrit en tant qu’objet à instance unique, qu’une seule instance de l’objet est créée, quelle que soit la procédure autant de fois `ActiveXObject` est exécutée. Avec un objet à instance unique, `GetObject` retourne toujours la même instance lorsqu’elle est appelée avec la chaîne de longueur nulle (« ») syntaxe et provoque une erreur si le `pathname` argument est omis.  
  
## <a name="requirements"></a>Spécifications  
 Prise en charge dans les modes de document suivants : Quirks, Internet Explorer 6 normes, des normes Internet Explorer 7 et les normes Internet Explorer 8. Voir [Informations de version](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Objet ActiveXObject](../../javascript/reference/activexobject-object-javascript.md)