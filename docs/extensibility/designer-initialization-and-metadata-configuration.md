---
title: Initialisation du concepteur et configuration des métadonnées | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e876dd9e6fa95bbe180d1737bc8c4911f16e1e9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712212"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Initialisation du concepteur et configuration des métadonnées

La manipulation des métadonnées et des attributs de filtre associés à un concepteur ou à un composant de concepteur fournit un mécanisme permettant aux applications de définir les outils utilisés par un concepteur particulier pour gérer différents <xref:System.Type> objets (tels que des structures de données, des classes ou des entités graphiques), lorsque le concepteur est disponible et comment l’IDE Visual Studio est configuré **Toolbox** pour prendre en charge le concepteur (par exemple, la catégorie

Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit plusieurs mécanismes pour faciliter le contrôle de l’initialisation d’un concepteur ou d’un composant de concepteur, ainsi que la manipulation de ses métadonnées par un VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Initialiser les métadonnées et les informations de configuration
 Étant donné qu’ils sont chargés à la demande, les VSPackages n’ont peut-être pas été chargés par l’environnement Visual Studio avant l’instanciation d’un concepteur. Par conséquent, les VSPackages ne peuvent pas utiliser le mécanisme standard pour configurer un concepteur ou un composant de concepteur lors de la création, qui consiste à gérer un <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> événement. Au lieu de cela, un VSPackage implémente une instance de l' <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> interface et s’inscrit lui-même pour fournir des personnalisations, appelées extensions de l’aire de conception.

### <a name="customize-initialization"></a>Personnaliser l’initialisation

La personnalisation d’un concepteur, d’un composant ou d’une aire de conception implique les opérations suivantes :

1. Modification des métadonnées du concepteur et modification efficace de l’accès ou de la conversion d’un certain <xref:System.Type> .

    Cela s’effectue généralement par le biais des <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> mécanismes ou.

    Par exemple, lorsque des <xref:System.Windows.Forms> concepteurs basés sur sont initialisés, l’environnement Visual Studio modifie le <xref:System.Drawing.Design.UITypeEditor> pour les <xref:System.Web.UI.WebControls.Image> objets utilisés avec le concepteur afin d’utiliser le gestionnaire de ressources pour obtenir des bitmaps au lieu du système de fichiers.

2. Intégration à l’environnement, par exemple, en s’abonnant à des événements ou en obtenant des informations de configuration de projet. Vous pouvez obtenir des informations sur la configuration du projet et vous abonner aux événements en obtenant l' <xref:System.ComponentModel.Design.ITypeResolutionService> interface.

3. Modification de l’environnement utilisateur en activant les catégories appropriées de la **boîte à outils** ou en restreignant l’applicabilité du concepteur en appliquant une instance de la <xref:System.ComponentModel.ToolboxItemFilterAttribute> classe au concepteur.

### <a name="designer-initialization-by-a-vspackage"></a>Initialisation du concepteur par un VSPackage

Un VSPackage doit gérer l’initialisation du concepteur de la façon suivante :

1. Création d’un objet qui implémente la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe.

   > [!NOTE]
   > La <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe ne doit jamais être implémentée sur le même objet que la <xref:Microsoft.VisualStudio.Shell.Package> classe.

2. Inscription de la classe qui implémente <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> comme assurant la prise en charge des extensions de concepteur du VSPackage. Inscrivez la classe en appliquant des instances de  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> , <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> et <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> à la classe qui fournit l’implémentation du VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> .

Chaque fois qu’un concepteur ou un composant de concepteur est créé, l’environnement Visual Studio :

- Accède à chaque fournisseur d’extension de l’aire de conception inscrite.

- Instancie et Initialise une instance de chaque objet du fournisseur d’extensions de l’aire de conception <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> .

- Appelle la méthode ou la méthode de chaque fournisseur d’extension de l’aire de conception <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> (selon le cas).

Lors de l’implémentation <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> de l’objet en tant que membre d’un VSPackage, il est important de comprendre ce qui suit :

- L’environnement Visual Studio ne fournit aucun contrôle sur les métadonnées ou autres paramètres de configuration qu’un `DesignSurfaceExtension` fournisseur particulier modifie. Il est possible que deux fournisseurs ou plus `DesignSurfaceExtension` modifient la même fonctionnalité de concepteur de manière contradictoire, avec la modification finale définitive. La dernière modification appliquée est indéterminée.

- Il est possible de limiter explicitement une implémentation de l' <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objet à des concepteurs spécifiques en appliquant des instances de <xref:System.ComponentModel.ToolboxItemFilterAttribute> à cette implémentation. Pour plus d’informations sur le filtrage des éléments de **boîte à outils** , consultez <xref:System.ComponentModel.ToolboxItemFilterAttribute> et <xref:System.ComponentModel.ToolboxItemFilterType> .

## <a name="additional-metadata-provisioning"></a>Approvisionnement de métadonnées supplémentaires

Un VSPackage peut modifier la configuration d’un concepteur ou d’un composant de concepteur autre qu’au moment de la conception.

La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe peut être utilisée par programmation ou appliquée à un VSPackage qui fournit un concepteur.

Une instance de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe est utilisée pour modifier les métadonnées des composants créés sur une aire de conception. Par exemple, il est possible de remplacer un Explorateur de propriétés par défaut utilisé par des <xref:System.Windows.Forms.CommonDialog> objets avec un Explorateur de propriétés personnalisé.

Les modifications fournies par une instance de <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> appliquée à l’implémentation d’un VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> peuvent avoir l’une des deux étendues suivantes :

- Global--pour toutes les nouvelles instances d’un composant donné

- Local : se rapportant uniquement à l’instance du composant créé sur une aire de conception fournie par le VSPackage actuel.

La `IsGlobal` propriété de l' <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> instance appliquée à l’implémentation d’un VSPackage <xref:Microsoft.VisualStudio.Shell.Package> détermine cette portée.

L’application de l’attribut à une implémentation de <xref:Microsoft.VisualStudio.Shell.Package> avec la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> propriété de l’objet ayant la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> valeur `true` , comme ci-dessous, modifie le navigateur pour l’ensemble de l’environnement Visual Studio :

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Si l’indicateur global a la valeur `false` , la modification des métadonnées est locale par le concepteur actuel pris en charge par le VSPackage actuel :

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> L’aire de conception ne prend en charge que la création de composants et, par conséquent, seuls les composants peuvent avoir des métadonnées locales. Dans l’exemple ci-dessus, nous avons tenté de modifier une propriété, telle que la `Color` propriété d’un objet. Si `false` a été passé pour l’indicateur global, n' `CustomBrowser` apparaîtrait jamais, car le concepteur ne crée jamais d’instance de `Color` . La définition de l’indicateur global sur `false` est utile pour les composants, tels que les contrôles, les minuteurs et les boîtes de dialogue.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Étendre la prise en charge au moment du design](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
