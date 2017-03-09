---
title: "Comment&#160;: tester la bo&#238;te de dialogue &#192; propos de du menu Aide et l’&#233;cran de d&#233;marrage | Microsoft Docs"
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
  - "Boîte de dialogue À propos de"
  - "VSPackages, écrans de démarrage"
  - "VSPackages, personnalisation"
ms.assetid: 2b959fa4-56d3-44f4-8c2d-9ea2e6fb269d
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Comment&#160;: tester la bo&#238;te de dialogue &#192; propos de du menu Aide et l’&#233;cran de d&#233;marrage
Une fois que vous avez implémenté **À propos de** et la prise en charge de l'écran de démarrage, vous pouvez tester votre implémentation dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Pour tester l'aide concernant la boîte de dialogue  
  
1.  À partir de l'invite de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , exécutez devenv.exe avec le commutateur d' **\/setup** .  Pour exécuter dans l'environnement instance expérimentale de, tapez :  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     **Remarque** vous devez répéter cette étape uniquement lorsque vous modifiez les informations d'écran de **À propos de** .  
  
2.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] exécuté dans la même racine de Registre qui a été mentionné précédemment, mais sans commutateur d' **\/setup** :  
  
     **devenv \/rootsuffix Exp**  
  
3.  Dans le menu d' **Aide** , cliquez sur **Sur Microsoft Visual Studio**.  
  
     Votre nom d'un VSPackage s'affiche dans la liste de **produits installés** .  
  
4.  sélectionnez votre VSPackage de la liste.  
  
     Vos informations sur les produits de VSPackage apparaît dans la zone de texte de **Détails du produit** .  
  
### pour tester l'écran de démarrage  
  
1.  exécutez devenv.exe avec le commutateur d' **\/setup** .  Pour exécuter dans l'environnement instance expérimentale de, tapez :  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     **Remarque** vous devez répéter cette étape uniquement lorsque vous modifiez les informations de l'écran de démarrage.  
  
2.  Exécutez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans la même racine de Registre qui a été mentionné précédemment, mais avec le commutateur d' **\/splash** au lieu du commutateur d' **\/setup** .  
  
     **devenv \/rootsuffix Exp \/splash**  
  
     La vos informations sur les produits et logo d'un VSPackage s'affichent à l'écran de démarrage.  
  
## Voir aussi  
 [Personnalisation de VSPackage](/visual-cpp/misc/vspackage-branding)