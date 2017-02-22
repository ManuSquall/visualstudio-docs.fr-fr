---
title: "Comment&#160;: g&#233;rer les modes de l&#39;&#233;diteur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeur de code, modes"
  - "éditeur de code, options d'affichage"
  - "polices et taille"
  - "mode Plein écran"
  - "numéros de ligne"
  - "numéros de ligne, afficher"
  - "vues, changer le mode"
  - "vues, créer des fenêtres"
  - "vues, numéros de ligne"
  - "vues, mode Plan"
  - "vues, fractionner"
  - "vues, espace virtuel"
  - "vues, retour automatique à la ligne"
  - "espace virtuel (mode)"
  - "retour automatique à la ligne"
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Comment&#160;: g&#233;rer les modes de l&#39;&#233;diteur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez afficher l'éditeur de code de Visual Studio selon différents modes.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Activation du mode Plein écran  
 Vous pouvez décider de masquer toutes les fenêtres Outil et d'afficher seulement les fenêtres de document en activant le mode **Plein écran**.  
  
#### Pour activer le mode Plein écran  
  
-   Appuyez sur ALT\+MAJ\+ENTRÉE pour passer en mode **Plein écran** ou le quitter.  
  
     – ou –  
  
-   Publiez la commande `View.Fullscreen` dans la fenêtre **Commande**.  
  
## Activation du mode Espace virtuel  
 En mode **Espace virtuel**, des espaces sont insérés à la fin de chaque ligne de code.  Sélectionnez cette option pour placer des commentaires en un point précis, proche du code.  
  
#### Pour activer le mode Espace virtuel  
  
1.  Sélectionnez **Options** dans le menu **Outils**.  
  
2.  Développez le dossier **Éditeur de texte** et choisissez **Tous les langages** pour définir cette option globalement, ou choisissez un dossier de langage spécifique.  \(Par exemple, pour n'activer les numéros de ligne qu'en Visual Basic, choisissez les options Basic, Éditeur de texte.\)  
  
3.  Sélectionnez les options souhaitées dans **Général** et, sous **Paramètres**, sélectionnez **Activer l'espace virtuel**.  
  
    > [!NOTE]
    >  **Espace virtuel** est activé en mode **Sélectionner les colonnes**.  Si le mode **Espace virtuel** n'est pas activé, le point d'insertion passe automatiquement du dernier caractère de la ligne au premier caractère de la ligne suivante.  
  
## Voir aussi  
 [Personnalisation de l'éditeur](../ide/customizing-the-editor.md)   
 [Comment : réorganiser et ancrer des fenêtres](../misc/how-to-arrange-and-dock-windows.md)   
 [Polices et couleurs, Environnement, boîte de dialogue Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)