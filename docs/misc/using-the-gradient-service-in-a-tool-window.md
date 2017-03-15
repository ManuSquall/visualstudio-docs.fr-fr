---
title: "Utilisation du service d&#233;grad&#233; dans une fen&#234;tre Outil | Microsoft Docs"
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
  - "services, procédures pas à pas"
  - "fenêtres Outil, service dégradé"
  - "service dégradé, procédures pas à pas"
  - "services, utiliser"
ms.assetid: 67590982-6e1f-4e4b-be18-7d1b294cabff
caps.latest.revision: 44
caps.handback.revision: 44
manager: "douge"
---
# Utilisation du service d&#233;grad&#233; dans une fen&#234;tre Outil
Étant donné que les fenêtres Outil de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sont générées avec Windows \(WPF\) Presentation Foundation, vous ne devez pas appeler le service dégradé dans le code.  À la place, dans le concepteur représentant la surface de la fenêtre Outil, sélectionnez l'élément de `StackPanel` , puis, dans la fenêtre de **Propriétés** , modifiez la propriété d' **Arrière\-plan** pour définir le dégradé.  Pour plus d'informations, consultez [Définition des couleurs, des dégradés et de l’opacité](../misc/setting-colors-gradients-and-opacity.md).  
  
## Voir aussi  
 [NOT IN BUILD: Tool Window Walkthroughs](http://msdn.microsoft.com/fr-fr/ecffc579-0e96-48ad-90f3-01a3d80f3ce5)   
 [Extension des fenêtres Outil](../misc/extending-tool-windows.md)   
 [Définition des couleurs, des dégradés et de l’opacité](../misc/setting-colors-gradients-and-opacity.md)