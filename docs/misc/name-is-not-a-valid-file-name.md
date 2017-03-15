---
title: "&lt;name&gt; is not a valid file name. | Microsoft Docs"
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
  - "VS_E_INVALIDFILENAME"
  - "VS.Message.0x00006A72"
ms.assetid: c5969671-3b64-4854-acb6-328e8a30863f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid file name.
Cette erreur se produit lorsque vous essayez de créer un nouveau fichier à partir de la fenêtre Commande, en incluant des caractères non pris en charge dans le nom de fichier.  
  
 Les noms de fichiers ne peuvent pas contenir les caractères suivants :  
  
-   dièse \(\#\)  
  
-   pourcentage \(%\)  
  
-   et commercial \(&\)  
  
-   astérisque \(\*\)  
  
-   barre verticale \(&#124;\)  
  
-   barre oblique inverse \(\\\)  
  
-   deux\-points \(:\)  
  
-   guillemet double \("\)  
  
-   inférieur à \(\<\)  
  
-   supérieur à \(\>\)  
  
-   point \(.\)  
  
-   point d'interrogation \(?\)  
  
-   barre oblique \(\/\)  
  
-   espace à gauche ou à droite \(' '\)  
  
-   noms réservés à Windows ou à MS\-DOS \(nul, aux, con, com1, lpt1, etc.\)  
  
### Pour corriger cette erreur  
  
-   Entrez la commande avec un nouveau nom de fichier qui ne contient pas les caractères répertoriés ci\-dessus.  
  
## Voir aussi  
 [Nouveau fichier, commande](../ide/reference/new-file-command.md)   
 [Commandes Visual Studio](../ide/reference/visual-studio-commands.md)