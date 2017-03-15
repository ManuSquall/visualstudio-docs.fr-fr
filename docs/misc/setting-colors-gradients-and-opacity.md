---
title: "D&#233;finition des couleurs, des d&#233;grad&#233;s et de l’opacit&#233; | Microsoft Docs"
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
  - "conception d’éléments d’interface utilisateur [Visual Studio SDK]"
ms.assetid: 1734bdc7-5e16-46c7-8507-eef5cea75cb9
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# D&#233;finition des couleurs, des d&#233;grad&#233;s et de l’opacit&#233;
Tous les éléments d’interface utilisateur de Visual Studio sont créés dans Windows Presentation Foundation \(WPF\). Quand vous créez des fenêtres Outil ou d’autres éléments d’interface utilisateur, vous pouvez donc appliquer des couleurs, des dégradés et une opacité en définissant les attributs appropriés pour ces éléments. Vous pouvez leur attribuer des valeurs spécifiques à l’aide de la fenêtre **Propriétés** ou vous pouvez lancer une requête dans l’environnement de développement intégré \(IDE\) pour connaître les valeurs système. Les valeurs système sont recommandées quand vous voulez que vos extensions ressemblent au reste de l’IDE.  
  
 L’interface utilisateur de Windows Forms et l’interface utilisateur du code natif sont encore prises en charge pour la compatibilité descendante. Pour plus d’informations sur la définition des couleurs et des dégradés dans les extensions non WPF, consultez la documentation [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
## Définition des couleurs, des dégradés et de l’opacité  
 Vous pouvez modifier l’apparence de la plupart des éléments XAML en définissant leurs attributs `Background`, `Foreground`, `Opacity` ou autres attributs visuels. Ces attributs correspondent aux propriétés qui acceptent <xref:System.Windows.Media.Brush?displayProperty=fullName> en tant que valeur.  
  
#### Pour définir les couleurs d’arrière\-plan, les dégradés et l’opacité dans une fenêtre Outil  
  
1.  Ouvrez MyControl.xaml.  
  
2.  Dans le volet **XAML**, dans l’élément <xref:System.Windows.Controls.UserControl> de niveau supérieur, tapez `background=`.  
  
     IntelliSense affiche une liste de couleurs pour l’attribut BackGround.  
  
     Sélectionnez une couleur dans la liste.  
  
3.  Dans la fenêtre **Propriétés**, développez le nœud **Pinceaux**, puis cliquez sur **Arrière\-plan**.  
  
     La fenêtre **Propriétés** affiche un sélecteur de couleurs. Au\-dessus du sélecteur de couleurs se trouve une rangée d’icônes représentant des pinceaux.  
  
4.  Utilisez les curseurs pour choisir une couleur.  
  
     Le code XAML est immédiatement mis à jour pour afficher la nouvelle couleur d’arrière\-plan.  
  
5.  Cliquez sur l’icône Pinceau de dégradé.  
  
     Le sélecteur de couleurs devient un sélecteur de dégradé.  
  
6.  Utilisez les curseurs pour choisir un dégradé.  
  
     Le code XAML est immédiatement mis à jour pour afficher le nouveau dégradé d’arrière\-plan.  
  
7.  Cliquez sur l’icône Pinceau image.  
  
     Le sélecteur de dégradé devient un outil de sélection d’image.  
  
8.  Sélectionnez une image et définissez ses paramètres d’étirement et de mosaïque.  
  
     Le code XAML est immédiatement mis à jour pour afficher la nouvelle image d’arrière\-plan.  
  
9. Cliquez sur l’icône Pinceau Null.  
  
     L’arrière\-plan du concepteur redevient neutre et l’attribut `BackGround` est défini sur `"{x:Null}"`.  
  
## Interrogation des valeurs système  
 Vous pouvez interroger les valeurs système à l’aide des propriétés de classe <xref:Microsoft.VisualStudio.Shell.VsBrushes?displayProperty=fullName> qui font référence aux pinceaux définis dans d’autres sections de Visual Studio.  
  
#### Pour définir les couleurs, les dégradés et l’opacité en interrogeant les valeurs système  
  
1.  Sélectionnez un élément XAML.  
  
2.  Dans la définition de l’élément, définissez l’un des attributs visuels de l’élément sur une propriété de la classe `VsBrushes`, comme indiqué dans l’exemple suivant.  
  
     [!code-xml[TWShortcutMenu#32](../misc/codesnippet/Xaml/setting-colors-gradients-and-opacity_1.xaml)]  
  
     L’extension [DynamicResource](../Topic/DynamicResource%20Markup%20Extension.md) permet à la valeur d’être modifiée selon les besoins, par exemple, quand un utilisateur modifie les paramètres. Vous devez utiliser l’extension [x:Static](../Topic/x:Static%20Markup%20Extension.md), car la classe `VsBrushes` ne fait pas partie de l’espace de noms WPF par défaut.  
  
## Voir aussi  
 [Extension des fenêtres Outil](../misc/extending-tool-windows.md)