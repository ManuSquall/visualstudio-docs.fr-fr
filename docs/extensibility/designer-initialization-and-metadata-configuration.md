---
title: Designer Initialisation et Configuration des métadonnées Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712212"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Initialisation et configuration de métadonnées de concepteur

La manipulation des métadonnées et des attributs de filtre associés à un composant de concepteur ou <xref:System.Type> de concepteur fournit un mécanisme pour les applications pour définir quels outils sont utilisés par un concepteur particulier pour manipuler différents objets (tels que les structures de données, les classes ou les entités graphiques), quand le concepteur est disponible, et comment le Visual Studio IDE est configuré pour prendre en charge le concepteur (par exemple quelle catégorie ou onglet **de boîte** à outils est disponible).

Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit plusieurs mécanismes pour faciliter le contrôle de l’initialisation d’un concepteur ou d’un composant de concepteur et la manipulation de ses métadonnées par un VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Initialiser les métadonnées et les informations de configuration
 Parce qu’ils sont chargés sur demande, VSPackages peut ne pas avoir été chargé par l’environnement Visual Studio avant l’instantanéisation d’un concepteur. Par conséquent, VSPackages ne peut pas utiliser le mécanisme standard pour configurer <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> un composant de concepteur ou de concepteur sur la création, qui est de gérer un événement. Au lieu de cela, un VSPackage implémente une instance de l’interface <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> et s’enregistre pour fournir des personnalisations, appelées extensions de surface de conception.

### <a name="customize-initialization"></a>Personnaliser l’initialisation

Personnaliser un concepteur, un composant ou une surface de concepteur implique :

1. Modification des métadonnées du concepteur <xref:System.Type> et modification efficace de la façon dont un certain est accessible ou converti.

    Cela se fait <xref:System.Drawing.Design.UITypeEditor> généralement <xref:System.ComponentModel.TypeConverter> par le biais de l’ou des mécanismes.

    Par exemple, <xref:System.Windows.Forms>lorsque les concepteurs basés sont parasés, l’environnement Visual Studio modifie le <xref:System.Drawing.Design.UITypeEditor> pour <xref:System.Web.UI.WebControls.Image> les objets utilisés avec le concepteur pour utiliser le gestionnaire de ressources pour obtenir des bitmaps plutôt que le système de fichiers.

2. S’intégrer à l’environnement, par exemple, en s’abonnant à des événements ou en obtenant des informations sur la configuration du projet. Vous pouvez obtenir des informations de configuration <xref:System.ComponentModel.Design.ITypeResolutionService> de projet et vous abonner aux événements en obtenant l’interface.

3. Modification de l’environnement utilisateur en activant les catégories appropriées **de boîte à** outils <xref:System.ComponentModel.ToolboxItemFilterAttribute> ou en limitant l’applicabilité du concepteur en appliquant une instance de la classe au concepteur.

### <a name="designer-initialization-by-a-vspackage"></a>Initialisation du concepteur par un VSPackage

Un VSPackage doit gérer l’initialisation du concepteur en :

1. Création d’un <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objet mettant en œuvre la classe.

   > [!NOTE]
   > La <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe ne doit jamais être <xref:Microsoft.VisualStudio.Shell.Package> mise en œuvre sur le même objet que la classe.

2. Enregistrement de la classe <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> qui met en œuvre comme fournissant un soutien pour les extensions de concepteur de la VSPackage. Enregistrez la classe <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>en <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>appliquant des instances de , , <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> et <xref:Microsoft.VisualStudio.Shell.Package>à la classe qui fournit la mise en œuvre du VSPackage de .

Chaque fois qu’un composant designer ou designer est créé, l’environnement Visual Studio :

- Accès à chaque fournisseur d’extension de surface de conception enregistré.

- Instantiates et initialise une instance de l’objet de chaque fournisseur d’extension de surface de <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> conception.

- Appelle la méthode ou <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> méthode de chaque fournisseur d’extension de surface de conception (le cas échéant).

Lors de <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> la mise en œuvre de l’objet en tant que membre d’un VSPackage, il est important de comprendre que:

- L’environnement Visual Studio ne donne aucun contrôle sur les `DesignSurfaceExtension` métadonnées ou autres paramètres de configuration modifiés par un fournisseur particulier. Il est possible pour `DesignSurfaceExtension` deux fournisseurs ou plus de modifier la même fonctionnalité de concepteur de manière contradictoire, avec la modification finale étant définitive. Il est indéterminé quelle modification est appliquée pour la dernière fois.

- Il est possible de limiter explicitement <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> la mise en œuvre de l’objet à des concepteurs spécifiques en appliquant des <xref:System.ComponentModel.ToolboxItemFilterAttribute> instances à cette implémentation. Pour plus d’informations sur le filtrage de l’élément **Toolbox,** voir le <xref:System.ComponentModel.ToolboxItemFilterAttribute> et <xref:System.ComponentModel.ToolboxItemFilterType>.

## <a name="additional-metadata-provisioning"></a>Fourniture de métadonnées supplémentaires

Un VSPackage peut modifier la configuration d’un composant de concepteur ou de concepteur autre qu’au moment de la conception.

La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe peut être utilisée de façon programmatique ou appliquée à un VSPackage qui fournit un concepteur.

Une instance <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> de la classe est utilisée pour modifier les métadonnées des composants créés sur une surface de conception. Par exemple, on pourrait remplacer un <xref:System.Windows.Forms.CommonDialog> navigateur de propriété par défaut utilisé par des objets par un navigateur de propriété personnalisé.

Les modifications fournies <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> par une instance d’application <xref:Microsoft.VisualStudio.Shell.Package> à la mise en œuvre d’un VSPackage peuvent avoir l’une des deux portées :

- Global -- pour tous les nouveaux cas d’un composant donné

- Local -- se rapportant uniquement à l’exemple du composant créé sur une surface de conception fournie par le VSPackage actuel.

La `IsGlobal` propriété <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> de l’instance s’appliquait <xref:Microsoft.VisualStudio.Shell.Package> à la mise en œuvre d’un VSPackage de détermine cette portée.

L’application de l’attribut <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> à <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> une implémentation de <xref:Microsoft.VisualStudio.Shell.Package> la propriété de l’objet réglé à `true`, comme ci-dessous, change le navigateur pour l’ensemble de l’environnement Visual Studio:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Si le drapeau mondial `false`a été fixé à , puis le changement de métadonnées est local pour le concepteur actuel soutenu par l’actuel VSPackage:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> La surface de conception ne prend en charge la création de composants, et donc seuls les composants peuvent avoir des métadonnées locales. Dans l’exemple ci-dessus, nous tentions `Color` de modifier une propriété, comme la propriété d’un objet. Si `false` a été passé pour `CustomBrowser` le drapeau mondial, n’apparaîtrait `Color`jamais parce que le concepteur ne crée jamais réellement un exemple de . La mise en `false` place du drapeau mondial est utile pour les composants, tels que les commandes, les minuteries et les boîtes de dialogue.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Étendre le support de conception-temps](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
