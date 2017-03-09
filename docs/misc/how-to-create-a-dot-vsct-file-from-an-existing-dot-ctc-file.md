---
title: "Comment&#160;: cr&#233;er un fichier .Vsct &#224; partir d’un fichier .Ctc existant | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fichiers VSCT, création basée sur un fichier .ctc"
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Comment&#160;: cr&#233;er un fichier .Vsct &#224; partir d’un fichier .Ctc existant
Vous pouvez créer un fichier .vsct XML à partir d’un fichier source .ctc de table de commande existant. Ainsi, vous pouvez tirer parti du nouveau format du compilateur \(VSTC\) de table de commande [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] XML.  
  
### Pour créer un fichier .vsct à partir d’un fichier .ctc  
  
1.  Obtenez une copie du langage Perl.  
  
2.  Obtenez une copie du script Perl ConvertCTCToVSCT.pl, généralement situé dans le dossier *\<Chemin d’installation du SDK Visual Studio\>*\\VisualStudioIntegration\\Tools\\bin.  
  
3.  Obtenez une copie du fichier source .ctc à convertir.  
  
4.  Placez les fichiers dans le même répertoire.  
  
5.  Dans la fenêtre d’invite de commandes [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], accédez au répertoire.  
  
6.  Type  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     où PkgCmd.ctc est le nom du fichier .ctc et PkgCmd.vsct est le nom du fichier .vsct à créer.  
  
     Un nouveau fichier source de table de commande XML .vsct est ainsi créé. Vous pouvez compiler le fichier à l’aide de Vsct.exe, le compilateur VSCT, comme vous le feriez pour tout autre fichier .vsct.  
  
    > [!NOTE]
    >  Vous pouvez améliorer la lisibilité du fichier .vsct en reformatant les commentaires XML.  
  
## Voir aussi  
 [Comment : créer un. Fichier VSCT](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)