---
title: "GetObject, fonction (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "GetObject"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetObject (fonction)"
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# GetObject, fonction (JavaScript)
Retourne une référence à un objet Automation d'un fichier.  
  
> [!NOTE]
>  Cette fonction n'est pas prise en charge dans Internet Explorer 9 \(mode standard\) ou version ultérieure.  
  
## Syntaxe  
  
```  
GetObject([pathname] [, class])  
```  
  
## Paramètres  
 `pathname`  
 Optionnel.  Chemin d'accès complet et nom du fichier contenant l'objet à récupérer.  Si `pathname` est omis, `class` est requis.  
  
 `class`  
 Optionnel.  Classe de l'objet.  
  
 L'argument `class` utilise la syntaxe `appname.objectype` et inclut ces différents éléments :  
  
 `appname`  
 Requis.  Nom de l'application qui fournit l'objet.  
  
 `objectype`  
 Requis.  Type ou classe de l'objet à créer.  
  
## Notes  
 La fonction `GetObject` n'est pas prise en charge dans [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] ou version ultérieure.  
  
 Utilisez la fonction `GetObject` pour accéder à un objet Automation à partir d'un fichier.  Assignez l'objet retourné par `GetObject` à la variable objet.  Par exemple :  
  
```javascript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 Lorsque ce code est exécuté, l'application associée à l'argument `pathname` spécifié démarre, et l'objet dans le fichier spécifié est activé.  Si `pathname` est une chaîne de longueur nulle \(""\), la fonction `GetObject` retourne une nouvelle instance d'objet du type spécifié.  Si l'argument `pathname` est omis, `GetObject` retourne un objet actuellement actif du type spécifié.  S'il n'existe aucun objet du type spécifié, une erreur se produit.  
  
 Certaines applications permettent d'activer une partie d'un fichier.  Pour ce faire, ajoutez un point d'exclamation \(\!\) à la fin du nom du fichier et faites suivre ce dernier d'une chaîne identifiant la partie du fichier à activer.  Pour plus d'informations sur la création de cette chaîne, consultez la documentation de l'application qui a créé l'objet.  
  
 Dans une application de dessin, par exemple, un fichier peut contenir un dessin constitué de plusieurs couches.  Le code suivant vous permet d'activer un plan d'un dessin nommé `SCHEMA.CAD` :  
  
```javascript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 Si vous ne spécifiez pas la classe de l'objet, Automation identifie l'application à démarrer et l'objet à activer, en fonction du nom de fichier que vous fournissez.  Cependant, certains fichiers peuvent prendre en charge plusieurs classes d'objets.  Par exemple, un dessin peut comporter un objet Application, un objet Drawing et un objet Toolbar, chacun faisant partie du même fichier.  Pour spécifier l'objet à activer dans un fichier, utilisez l'argument `class` facultatif.  Par exemple :  
  
```javascript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 Dans l'exemple précédent, `FIGMENT` est le nom d'une application de dessin et `DRAWING` est un des types d'objets qu'elle prend en charge.  Une fois l'objet activé, vous le référencez dans le code à l'aide de la variable objet que vous avez définie.  Dans l'exemple précédent, vous accédez aux propriétés et aux méthodes du nouvel objet en utilisant la variable objet `MyObject`.  Par exemple :  
  
```javascript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  Utilisez la fonction `GetObject` s'il existe une instance active de l'objet, ou lorsque vous souhaitez créer l'objet avec un fichier déjà chargé.  En l'absence d'instance active, et si vous ne souhaitez pas que l'objet soit créé avec un fichier chargé, utilisez l'objet `ActiveXObject`.  
  
 Si un objet s'est inscrit comme un objet à instance unique, une seule instance de l'objet est créée, quel que soit le nombre d'exécutions de l'objet `ActiveXObject`.  Avec un objet à instance unique, `GetObject` retourne toujours la même instance lorsqu'elle est appelée à l'aide de la syntaxe de chaîne de longueur nulle \(""\). Cela entraîne une erreur si l'argument `pathname` est omis.  
  
## Configuration requise  
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 \(mode standard\), Internet Explorer 7 \(mode standard\) et Internet Explorer 8 \(mode standard\).  Consultez [Informations sur la version](../../javascript/reference/javascript-version-information.md).  
  
## Voir aussi  
 [ActiveXObject, objet](../../javascript/reference/activexobject-object-javascript.md)