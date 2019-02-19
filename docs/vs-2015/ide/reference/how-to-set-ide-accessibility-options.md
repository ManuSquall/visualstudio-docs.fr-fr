---
title: Guide pratique pour définir les options d’accessibilité IDE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1f70f2f33b8ad0af4f0fa13489cb75be529c322
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54803221"
---
# <a name="how-to-set-ide-accessibility-options"></a>Guide pratique pour définir les options d'accessibilité IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] contient des fonctionnalités qui facilitent la lecture pour les personnes à acuité visuelle réduite et l’écriture pour celles dont la dextérité manuelle est réduite. Ces fonctionnalités incluent notamment la modification de la taille et de la couleur du texte dans les éditeurs, la modification de la taille du texte et des boutons des barres d’outils et la saisie semi-automatique pour les méthodes et les paramètres.  
  
 En outre, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prend en charge les dispositions de clavier Dvorak, qui rendent plus accessibles les caractères les plus fréquemment tapés. Vous pouvez également personnaliser les touches de raccourci par défaut disponibles dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Pour plus d’informations, consultez [Identification et personnalisation des raccourcis clavier](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="editors-dialogs-and-tool-windows"></a>Éditeurs, boîtes de dialogue et fenêtres d’outils  
 Par défaut, les boîtes de dialogue et les fenêtres d’outils de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utilisent les mêmes taille de police et couleurs que le système d’exploitation. Les paramètres de couleur pour le cadre de l’IDE, les boîtes de dialogue, les barres d’outils et les fenêtres d’outils sont basés sur un modèle de couleurs : clair ou sombre. Vous pouvez changer le modèle de couleurs actuel dans la [boîte de dialogue Général, Environnement, Options](../../ide/reference/general-environment-options-dialog-box.md).  
  
 Vous pouvez également afficher des fenêtres indépendantes dans le mode Code de l’éditeur. Ces fenêtres peuvent vous demander de fournir des membres disponibles sur l’objet en cours et les paramètres pour exécuter une fonction ou une instruction. Ces fenêtres peuvent être utiles si vous avez des difficultés à taper. Toutefois, elles interfèrent avec le focus dans l’éditeur de code, ce qui peut être problématique pour certains utilisateurs. Vous pouvez désactiver ces fenêtres en ouvrant la boîte de dialogue Options et en décochant **Répertorier automatiquement les membres** et **Informations sur les paramètres** dans la page **Éditeur de texte**, **Toutes les langues**, **Général** de la boîte de dialogue **Options**. Pour plus d’informations, consultez [Guide pratique pour définir les options générales de l’éditeur](http://msdn.microsoft.com/704e4a7b-2162-4bed-8a47-f4f6ffec98c2).  
  
 Vous pouvez réorganiser les fenêtres dans l’environnement de développement intégré (IDE) pour les adapter au mieux à votre manière de travailler. Vous pouvez ancrer, rendre flottante, masquer ou masquer automatiquement chaque fenêtre Outil.  
  
 Pour plus d’informations sur la modification des dispositions de fenêtres, consultez [Personnalisation des dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
### <a name="changing-the-size-of-text"></a>Modification de la taille du texte  
 Vous pouvez modifier les paramètres des fenêtres Outil de texte, telles que la fenêtre **Commande**, la fenêtre **Exécution** et la fenêtre **Sortie**, dans le volet **Polices et couleurs** des options **Environnement**, dans la boîte de dialogue **Outils**. Lorsque l’option **[Toutes les fenêtres Outil de texte]** est sélectionnée dans la liste déroulante **Afficher les paramètres de**, le paramètre par défaut est répertorié en tant que **Par défaut** dans les listes déroulantes **Premier plan de l’élément** et **Arrière plan de l’élément**. Vous pouvez également modifier les paramètres d’affichage du texte dans l’éditeur.  
  
##### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Pour modifier la taille du texte dans les éditeurs et les fenêtres Outil de texte  
  
1.  Dans le menu **Outils** , choisissez **Options**.  
  
2.  Choisissez **Polices et couleurs** dans le dossier **Environnement**.  
  
3.  Sélectionnez une option dans le menu déroulant **Afficher les paramètres de**.  
  
     Pour modifier la taille de police du texte dans un éditeur, choisissez **Éditeur de texte**.  
  
     Pour modifier la taille de police du texte dans les fenêtres Outil de texte, choisissez **[Toutes les fenêtres Outil de texte]**.  
  
     Pour modifier la taille de police du texte des info-bulles dans un éditeur, choisissez **Info-bulle de l’éditeur**.  
  
     Pour modifier la taille de police du texte dans la saisie semi-automatique des instructions, choisissez **Saisie semi-automatique des instructions**.  
  
4.  Dans **Afficher les éléments**, sélectionnez **Texte brut**.  
  
5.  Dans **Police**, sélectionnez un nouveau type de police.  
  
6.  Dans **Taille**, sélectionnez une nouvelle taille de police.  
  
    > [!NOTE]
    >  Pour rétablir la taille du texte pour les éditeurs et les fenêtres Outil de texte, choisissez **Par défaut**.  
  
7.  Cliquez sur **OK**.  
  
### <a name="changing-the-colors-used-in-the-ide"></a>Modification des couleurs utilisées dans l’IDE  
 Vous pouvez également choisir de modifier les couleurs par défaut pour le texte, les indicateurs en marge, l’espace blanc et les éléments de code dans l’éditeur.  
  
> [!NOTE]
>  Pour utiliser des couleurs à contraste élevé pour toutes les fenêtres d’application dans votre système d’exploitation, appuyez sur <strong>Alt gauche+</strong>**Maj gauche+Impr. écran**. Si [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est ouvert, fermez et rouvrez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour implémenter complètement les couleurs à contraste élevé.  
  
##### <a name="to-change-the-color-of-items-in-the-editor"></a>Pour changer la couleur des éléments dans l’éditeur  
  
1.  Dans le menu **Outils** , choisissez **Options**.  
  
2.  Choisissez **Polices et couleurs** dans le dossier **Environnement**.  
  
3.  Dans **Afficher les paramètres de**, choisissez **Éditeur de texte**.  
  
4.  Dans **Afficher les éléments**, sélectionnez un élément dont vous avez besoin de modifier l’affichage, tel que **Texte brut**, **Marge des indicateurs**, **Espaces blancs visibles**, **Nom d’attribut HTML** ou **Attribut XML**.  
  
5.  Sélectionnez les paramètres d’affichage parmi les options suivantes : **Premier plan de l’élément**, **Arrière-plan de l’élément** et **Gras**.  
  
6.  Cliquez sur **OK**.  
  
## <a name="toolbars"></a>Barres d'outils  
 Pour améliorer l’accessibilité et la facilité d’utilisation de la barre d’outils, vous pouvez ajouter du texte aux boutons de barre d’outils.  
  
#### <a name="to-assign-text-to-toolbar-buttons"></a>Pour affecter un texte à des boutons de barre d’outils  
  
1.  Dans le menu **Outils**, choisissez **Personnaliser**.  
  
2.  Dans la boîte de dialogue **Personnaliser**, sélectionnez l’onglet **Commandes**.  
  
3.  Sélectionnez **Barre d’outils**, puis choisissez le nom de la barre d’outils qui contient le bouton pour lequel vous souhaitez afficher le texte.  
  
4.  Dans la liste, sélectionnez la commande que vous souhaitez modifier.  
  
5.  Choisissez **Modifier la sélection**.  
  
6.  Choisissez **Image et texte**.  
  
#### <a name="to-modify-the-buttons-displayed-text"></a>Pour modifier le texte du bouton à afficher  
  
1.  Sélectionnez de nouveau **Modifier la sélection**.  
  
2.  À côté de **Nom**, insérez une nouvelle légende pour le bouton sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités d’accessibilité de Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)   
 [Ressources pour la conception d’applications accessibles](../../ide/reference/resources-for-designing-accessible-applications.md)
