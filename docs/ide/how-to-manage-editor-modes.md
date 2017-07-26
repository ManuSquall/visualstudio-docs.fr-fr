---
title: "Guide pratique pour gérer les modes de l’éditeur | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
caps.latest.revision: 20
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 71566f11a069d266ded2aebe02bbf388cf00730e
ms.contentlocale: fr-fr
ms.lasthandoff: 05/24/2017

---
# <a name="how-to-manage-editor-modes"></a>Guide pratique pour gérer les modes de l'éditeur
Vous pouvez afficher l’éditeur de code Visual Studio dans différents modes d’affichage.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="enabling-full-screen-mode"></a>Activation du mode Plein écran  
 Vous pouvez choisir de masquer toutes les fenêtres Outil et d’afficher uniquement les fenêtres de document en activant le mode **Plein écran**.  
  
#### <a name="to-enable-full-screen-mode"></a>Pour activer le mode Plein écran  
  
-   Appuyez sur Alt+Maj+Entrée pour entrer en mode **Plein écran** ou le quitter.  
  
     – ou –  
  
-   Exécutez la commande `View.Fullscreen` dans la fenêtre **Commande**.  
  
## <a name="enabling-virtual-space-mode"></a>Activation du mode Espace virtuel  
 En mode **Espace virtuel**, des espaces sont insérés à la fin de chaque ligne de code. Sélectionnez cette option pour placer des commentaires en un point précis, proche de votre code.  
  
#### <a name="to-enable-virtual-space-mode"></a>Pour activer le mode Espace virtuel  
  
1.  Sélectionnez **Options** dans le menu **Outils**.  
  
2.  Développez le dossier **Éditeur de texte** et choisissez **Tous les langages** pour définir cette option globalement, ou choisissez un dossier de langage spécifique. (Par exemple, pour activer les numéros de ligne uniquement dans Visual Basic, choisissez les options De base, Éditeur de texte.)  
  
3.  Sélectionnez les options **Général**, puis, sous **Paramètres**, sélectionnez **Activer l’espace virtuel**.  
  
    > [!NOTE]
    >  **Espace virtuel** est activé dans le mode **Sélectionner les colonnes**. Lorsque le mode **Espace virtuel** n’est pas activé, le point d’insertion passe de la fin d’une ligne directement au premier caractère de la suivante.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de l’éditeur](../ide/customizing-the-editor.md)   
 [Personnalisation des dispositions de fenêtres dans Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)   
 [Polices et couleurs, Environnement, boîte de dialogue Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
