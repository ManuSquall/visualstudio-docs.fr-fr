---
title: "escape, fonction (JavaScript) | Microsoft Docs"
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
  - "escape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encoder les objets String"
  - "Escape (méthode)"
  - "hexadécimal"
  - "objet String, encoder"
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# escape, fonction (JavaScript)
Encode des chaînes pour en permettre la lecture sur tous les ordinateurs.  Déconseillé.  
  
## Syntaxe  
  
```  
escape(charString)   
```  
  
## Notes  
 L'argument `charString` requis représente tout objet de la `String` ou un littéral à encoder.  
  
 La fonction **escape** retourne une valeur de chaîne \(au format Unicode\) reprenant le contenu de `charstring`.  Les espaces, la ponctuation, les caractères accentués et tous les autres caractères non ASCII sont remplacés par un encodage `%`*xx*, dans lequel *xx* équivaut au nombre hexadécimal représentant le caractère en question.  Par exemple, un espace est retourné sous la forme « %20 ».  
  
 Les caractères d'une valeur supérieure à 255 sont stockés selon le format **%u** *xxxx*.  
  
> [!NOTE]
>  N'utilisez pas la fonction **escape** pour encoder des URI \(Uniform Resource Identifiers\).  Utilisez plutôt les fonctions `encodeURI` et `encodeURIComponent` à la place.  
  
 **S'applique à** : [Objet Global](../../javascript/reference/global-object-javascript.md)  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [Fonction encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent, fonction](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [String, objet](../../javascript/reference/string-object-javascript.md)   
 [Fonction unescape](../../javascript/reference/unescape-function-javascript.md)