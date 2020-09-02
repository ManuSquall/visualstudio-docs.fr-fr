---
title: Vue d’ensemble des polices et des couleurs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a20cfa2372b1e55652ffcebe6d173cff86140a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204348"
---
# <a name="font-and-color-overview"></a>Présentation de la couleur et de la police
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique décrit les paramètres de police et de couleur du texte dans l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environnement de développement intégré (IDE). Il présente également les concepts des catégories et des éléments d’affichage, et décrit comment les VSPackages et l’éditeur de base utilisent des attributs de texte.  
  
## <a name="the-fonts-and-colors-property-page"></a>Page de propriétés polices et couleurs  
 Vous pouvez gérer les attributs du texte affiché dans l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environnement de développement intégré (IDE) à l’aide de la page de propriétés **polices et couleurs** . Pour rechercher la page de propriétés **polices et couleurs** , dans le menu **Outils** , cliquez sur **options**. Développez l’option **Environnement**, puis cliquez sur **Polices et couleurs**.  
  
## <a name="categories-and-display-items"></a>Catégories et éléments affichés  
 Les polices et les couleurs sont organisées en **catégories** et en **éléments d’affichage**.  
  
- Une **catégorie** est un conteneur logique ou fonctionnel pour un certain nombre d' **éléments d’affichage**.  
  
   Une liste de **catégories** se trouve dans la zone de liste déroulante **afficher les paramètres** de de la page de propriétés **polices et couleurs** .  
  
- Un **élément d’affichage** est une entité de texte bien définie, telle qu’un commentaire, une chaîne ou une structure de contrôle qui doit être coloriée lorsqu’elle est affichée.  
  
  Chaque **élément d’affichage** est défini de façon unique dans la **catégorie** qui le contient. Par conséquent, plusieurs **catégories** peuvent avoir un **élément d’affichage** portant le même nom.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Contrôle VSPackage des polices et des couleurs  
 Le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] permet aux VSPackages de :  
  
- Définir les **catégories**de polices et de couleurs.  
  
- Spécifiez les polices et les couleurs utilisées pour présenter les **éléments d’affichage**.  
  
- Interagissez avec la page de propriétés **polices et couleurs** .  
  
- Regroupez plusieurs **catégories** dans des groupes.  
  
- Conserver les modifications dans les paramètres par défaut.  
  
  Il existe deux façons d’interagir avec les sélections de polices et de couleurs dans le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .  
  
- L’une des méthodes est appelée *coloration*de la syntaxe. Il est utilisé par un VSPackage qui personnalise l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur existant pour implémenter un service de langage et créer un éditeur de code source.  
  
   Une seule **catégorie** prend en charge ce mécanisme, à savoir, l' **éditeur de texte**.  
  
- Une alternative plus générale prend en charge toutes les autres **catégories** et composants de l’interface utilisateur autres que l’éditeur de code source lors de l’affichage de texte. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Paramètres de texte de l’éditeur principal  
 Les paramètres de police et de couleur pour l’éditeur de base d’un objet de service de langage sont régis par le **texte EditorCategory** figurant dans la zone de liste déroulante **afficher les paramètres** de de la page de propriétés **polices et couleurs** .  
  
 Lorsque vous utilisez des éditeurs, vous devez utiliser le mécanisme de contrôle de police et de couleur spécialisé que le service de langage fournit pour contrôler et étendre les paramètres de l' **éditeur de texte** . Le mécanisme est appelé coloration de la *syntaxe* et fournit les éléments suivants :  
  
- Technique simplifiée pour la gestion des polices et des couleurs des éléments d’affichage.  
  
   Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
- Un mécanisme de colorisation bien défini et optimisé.  
  
   Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
- La possibilité d’utiliser des éléments d’affichage intégrés à partir du **EditorCategory de texte** et de les étendre.  
  
   Pour plus d’informations, consultez [Comment : utiliser des éléments coloriables intégrés](../extensibility/internals/how-to-use-built-in-colorable-items.md) et des [éléments coloriables personnalisés](../extensibility/internals/custom-colorable-items.md).  
  
- Persistance automatique de l’état actuel des éléments d’affichage intégrés et personnalisés avec la catégorie **éditeur de texte** .  
  
  Pour plus d’informations sur la coloration de [la syntaxe, consultez coloration de la syntaxe dans un service de langage hérité](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces héritées dans l’éditeur](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Couleurs de syntaxe dans un service de langage hérité](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
