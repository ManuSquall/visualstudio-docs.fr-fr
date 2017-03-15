---
title: "Argument is missing in &#39;\&#39; escape sequence. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_RE_ESCAPEMISSINGARG"
  - "vs.message.0x800A00BD"
ms.assetid: 5bd6559b-8cd9-450f-91c8-335ff1b1ef86
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Argument is missing in &#39;\&#39; escape sequence.
Cette erreur se produit généralement durant la recherche ou le remplacement, si des expressions régulières ou à caractères génériques sont utilisées dans la chaîne recherchée.  Cette erreur peut être provoquée par l'utilisation d'une barre oblique simple \(`\`\) à la fin d'un masque ou l'utilisation de `\x` ou `\u` sans code hexadécimal de caractère Unicode valide.  
  
### Pour corriger cette erreur  
  
1.  Pour effectuer la recherche en utilisant le caractère d'échappement de l'expression régulière, entrez `\`.  
  
2.  Pour rechercher un caractère Unicode, entrez `\x` ou `\u`, suivis d'une valeur Unicode valide.  
  
3.  Pour rechercher une barre oblique inverse, utilisez `\\`.  
  
## Voir aussi  
 [Utilisation d'expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/fr-fr/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Rechercher dans les fichiers](../ide/find-in-files.md)