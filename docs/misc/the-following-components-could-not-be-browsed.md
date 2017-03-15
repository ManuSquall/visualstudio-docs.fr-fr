---
title: "The following components could not be browsed: | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS_E_CANNOTBROWSECOM"
  - "VS.Message.0x00006A6D"
  - "VS_E_LOADTYPELIBFAILED"
  - "VS_E_INVALIDCOMCOMPONENT"
  - "VS_E_UNRECOGNIZEDCOMPONENT"
  - "VS.Message.0x00006A6E"
  - "VS.Message.ObjectBrowserErrors"
  - "vs.Message.0x00005AC3"
  - "VS.Message.0x00005AC4"
  - "VS.Message.0x00005AC5"
  - "VS_E_REGFAILEDCOMCOMPONENT"
ms.assetid: 83b03767-eecb-47a4-8029-166308c7dded
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The following components could not be browsed:
Cette boîte de message peut répertorier plusieurs erreurs liées à l'Explorateur d'objets et à la boîte de dialogue Sélection des composants.  Les erreurs suivantes font partie des plus courantes.  
  
## Impossible d'afficher ce type de composant ou de fichier dans l'Explorateur d'objets.  
 Cette erreur se produit généralement lorsque vous spécifiez un nom de fichier qui n'existe pas ou qui n'est pas valide, ou un fichier que l'Explorateur d'objets ne peut pas explorer.  
  
#### Pour corriger cette erreur  
  
-   Vérifiez que le nom de fichier spécifié existe et qu'il s'agit d'un composant pouvant être exploré, tel qu'un assembly .NET, une bibliothèque de types COM ou un fichier browser source.  
  
## Le fichier n'est pas un composant .NET Framework ou COM valide.  
 Cette erreur se produit généralement lorsque le composant spécifié n'est pas un assembly .NET Framework ou une bibliothèque de types COM.  
  
#### Pour corriger cette erreur  
  
-   Choisissez un autre composant à explorer.  
  
## Impossible d'inscrire le fichier en tant que composant COM.  
 Cette erreur se produit généralement lorsque l'inscription de la bibliothèque de types d'un composant COM échoue.  La bibliothèque de types n'existe peut\-être pas ou est peut\-être endommagée.  
  
#### Pour corriger cette erreur  
  
-   Réinstallez le composant et recommencez.  
  
## Aucune bibliothèque de types n'a été enregistrée ou les informations inscrites ne sont pas valides.  
 La bibliothèque de types spécifiée n'existe peut\-être plus ou ne contient peut\-être pas d'informations valides.  
  
#### Pour corriger cette erreur  
  
-   Vérifiez que la bibliothèque de types existe et qu'elle est correctement inscrite.  
  
## Les composants requis pour parcourir les bibliothèques de types COM sont manquants ou ne sont pas inscrits correctement.  
 Le fichier vstlbinf.dll est manquant ou n'est pas correctement inscrit.  
  
#### Pour corriger cette erreur  
  
1.  Recherchez vstlbinf.dll sur votre ordinateur et inscrivez\-le via regsvr32.exe.  
  
     \- ou \-  
  
2.  Si vous ne trouvez aucun fichier vstlbinf.dll sur votre ordinateur, réinstallez ce produit.  
  
## Voir aussi  
 [Object Browser](http://msdn.microsoft.com/fr-fr/f89acfc5-1152-413d-9f56-3dc16e3f0470)   
 [Edit Custom Component Set Dialog Box](http://msdn.microsoft.com/fr-fr/dc995bd7-afbf-4389-ba1c-f377b677ded7)