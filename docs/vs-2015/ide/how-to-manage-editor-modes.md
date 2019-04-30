---
title: 'Procédure : Gérer les Modes de l’éditeur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7db5f2869c1118a04f1aa734e5067ece4b268833
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430533"
---
# <a name="how-to-manage-editor-modes"></a>Procédure : Gérer les Modes de l’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez afficher l’éditeur de code Visual Studio dans différents modes d’affichage.  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="enabling-full-screen-mode"></a>Activation du mode Plein écran  
 Vous pouvez choisir de masquer toutes les fenêtres Outil et d’afficher uniquement les fenêtres de document en activant le mode **Plein écran**.  
  
#### <a name="to-enable-full-screen-mode"></a>Pour activer le mode Plein écran  
  
- Appuyez sur Alt+Maj+Entrée pour entrer en mode **Plein écran** ou le quitter.  
  
     – ou –  
  
- Exécutez la commande `View.Fullscreen` dans la fenêtre **Commande**.  
  
## <a name="enabling-virtual-space-mode"></a>Activation du mode Espace virtuel  
 En mode **Espace virtuel**, des espaces sont insérés à la fin de chaque ligne de code. Sélectionnez cette option pour placer des commentaires en un point précis, proche de votre code.  
  
#### <a name="to-enable-virtual-space-mode"></a>Pour activer le mode Espace virtuel  
  
1. Sélectionnez **Options** dans le menu **Outils**.  
  
2. Développez le dossier **Éditeur de texte** et choisissez **Tous les langages** pour définir cette option globalement, ou choisissez un dossier de langage spécifique. (Par exemple, pour activer les numéros de ligne uniquement dans Visual Basic, choisissez les options De base, Éditeur de texte.)  
  
3. Sélectionnez les options **Général**, puis, sous **Paramètres**, sélectionnez **Activer l’espace virtuel**.  
  
    > [!NOTE]
    > **Espace virtuel** est activé dans le mode **Sélectionner les colonnes**. Lorsque le mode **Espace virtuel** n’est pas activé, le point d’insertion passe de la fin d’une ligne directement au premier caractère de la suivante.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de l’éditeur](../ide/customizing-the-editor.md)   
 [Guide pratique pour Réorganiser et ancrer Windows](../misc/how-to-arrange-and-dock-windows.md)   
 [Polices et couleurs, Environnement, boîte de dialogue Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
