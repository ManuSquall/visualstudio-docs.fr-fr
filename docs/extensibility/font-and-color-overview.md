---
title: "Vue d’ensemble de la couleur et de police | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13a2a8b584af507f8937fd6abb46c85f329de0b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="font-and-color-overview"></a>Vue d’ensemble de la couleur et de police
Cette rubrique décrit les paramètres de police et la couleur du texte dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Elle présente également les concepts de catégories et les éléments d’affichage, et elle explique également comment les VSPackages et l’éditeur principal utilisent les attributs de texte.  
  
## <a name="the-fonts-and-colors-property-page"></a>La Page polices et couleurs propriété  
 Vous pouvez gérer les attributs du texte affiché dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) via la **polices et couleurs** page de propriétés. Pour rechercher la **polices et couleurs** page de propriété, sur le **outils** menu, cliquez sur **Options**. Développez **environnement**, puis cliquez sur **polices et couleurs**.  
  
## <a name="categories-and-display-items"></a>Catégories et les éléments d’affichage  
 Polices et couleurs sont organisés en **catégories** et **afficher les éléments**.  
  
-   A **catégorie** est un conteneur logique ou fonctionnel pour un certain nombre de **afficher les éléments**.  
  
     Une liste de **catégories** est dans le **afficher les paramètres de** zone de liste déroulante de la **polices et couleurs** page de propriétés.  
  
-   A **élément d’affichage** est une entité de texte bien défini comme un commentaire, une chaîne ou une structure de contrôle à colorisés lorsque affichée.  
  
 Chaque **élément d’affichage** est défini de manière unique dans le **catégorie** qui le contient. Par conséquent, plusieurs **catégorie** peut avoir un **élément d’affichage** portant le même nom.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Contrôle VSPackage polices et couleurs  
 Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] permet de VSPackages à :  
  
-   Définir la police et couleur **catégories**.  
  
-   Spécifier les polices et les couleurs utilisées pour présenter **afficher les éléments**.  
  
-   Interagir avec les **polices et couleurs** page de propriétés.  
  
-   Agrégation multiple **catégories** en groupes.  
  
-   Conserver les modifications dans les paramètres par défaut.  
  
 Il existe deux moyens d’interagir avec la police et la couleur des sélections dans la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
-   Une façon est appelé *coloration de la syntaxe*. Il est utilisé par un VSPackage qui personnalise existants [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’éditeur pour implémenter un service de langage et de créer une source de l’éditeur.  
  
     Seul **catégorie** prend en charge de ce mécanisme, à savoir, le **éditeur de texte**.  
  
-   Une alternative plus générale prend en charge tous les autres **catégories** et les composants d’interface utilisateur autre que l’éditeur de code source lors de l’affichage de texte. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Paramètres du texte de l’éditeur de base  
 Paramètres de police et la couleur de l’éditeur de base d’un objet de service de langage sont régies par la **texte EditorCategory** trouvé dans le **afficher les paramètres de** zone de liste déroulante de la **polices et couleurs** page de propriétés.  
  
 Lorsque vous travaillez avec les éditeurs, vous devez utiliser le mécanisme de contrôle de couleur que le service de langage fournit pour contrôler et d’étendre et de police spécialisée la **éditeur de texte** paramètres. Le mécanisme est appelé *la coloration de syntaxe* et fournit :  
  
-   Une technique simplifiée pour gérer les polices et couleurs des éléments d’affichage.  
  
     Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
-   Un mécanisme de colorisation bien définis et optimisée.  
  
     Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
-   La possibilité d’utiliser des éléments d’affichage intégré à partir de la **texte EditorCategory** et de les étendre.  
  
     Pour plus d’informations, consultez [Comment : utiliser les éléments intégrés coloriable](../extensibility/internals/how-to-use-built-in-colorable-items.md) et [les éléments coloriable personnalisé](../extensibility/internals/custom-colorable-items.md).  
  
-   Persistance automatique en cours de l’état de ces deux intégrés et personnalisés afficher les éléments avec la **éditeur de texte** catégorie.  
  
 Pour plus d’informations sur la syntaxe de coloration de la voir [coloration de syntaxe dans un Service de langage hérité](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces héritées dans l’éditeur](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Couleurs de syntaxe dans un service de langage hérité](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)