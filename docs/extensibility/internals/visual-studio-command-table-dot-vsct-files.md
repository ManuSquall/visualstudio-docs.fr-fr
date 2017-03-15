---
title: "Table de commandes de Visual Studio (. Fichiers VSCT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Les fichiers VSCT, vue d'ensemble"
  - "Fichiers de Visual Studio commande table configuration (VSCT), vue d'ensemble"
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Table de commandes de Visual Studio (. Fichiers VSCT)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un fichier de configuration de table de commande est un fichier texte qui décrit l'ensemble des commandes qui contient un VSPackage. Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] commande compilateur de table \(VSCT\) compile des fichiers de configuration XML \(fichiers .vsct\) en fichiers de sortie \(.cto\) de table commande binaire. Les fichiers résultants .cto sont les mêmes que ceux qui sont créés à l'aide du compilateur de table \(CTC\) commande pour compiler des fichiers de configuration .ctc. Toutefois, les fichiers .vsct basé sur XML présente certains avantages, notamment un éditeur XML et le XML IntelliSense.  
  
 Pour en savoir plus sur la syntaxe et la sémantique des fichiers .vsct, consultez [Conception de Table de commande XML \(. Fichiers VSCT\)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## Dans cette section  
 [Conception de Table de commande XML \(. Fichiers VSCT\)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Explique comment concevoir des fichiers .vsct.  
  
 [Comment : créer un. Fichier VSCT](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Compare les méthodes de création d'un fichier .vsct. Décrit le processus de création manuelle d'un nouveau fichier .vsct.  
  
## Rubriques connexes  
 [Référence de schéma XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Fournit des détails sur chaque section du fichier de configuration XML de table de commande.  
  
 [Command Table Configuration \(.Ctc\) Files](http://msdn.microsoft.com/fr-fr/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Présente une vue d'ensemble du format de fichier .ctc déconseillées.  
  
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Décrit la spécification de format de table de commande.  
  
 [Ressources dans les packages VS](../../extensibility/internals/resources-in-vspackages.md)  
 Décrit comment utiliser les ressources managées et non managées dans les VSPackages gérés.  
  
 [Commandes, Menus et barres d'outils](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explique comment créer une interface utilisateur qui comprend les menus, barres d'outils et les zones de liste déroulante de commande.