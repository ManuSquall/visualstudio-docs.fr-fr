---
title: "Guide pratique pour personnaliser des menus et des barres d’outils dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.renametoolbar
- vs.customize.toolbars
- vs.buttoneditor
- vs.customize.commands
- vs.newtoolbar
helpviewer_keywords:
- captions, customizing toolbar
- custom toolbars [Visual Studio]
- command buttons, customizing toolbar
- labels, customizing toolbar
- images [Visual Studio], toolbar buttons
- buttons [Visual Studio], custom toolbars
- toolbars [Visual Studio], creating in the IDE
- icons [Visual Studio], customizing toolbar
- commands [Visual Studio], customizing environment
- customizing toolbars
- toolbars [Visual Studio], customizing
- toolbars [Visual Studio], customizing in the IDE
ms.assetid: b570ae2f-5302-45dc-9cc9-8d4d1ad50603
caps.latest.revision: 28
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0ca0020fa9025e57df874f8fa8b5eb41e63a8c29
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Comment : personnaliser des menus et des barres d'outils dans Visual Studio
Vous pouvez personnaliser Visual Studio non seulement en ajoutant et en supprimant des barres d'outils et des menus dans la barre de menus, mais aussi en ajoutant et en supprimant des commandes dans une barre d'outils ou un menu quelconques.  
  
> [!WARNING]
>  Après avoir personnalisé une barre d’outils ou un menu, veillez à ce que sa case demeure cochée dans la boîte de dialogue **Personnaliser**. Dans le cas contraire, vos modifications ne seront pas conservées une fois que vous aurez fermé et rouvert Visual Studio.  
  
 **Dans cette rubrique :**  
  
-   [Ajout, suppression ou déplacement d’un menu dans la barre de menus](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addmenu)  
  
-   [Ajout, suppression ou déplacement d’une barre d’outils](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addtoolbar)  
  
-   [Personnalisation d’un menu ou d’une barre d’outils](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_customize)  
  
-   [Réinitialisation d’un menu ou d’une barre d’outils](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_reset)  
  
##  <a name="bkmk_addmenu"></a> Ajout, suppression ou déplacement d’un menu dans la barre de menus  
  
1.  Dans la barre de menus, choisissez **Outils**, **Personnaliser**.  
  
     La boîte de dialogue **Personnaliser** s’affiche.  
  
2.  Sous l’onglet **Commandes**, laissez la case d’option **Barre de menus** sélectionnée, laissez l’option **Barre de menus** sélectionnée dans la liste située en regard de cette case d’option, puis exécutez l’une des procédures suivantes :  
  
    -   Pour ajouter un menu, choisissez le bouton **Ajouter un nouveau menu**, choisissez le bouton **Modifier la sélection**, puis nommez le menu à ajouter.  
  
         ![Boîte de dialogue Personnaliser montrant comment ajouter un menu](~/docs/ide/media/addmenu.png "AddMenu")  
  
    -   Pour supprimer un menu, choisissez-le dans la liste **Contrôles**, puis choisissez le bouton **Supprimer**.  
  
    -   Pour déplacer un menu dans la barre de menus, choisissez le menu dans la liste **Contrôles**, puis choisissez le bouton **Monter** ou **Descendre**.  
  
##  <a name="bkmk_addtoolbar"></a> Ajout, suppression ou déplacement d’une barre d’outils  
  
1.  Dans la barre de menus, choisissez **Outils**, **Personnaliser**.  
  
     La boîte de dialogue **Personnaliser** s’affiche.  
  
2.  Sous l’onglet **Barre d’outils**, exécutez l’une des procédures suivantes :  
  
    -   Pour ajouter une barre d’outils, choisissez le bouton **Nouveau**, spécifiez le nom de la barre d’outils à ajouter, puis choisissez le bouton **OK**.  
  
         ![Boîte de dialogue Personnaliser montrant comment ajouter une barre d’outils](~/docs/ide/media/addtoolbar.png "AddToolbar")  
  
    -   Pour supprimer une barre d’outils personnalisée, choisissez-la dans la liste **Barres d’outils**, puis choisissez le bouton **Supprimer**.  
  
        > [!IMPORTANT]
        >  Vous pouvez supprimer les barres d'outils que vous créez mais pas les barres d'outils par défaut.  
  
    -   Pour déplacer une barre d’outils vers un autre emplacement d’ancrage, choisissez-la dans la liste **Barres d’outils**, choisissez le bouton **Modifier la sélection**, puis choisissez un emplacement dans la liste qui s’affiche.  
  
         Vous pouvez également faire glisser le bord gauche d'une barre d'outils pour placer cette dernière n'importe où dans la zone d'ancrage principale.  
  
        > [!NOTE]
        >  Pour plus d’informations sur l’amélioration de l’utilisation et de l’accessibilité des barres d’outils, consultez [Guide pratique pour définir les options d’accessibilité IDE](../ide/reference/how-to-set-ide-accessibility-options.md).  
  
##  <a name="bkmk_customize"></a> Personnalisation d’un menu ou d’une barre d’outils  
  
1.  Dans la barre de menus, choisissez **Outils**, **Personnaliser**.  
  
     La boîte de dialogue **Personnaliser** s’affiche.  
  
2.  Sous l’onglet **Commandes**, choisissez la case d’option correspondant au type d’élément que vous souhaitez personnaliser.  
  
3.  Dans la liste correspondant à ce type d'élément, choisissez le menu ou la barre d'outils que vous souhaitez personnaliser, puis exécutez l'une des procédures suivantes :  
  
    -   Pour ajouter une commande, choisissez le bouton **Ajouter une commande**.  
  
         Dans la boîte de dialogue **Ajouter une commande**, choisissez un élément dans la liste **Catégories**, choisissez un élément dans la liste **Commandes**, puis choisissez le bouton **OK**.  
  
         ![Boîte de dialogue Ajouter une commande de Visual Studio](~/docs/ide/media/addcommand.png "AddCommand")  
  
    -   Pour supprimer une commande, choisissez-la dans la liste **Contrôles**, puis choisissez le bouton **Supprimer**.  
  
    -   Pour réorganiser des commandes, choisissez une commande dans la liste **Contrôles**, puis choisissez le bouton **Monter** ou **Descendre**.  
  
    -   Pour répartir les commandes dans des groupes, choisissez une commande dans la liste **Contrôles**, choisissez le bouton **Modifier la sélection**, puis choisissez **Nouveau groupe** dans le menu qui s’affiche.  
  
##  <a name="bkmk_reset"></a> Réinitialisation d’un menu ou d’une barre d’outils  
  
1.  Dans la barre de menus, choisissez **Outils**, **Personnaliser**.  
  
     La boîte de dialogue **Personnaliser** s’affiche.  
  
2.  Sous l’onglet **Commandes**, choisissez la case d’option correspondant au type d’élément que vous souhaitez réinitialiser.  
  
3.  Dans la liste correspondant à ce type d'élément, choisissez le menu ou la barre d'outils à réinitialiser.  
  
4.  Choisissez le bouton **Modifier la sélection**, puis choisissez **Réinitialiser** dans le menu qui s’affiche.  
  
     Vous pouvez également réinitialiser l’ensemble des menus et des barres d’outils en choisissant le bouton **Réinitialiser tout**.
