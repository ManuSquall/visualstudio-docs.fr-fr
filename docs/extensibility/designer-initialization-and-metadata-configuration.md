---
title: "L’initialisation du concepteur et la Configuration des métadonnées | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 61624d9926f4d984386f1a8b3fe8a575ce465331
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="designer-initialization-and-metadata-configuration"></a>L’initialisation du concepteur et la Configuration des métadonnées
Manipulation des attributs de métadonnées et le filtre associé à un concepteur ou un composant de concepteur fournit un mécanisme permettant aux applications de définir quels outils sont utilisés par un concepteur particulier pour gérer différents <xref:System.Type> objets (tels que les structures de données, classes, ou les entités graphiques), lorsque le concepteur est disponible, et comment l’IDE de Visual Studio est configuré pour prendre en charge le concepteur (pour une instance qui **boîte à outils** catégorie ou l’onglet est disponible).  
  
 Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit plusieurs mécanismes pour faciliter le contrôle de l’initialisation du composant concepteur du concepteur et la manipulation de ses métadonnées par un VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Initialisation des métadonnées et les informations de Configuration  
 Car elles sont chargées à la demande, VSPackages ont ne peut-être pas été chargés par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement avant l’instanciation d’un concepteur. Par conséquent, les VSPackages ne peut pas utiliser le mécanisme standard de configuration d’un concepteur ou un composant de concepteur sur la création, ce qui est de gérer un <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> événement. Au lieu de cela, un VSPackage implémente une instance de la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> de l’interface et s’inscrit lui-même pour fournir des personnalisations, appelées extensions surface de conception.  
  
### <a name="customizing-initialization"></a>Personnalisation de l’initialisation  
 Personnalisation d’un concepteur, un composant ou une aire du concepteur, implique :  
  
1.  Modifier les métadonnées du concepteur et qui permet de modifier comment une certaine <xref:System.Type> est accessible ou converti.  
  
     Cette opération est généralement effectuée par le biais du <xref:System.Drawing.Design.UITypeEditor> ou <xref:System.ComponentModel.TypeConverter> mécanismes.  
  
     Par exemple, lorsque <xref:System.Windows.Forms>-en fonction des concepteurs sont initialisées, le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement modifie le <xref:System.Drawing.Design.UITypeEditor> pour <xref:System.Web.UI.WebControls.Image> objets utilisés avec le concepteur pour le Gestionnaire de ressources permet d’obtenir des images bitmap plutôt que le système de fichiers.  
  
2.  Intégration avec l’environnement, par exemple, en vous abonnant aux événements ou obtenir des informations de configuration de projet. Vous pouvez obtenir des informations de configuration de projet et vous abonner aux événements en obtenant la <xref:System.ComponentModel.Design.ITypeResolutionService> interface.  
  
3.  Modification de l’environnement utilisateur en activant approprié **boîte à outils** catégories ou en limitant la mise en application du concepteur en appliquant une instance de la <xref:System.ComponentModel.ToolboxItemFilterAttribute> classe vers le concepteur.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Initialisation du concepteur par un VSPackage  
 Un VSPackage doit gérer l’initialisation du concepteur par :  
  
1.  Création d’un objet qui implémente le <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe.  
  
    > [!NOTE]
    >  Le <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe ne doit jamais être implémentée sur le même objet que la <xref:Microsoft.VisualStudio.Shell.Package> classe.  
  
2.  Inscrire la classe implémentant <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> en tant que la prise en charge pour les extensions de concepteur le VSPackage en appliquant des instances de <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> et <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> à la classe d’implémentation du VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> .  
  
 Chaque fois qu’un concepteur ou un composant concepteur est créé, le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement :  
  
1.  Accède à chaque fournisseur d’extensions aire de conception de modèle enregistré.  
  
2.  Instancie et initialise une instance de chaque fournisseur d’extension de surface de conception <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objet  
  
3.  Appelle chaque fournisseur d’extension de surface de conception <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> méthode ou <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> (méthode) (le cas échéant).  
  
 Lorsque vous implémentez le <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> de l’objet en tant que membre d’un VSPackage, il est important de comprendre que :  
  
1.  Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement ne fournit pas de n’importe quel contrôle sur les métadonnées ou d’autres paramètres de configuration événements `DesignSurfaceExtension` fournisseur modifie. Il est possible pour plusieurs `DesignSurfaceExtension` fournisseurs de modification de la même fonctionnalité Concepteur manières en conflit, avec la dernière modification est définitive. Elle est indéterminée quelle modification est appliquée en dernier lieu.  
  
2.  Il est possible de restreindre explicitement l’implémentation de la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objet aux concepteurs spécifiques, en appliquant des instances de <xref:System.ComponentModel.ToolboxItemFilterAttribute> à cette implémentation. Pour plus d’informations sur **boîte à outils** filtrage d’élément, consultez la <xref:System.ComponentModel.ToolboxItemFilterAttribute> et <xref:System.ComponentModel.ToolboxItemFilterType>.  
  
## <a name="additional-metadata-provisioning"></a>Configuration des métadonnées supplémentaires  
 Un VSPackage peut modifier la configuration d’un concepteur ou un composant autre que de concepteur au moment du design.  
  
 La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe peut être utilisée par programme, ou être appliqués à un VSPackage qui fournit un concepteur.  
  
 Une instance de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe est utilisée pour modifier les métadonnées des composants créés sur une aire de conception. Par exemple, un peut remplacer un Explorateur de propriétés par défaut utilisé par <xref:System.Windows.Forms.CommonDialog> objets, avec un navigateur de propriétés personnalisées.  
  
 Modifications fournies par une instance de <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> appliqué à l’implémentation d’un VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> peut avoir une des deux étendues :  
  
-   Global--pour toutes les nouvelles instances d’un composant donné  
  
-   Local--appartenant uniquement à l’instance du composant créé sur une aire de conception fournie par le VSPackage actuel.  
  
 Le `IsGlobal` propriété de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> instance appliquée à l’implémentation d’un VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> détermine l’étendue.  
  
 Appliquant l’attribut à une implémentation de <xref:Microsoft.VisualStudio.Shell.Package> avec la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> propriété de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> objet `true`, comme ci-dessous, modifie le navigateur de l’ensemble du [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement :  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Si la valeur de l’indicateur global `false`, la modification de métadonnées est locale pour le concepteur actuel pris en charge par le VSPackage actuel :  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  À l’heure actuelle, l’aire de conception prend uniquement en charge la création de composants et par conséquent seuls les composants peuvent avoir des métadonnées locales. Dans l’exemple ci-dessus, nous avons tente de modifier une propriété, tel que le `Color` propriété d’un objet. Si `false` a été transmise pour l’indicateur global, `CustomBrowser` apparaîtrait jamais, car le concepteur crée en réalité jamais une instance de `Color`. Définition de l’indicateur global `false` est utile pour les composants, tels que les contrôles, les minuteries et les boîtes de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Extension de la prise en charge au moment du design](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)