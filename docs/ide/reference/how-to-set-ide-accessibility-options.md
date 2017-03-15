---
title: "Comment&#160;: d&#233;finir les options d&#39;accessibilit&#233; IDE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "accessibilité (Visual Studio)"
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Comment&#160;: d&#233;finir les options d&#39;accessibilit&#233; IDE
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contient des fonctionnalités qui facilitent la lecture pour les personnes à acuité visuelle réduite et l'écriture pour celles dont la mobilité est réduite.  Ces fonctionnalités incluent notamment la modification de la taille et de la couleur du texte dans les éditeurs, la modification de la taille du texte et des boutons des barres d'outils et la saisie semi\-automatique pour les méthodes et les paramètres.  
  
 En outre, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge les dispositions de clavier Dvorak, qui rendent plus accessibles les caractères les plus fréquemment tapés.  Vous pouvez également personnaliser les touches de raccourci par défaut disponibles dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Pour plus d'informations, consultez [Identification et personnalisation des raccourcis clavier](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Éditeurs, boîtes de dialogue et fenêtres Outil  
 Par défaut, les boîtes de dialogue et fenêtres Outil de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilisent la même taille de police et couleurs que le système d'exploitation.  Les paramètres de couleurs pour le frame IDE, des boîtes de dialogue, des barres d'outils, et des fenêtres Outil sont basés sur un modèle de couleurs : lumière ou sombres.  Vous pouvez modifier le thème actuel de couleur dans [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md).  
  
 Vous pouvez également afficher des fenêtres indépendantes en mode Code de l'éditeur.  Ces fenêtres peuvent vous amener avec les membres disponibles sur l'objet en cours et les paramètres à exécuter une fonction ou une instruction.  Ces fenêtres peuvent être utiles si la saisie de stimulation.  Toutefois, elles interfèrent avec le focus dans l'éditeur de code, qui peut s'avérer problématique pour certains utilisateurs.  Vous pouvez désactiver ces fenêtres en ouvrant la boîte de dialogue Options et désactivant **Répertorier automatiquement les membres** et **Informations sur les paramètresÉditeur de texte**, **Tous les langages**, page **Général** dans la boîte de dialogue **Options**.  Pour plus d'informations, consultez [How to: Set General Editor Options](http://msdn.microsoft.com/fr-fr/704e4a7b-2162-4bed-8a47-f4f6ffec98c2).  
  
 Vous avez la possibilité de réorganiser les fenêtres dans l'environnement de développement intégré \(IDE\) de la façon la plus adaptée à votre méthode de travail.  Vous pouvez ancrer, flotter, masquer, ou automatiquement masquer chaque fenêtre Outil.  
  
 Pour plus d'informations sur la modification des dispositions de fenêtre, consultez [Personnalisation des dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
### Modification de la taille du texte  
 Vous pouvez modifier les paramètres des fenêtres Outil de texte, comme les fenêtres **Commande**, **Exécution** et **Sortie**, dans le volet **Polices et couleurs** des options **Environnement** de la boîte de dialogue **Outils**.  Lorsque **\[Toutes les fenêtres Outil de texte\]** est sélectionné dans la liste déroulante **Afficher les paramètres de**, le paramètre par défaut est indiqué sous la forme **Par défaut** dans les listes déroulantes **Premier plan** et **Arrière\-plan**.  Vous pouvez aussi modifier les paramètres d'affichage du texte dans l'éditeur.  
  
##### Pour modifier la taille du texte dans les fenêtres Outil de texte et les éditeurs  
  
1.  Dans le menu **Outils**, sélectionnez **Options**.  
  
2.  Choisissez **Polices et couleurs** dans le dossier **Environnement**.  
  
3.  Sélectionnez une option dans le menu déroulant **Afficher les paramètres de**.  
  
     Pour modifier la taille de la police du texte dans un éditeur, choisissez **Éditeur de texte**.  
  
     Pour modifier la taille de la police du texte dans les fenêtres Outil de texte, choisissez **\[Toutes les fenêtres Outil de texte\]**.  
  
     Pour modifier la taille de la police du texte d'info\-bulle dans un éditeur, choisissez **Info\-bulle de l'éditeur**.  
  
     Pour modifier la taille de la police du texte dans la saisie semi\-automatique des instructions, choisissez **Compléter automatiquement les instructions**.  
  
4.  Dans **Éléments affichés**, sélectionnez **Texte brut**.  
  
5.  Dans **Police**, sélectionnez un nouveau type de police.  
  
6.  Dans **Taille**, sélectionnez une nouvelle taille de police.  
  
    > [!NOTE]
    >  Pour rétablir les valeurs par défaut pour la taille du texte des fenêtres Outil de texte et des éditeurs, choisissez **Par défaut**.  
  
7.  Cliquez sur **OK**.  
  
### Modification des couleurs utilisées dans l'IDE  
 Vous pouvez aussi choisir de modifier les couleurs par défaut du texte, des indicateurs en marge, des espaces blancs et des éléments de code dans l'éditeur.  
  
> [!NOTE]
>  Pour utiliser des couleurs à contraste élevé dans toutes les fenêtres des applications de votre système d'exploitation, appuyez sur **ALT gauche \+ MAJ gauche \+ IMPR. ÉCRAN**.  Si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est ouvert, fermez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et rouvrez\-le pour implémenter intégralement les couleurs à contraste élevé.  
  
##### Pour modifier la couleur des éléments dans l'éditeur  
  
1.  Dans le menu **Outils**, sélectionnez **Options**.  
  
2.  Choisissez **Polices et couleurs** dans le dossier **Environnement**.  
  
3.  Sous **Afficher les paramètres de**, sélectionnez **Éditeur de texte**.  
  
4.  Dans **Éléments affichés**, sélectionnez un élément dont vous devez modifier l'affichage, comme **Texte brut**, **Marge des indicateurs**, **Blancs visibles**, **Nom d'attribut HTML** ou **Attribut XML**.  
  
5.  Sélectionnez les paramètres d'affichage parmi les options suivantes : **Premier plan**, **Arrière\-plan** et **Gras**.  
  
6.  Cliquez sur **OK**.  
  
## Barres d'outils  
 Pour améliorer la facilité d'utilisation et l'accessibilité des barres d'outils, vous pouvez ajouter du texte aux boutons de barre d'outils.  
  
#### Pour assigner du texte aux boutons de barres d'outils  
  
1.  Dans le menu **Outils**, choisissez **Personnaliser**.  
  
2.  Dans la boîte de dialogue **Personnaliser**, sélectionnez l'onglet **Commandes**.  
  
3.  Sélectionnez **Barre d'outils**, puis choisissez le nom de la barre d'outils qui contient le bouton pour lequel vous voulez afficher du texte.  
  
4.  Dans la liste, sélectionnez la commande que vous voulez modifier.  
  
5.  Choisissez **Modifier la sélection**.  
  
6.  Choisissez **Image et texte**.  
  
#### Pour modifier le texte du bouton  
  
1.  Choisissez de nouveau **Modifier la sélection**.  
  
2.  À côté de Dans **Nom**, l'insertion fournissent une légende pour le bouton sélectionné.  
  
## Voir aussi  
 [Fonctionnalités d'accessibilité de Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)   
 [Ressources pour la conception d'applications accessibles](../../ide/reference/resources-for-designing-accessible-applications.md)