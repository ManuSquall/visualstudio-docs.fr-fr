---
title: Vue d’ensemble de la couleur et de police | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da93d4f98bf3795c2dd60b02f9cf5b332b022ad2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684960"
---
# <a name="font-and-color-overview"></a>Vue d’ensemble de police et de couleur
Cette rubrique décrit les paramètres de police et la couleur du texte dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Il présente également les concepts des catégories et des éléments d’affichage, et il explique comment les VSPackages et l’éditeur principal utilisent des attributs de texte.

## <a name="the-fonts-and-colors-property-page"></a>Les polices et couleurs propriété page
 Vous pouvez gérer les attributs du texte affiché dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) via la **polices et couleurs** page de propriétés. Pour rechercher le **polices et couleurs** page de propriété, sur le **outils** menu, cliquez sur **Options**. Développez l’option **Environnement**, puis cliquez sur **Polices et couleurs**.

## <a name="categories-and-display-items"></a>Catégories et les éléments d’affichage
 Polices et couleurs sont organisés en **catégories** et **éléments affichés**.

- Un **catégorie** est un conteneur logique ou fonctionnels pour un nombre de **éléments affichés**.

   Une liste de **catégories** est dans le **afficher les paramètres de** zone de liste déroulante de la **polices et couleurs** page de propriétés.

- Un **élément d’affichage** est une entité de texte bien défini comme un commentaire, une chaîne ou une structure de contrôle qui est à mettre en couleur lorsque affichée.

  Chaque **élément d’affichage** est défini de manière unique dans le **catégorie** qui le contient. Par conséquent, plusieurs **catégorie** peut avoir un **élément d’affichage** portant le même nom.

## <a name="vspackage-control-of-fonts-and-colors"></a>Contrôle de VSPackage de polices et couleurs
 Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] permet les VSPackages pour :

- Définir la police et couleur **catégories**.

- Spécifier les polices et couleurs utilisées pour présenter **éléments affichés**.

- Interagir avec le **polices et couleurs** page de propriétés.

- Agréger plusieurs **catégories** en groupes.

- Conserver les modifications dans les paramètres par défaut.

  Il existe deux façons d’interagir avec la police et la couleur des sélections dans la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].

- Une façon est appelé *la coloration de syntaxe*. Il est utilisé par un VSPackage qui personnalise existant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur pour implémenter un service de langage et de créer une source de l’éditeur.

   Seul **catégorie** prend en charge ce mécanisme, à savoir, le **éditeur de texte**.

- Une alternative plus générale prend en charge tous les autres **catégories** et composants d’interface utilisateur autre que l’éditeur de source lors de l’affichage de texte. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.

## <a name="core-editor-text-settings"></a>Paramètres de texte éditeur Core
 Paramètres de police et de couleur pour l’éditeur principal d’un objet de service de langage sont régies par la **texte EditorCategory** trouvé dans le **afficher les paramètres de** zone de liste déroulante de la **polices et couleurs** page de propriétés.

 Lorsque vous travaillez avec les éditeurs, vous devez utiliser le mécanisme de contrôle de couleur fournies par le service de langage permettant de contrôler et d’étendre et de police spécialisé le **éditeur de texte** paramètres. Le mécanisme est appelé *la coloration syntaxique* et fournit :

- Une technique simplifiée pour la gestion des polices et couleurs des éléments d’affichage.

   Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

- Un mécanisme de colorisation bien définis et optimisée.

   Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.

- La possibilité pour les deux utiliser des éléments d’affichage intégrées à partir de la **texte EditorCategory** et d’étendre les.

   Pour plus d'informations, voir [Procédure : Utiliser des éléments coloriables intégrés](../extensibility/internals/how-to-use-built-in-colorable-items.md) et [éléments coloriables personnalisés](../extensibility/internals/custom-colorable-items.md).

- Persistance automatique du courant de l’état de ces deux intégrés et personnalisé afficher les éléments avec le **éditeur de texte** catégorie.

  Pour plus d’informations sur la syntaxe de coloration de la voir [couleurs de syntaxe dans un service de langage hérité](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

## <a name="see-also"></a>Voir aussi
- [Interfaces héritées dans l’éditeur](../extensibility/legacy-interfaces-in-the-editor.md)
- [Couleurs de syntaxe dans un service de langage hérité](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)