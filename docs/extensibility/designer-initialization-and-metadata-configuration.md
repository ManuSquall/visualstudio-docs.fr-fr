---
title: L’initialisation du concepteur et Configuration des métadonnées | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3084561be779eba73aa21ba7f23f7f5265bfd5b3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348127"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Configuration de l’initialisation et de métadonnées de concepteur

Manipulation des attributs de métadonnées et de filtre associé à un concepteur ou un composant de concepteur fournit un mécanisme permettant aux applications de définir quels outils sont utilisés par un concepteur particulier pour gérer différents <xref:System.Type> objets (tels que les structures de données, classes, ou les entités graphiques), lorsque le concepteur est disponible, et comment l’IDE Visual Studio est configuré pour prendre en charge le concepteur (pour une instance qui **boîte à outils** catégorie ou un onglet est disponible).

Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit plusieurs mécanismes pour faciliter le contrôle de l’initialisation du concepteur ou de du composant de concepteur et la manipulation de ses métadonnées par un VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Initialiser les informations de configuration et métadonnées
 Car elles sont chargées à la demande, VSPackages n’ont ne peut-être pas été chargés par l’environnement Visual Studio avant l’instanciation d’un concepteur. Par conséquent, les VSPackages ne peut pas utiliser le mécanisme standard pour la configuration d’un concepteur ou un composant de concepteur sur la création, qui consiste à gérer un <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> événement. Au lieu de cela, un VSPackage implémente une instance de la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> interface et s’inscrit lui-même pour fournir des personnalisations, appelées extensions de surface de conception.

### <a name="customize-initialization"></a>Personnaliser l’initialisation

Personnalisation d’un concepteur, un composant ou une aire du concepteur, implique :

1. Modifier les métadonnées du concepteur et qui permet de modifier comment un certain <xref:System.Type> est accessible ou converti.

    Cela est généralement effectuée via la <xref:System.Drawing.Design.UITypeEditor> ou <xref:System.ComponentModel.TypeConverter> mécanismes.

    Par exemple, lorsque <xref:System.Windows.Forms>-en fonction des concepteurs sont initialisées, l’environnement Visual Studio modifie le <xref:System.Drawing.Design.UITypeEditor> pour <xref:System.Web.UI.WebControls.Image> objets utilisés avec le concepteur à utiliser le Gestionnaire de ressources pour obtenir des images bitmap plutôt que le système de fichiers.

2. L’intégration avec l’environnement, par exemple, en s’abonnant aux événements ou l’obtention des informations de configuration de projet. Vous pouvez obtenir des informations de configuration de projet et s’abonner aux événements en obtenant le <xref:System.ComponentModel.Design.ITypeResolutionService> interface.

3. Modification de l’environnement utilisateur en activant approprié **boîte à outils** catégories ou en limitant la mise en application du concepteur en appliquant une instance de la <xref:System.ComponentModel.ToolboxItemFilterAttribute> classe vers le concepteur.

### <a name="designer-initialization-by-a-vspackage"></a>Initialisation du concepteur par un VSPackage

Un VSPackage doit gérer l’initialisation du concepteur par :

1. Création d’un objet qui implémente le <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe.

   > [!NOTE]
   > Le <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe ne doit jamais être implémentée sur le même objet que la <xref:Microsoft.VisualStudio.Shell.Package> classe.

2. L’inscription de la classe qui implémente <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> en tant que la prise en charge d’extensions de concepteur du VSPackage. Inscrire la classe en appliquant des instances de <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>, et <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> à la classe qui fournit l’implémentation du VSPackage de <xref:Microsoft.VisualStudio.Shell.Package>.

Chaque fois qu’un concepteur ou un composant de concepteur est créé, l’environnement Visual Studio :

- Accède à chaque fournisseur d’extension de l’aire de conception inscrits.

- Instancie et initialise une instance de chaque fournisseur d’extension de l’aire de conception <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objet.

- Appelle chaque fournisseur d’extension de l’aire de conception <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> méthode ou <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> (méthode) (le cas échéant).

Lorsque vous implémentez le <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> de l’objet en tant que membre d’un VSPackage, il est important de comprendre que :

- L’environnement Visual Studio ne fournit pas de n’importe quel contrôle sur les métadonnées ou d’autres paramètres de configuration événements `DesignSurfaceExtension` modifie du fournisseur. Il est possible pour plusieurs `DesignSurfaceExtension` fournisseurs de modification de la même fonctionnalité de Concepteur de manières en conflit, avec la dernière modification est définitive. Il est indéterminé quelle modification est appliquée en dernier.

- Il est possible de restreindre explicitement une implémentation de la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objet aux concepteurs spécifiques en appliquant des instances de <xref:System.ComponentModel.ToolboxItemFilterAttribute> à cette implémentation. Pour plus d’informations sur **boîte à outils** filtrage d’élément, consultez la <xref:System.ComponentModel.ToolboxItemFilterAttribute> et <xref:System.ComponentModel.ToolboxItemFilterType>.

## <a name="additional-metadata-provisioning"></a>L’approvisionnement des métadonnées supplémentaires

Un VSPackage peut modifier la configuration d’un concepteur ou un composant de concepteur différent au moment du design.

Le <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe peut être utilisée par programmation ou appliquée à un VSPackage qui fournit un concepteur.

Une instance de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe est utilisée pour modifier les métadonnées de composants créés sur une aire de conception. Par exemple, un peut substituer un Explorateur de propriétés par défaut utilisé par <xref:System.Windows.Forms.CommonDialog> objets avec un Explorateur de propriétés personnalisées.

Modifications fournies par une instance de <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> appliqué à l’implémentation d’un VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> peut avoir l’une des deux portées :

- Global--pour toutes les nouvelles instances d’un composant donné

- Local--appartenant uniquement à l’instance du composant créé sur une aire de conception fournie par le VSPackage actuel.

Le `IsGlobal` propriété de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> instance appliqué à l’implémentation d’un VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> détermine cette étendue.

Appliquant l’attribut à une implémentation de <xref:Microsoft.VisualStudio.Shell.Package> avec la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> propriété de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> objet la valeur `true`, comme suit, modifie le navigateur pour tout l’environnement Visual Studio :

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Si l’indicateur global a la valeur `false`, la modification de métadonnées est locale au concepteur actuel pris en charge par le VSPackage actuel :

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> L’aire de conception prend uniquement en charge la création de composants, et par conséquent seuls les composants peuvent avoir des métadonnées locales. Dans l’exemple ci-dessus, nous étions tente de modifier une propriété, tel que le `Color` propriété d’un objet. Si `false` a été transmise pour l’indicateur global, `CustomBrowser` n’apparaîtrait jamais, car le concepteur crée en fait jamais une instance de `Color`. Définition de l’indicateur global `false` est utile pour les composants, tels que les contrôles, les minuteurs et les boîtes de dialogue.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Étendre la prise en charge au moment du design](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)