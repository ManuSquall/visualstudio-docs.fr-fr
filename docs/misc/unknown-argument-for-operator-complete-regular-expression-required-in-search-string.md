---
title: "Unknown argument for &#39;:&#39; operator. Complete Regular Expression required in search string. | Microsoft Docs"
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
  - "vs.message.0x800A00BE"
  - "vs.message.VS_E_RE_SPECIALUNKNOWN"
ms.assetid: 8cbc2f7f-7ea1-4803-904c-1f716cd36376
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unknown argument for &#39;:&#39; operator. Complete Regular Expression required in search string.
Cette erreur se produit généralement durant la recherche ou le remplacement, si des expressions régulières ou à caractères génériques sont utilisées dans la chaîne recherchée.  L'opérateur deux\-points \(`:`\) a été entré, mais l'argument qui le suit ne constitue pas un argument valide.  
  
> [!NOTE]
>  Les arguments qui correspondent à l'opérateur \(`:`\) respectent la casse.  
  
### Pour corriger cette erreur  
  
1.  Examinez les syntaxes d'expressions régulières qui se trouvent dans la rubrique « Expressions régulières ».  
  
2.  Vérifiez que la casse appropriée a été utilisée pour l'argument.  
  
3.  Si vous utilisez un Éditeur de méthode d'entrée, assurez\-vous que l'argument n'est pas spécifié à l'aide de caractères pleine chasse.  
  
## Voir aussi  
 [Utilisation d'expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/fr-fr/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Rechercher dans les fichiers](../ide/find-in-files.md)