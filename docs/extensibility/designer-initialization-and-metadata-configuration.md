---
title: "L’initialisation du concepteur et la Configuration des métadonnées | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c0865b62cc2683a8197b5eb6cbc0599d6c063534
ms.lasthandoff: 02/22/2017

---
# <a name="designer-initialization-and-metadata-configuration"></a>L’initialisation du concepteur et la Configuration des métadonnées
Manipulation des attributs de métadonnées et le filtre associé à un concepteur ou un composant de concepteur fournit un mécanisme pour les applications définir quels outils sont utilisés par un concepteur particulier pour gérer différents <xref:System.Type>objets (tels que des structures de données, les classes ou les entités graphiques), lorsque le concepteur n’est disponible, et comment l’IDE de Visual Studio est configuré pour prendre en charge le concepteur (pour l’instance qui **boîte à outils** catégorie ou l’onglet est disponible).</xref:System.Type>  
  
 Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit plusieurs mécanismes pour faciliter le contrôle de l’initialisation du composant concepteur du concepteur et la manipulation de ses métadonnées par un VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Initialisation des métadonnées et les informations de Configuration  
 Car ils sont chargés à la demande, VSPackages ont ne peut-être pas été chargés par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement avant l’instanciation d’un concepteur. Par conséquent, les packages VS ne peut pas utiliser le mécanisme standard pour la configuration d’un concepteur ou un composant de concepteur lors de la création, qui consiste à gérer un <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>événements.</xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> Au lieu de cela, un VSPackage implémente une instance de la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>de l’interface et s’inscrit pour fournir des personnalisations, appelées extensions surface de conception.</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
### <a name="customizing-initialization"></a>Personnalisation de l’initialisation  
 Personnalisation d’un concepteur, un composant ou une aire de conception, implique :  
  
1.  Modifier les métadonnées du concepteur et qui permet de modifier comment une certaine <xref:System.Type>est accessible ou converti.</xref:System.Type>  
  
     Cela est généralement effectuée via la <xref:System.Drawing.Design.UITypeEditor>ou <xref:System.ComponentModel.TypeConverter>mécanismes.</xref:System.ComponentModel.TypeConverter> </xref:System.Drawing.Design.UITypeEditor>  
  
     Par exemple, lorsque <xref:System.Windows.Forms>-en fonction des concepteurs sont initialisés, le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement modifie le <xref:System.Drawing.Design.UITypeEditor>de <xref:System.Web.UI.WebControls.Image>objets utilisés avec le concepteur pour le Gestionnaire de ressources permet d’obtenir des images bitmap plutôt que le système de fichiers.</xref:System.Web.UI.WebControls.Image> </xref:System.Drawing.Design.UITypeEditor> </xref:System.Windows.Forms>  
  
2.  Intégration avec l’environnement, par exemple, en vous abonnant aux événements ou obtenir des informations de configuration de projet. Vous pouvez obtenir des informations de configuration de projet et s’abonner aux événements en obtenant le <xref:System.ComponentModel.Design.ITypeResolutionService>interface.</xref:System.ComponentModel.Design.ITypeResolutionService>  
  
3.  Modification de l’environnement utilisateur en activant approprié **boîte à outils** catégories ou en restreignant l’applicabilité du concepteur en appliquant une instance de la <xref:System.ComponentModel.ToolboxItemFilterAttribute>classe vers le concepteur.</xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
### <a name="designer-initialization-by-a-vspackage"></a>Initialisation du concepteur à un VSPackage  
 Un VSPackage doit gérer l’initialisation du concepteur par :  
  
1.  Création d’un objet qui implémente la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>classe.</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>classe ne doit jamais être implémentée sur le même objet que la <xref:Microsoft.VisualStudio.Shell.Package>classe.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
2.  Enregistrez la classe d’implémentation <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>en tant que la prise en charge pour les extensions de concepteur du VSPackage en appliquant des instances de <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>et <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>à la classe en fournissant l’implémentation du VSPackage de <xref:Microsoft.VisualStudio.Shell.Package>.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
 Lorsqu’un concepteur ou un composant de concepteur est créée, le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement :  
  
1.  Accède à chaque fournisseur d’extension de surface modèle enregistré.  
  
2.  Instancie et initialise une instance de, <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>objet de chaque fournisseur extension de surface de conception</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
3.  Appelle chaque fournisseur extension de surface de conception <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>méthode ou <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>(méthode) (le cas échéant).</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>  
  
 Lorsque vous implémentez le <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>de l’objet en tant que membre d’un VSPackage, il est important de comprendre que :</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
1.  Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement ne fournit pas de contrôler les métadonnées ou d’autres paramètres de configuration a notamment `DesignSurfaceExtension` modifie du fournisseur. Il est possible pour plusieurs `DesignSurfaceExtension` fournisseurs de modifier les mêmes fonctionnalités de Concepteur de manières en conflit, avec la dernière modification est définitive. Il est indéterminé quelle modification est appliquée en dernier lieu.  
  
2.  Il est possible de limiter explicitement une implémentation de la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>concepteurs spécifiques, en appliquant des instances d’objet <xref:System.ComponentModel.ToolboxItemFilterAttribute>à cette implémentation.</xref:System.ComponentModel.ToolboxItemFilterAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Pour plus d’informations sur **boîte à outils** élément de filtrage, consultez <xref:System.ComponentModel.ToolboxItemFilterAttribute>et <xref:System.ComponentModel.ToolboxItemFilterType>.</xref:System.ComponentModel.ToolboxItemFilterType> </xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
## <a name="additional-metadata-provisioning"></a>Configuration des métadonnées supplémentaires  
 Un VSPackage peut modifier la configuration d’un concepteur ou un composant de concepteur différent au moment du design.  
  
 La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>classe peut être utilisée par programme, ou être appliqués à un VSPackage fournissant un concepteur.</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 Une instance de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>classe est utilisée pour modifier les métadonnées des composants créés sur une aire de conception.</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Par exemple, un peut remplacer un Explorateur de propriétés par défaut utilisé par <xref:System.Windows.Forms.CommonDialog>objets, avec un navigateur de propriétés personnalisées.</xref:System.Windows.Forms.CommonDialog>  
  
 Modifications fournies par une instance de <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>appliquée à l’implémentation d’un VSPackage de <xref:Microsoft.VisualStudio.Shell.Package>peut avoir l’une des deux portées :</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
-   Global--pour toutes les nouvelles instances d’un composant donné  
  
-   Local--se rapportant uniquement à l’instance du composant créé sur une aire de conception fournie par le VSPackage actuel.  
  
 Le `IsGlobal` propriété de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>instance appliqué à l’implémentation d’un VSPackage de <xref:Microsoft.VisualStudio.Shell.Package>détermine l’étendue.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 Appliquant l’attribut à une implémentation de <xref:Microsoft.VisualStudio.Shell.Package>avec la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>propriété de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>objet `true`, comme expliqué ci-dessous, modifie le navigateur de l’ensemble du [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement :</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> </xref:Microsoft.VisualStudio.Shell.Package>  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Si l’indicateur global a été défini sur `false`, puis la modification de métadonnées est locale pour le concepteur actuel est pris en charge par le VSPackage actuel :  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  À l’heure actuelle, l’aire de conception prend uniquement en charge la création de composants et par conséquent, seuls les composants peuvent avoir des métadonnées locale. Dans l’exemple ci-dessus, nous avons tente de modifier une propriété, tel que le `Color` propriété d’un objet. Si `false` a été transmise pour l’indicateur global, `CustomBrowser` n’apparaîtrait jamais, car le concepteur crée en fait jamais une instance de `Color`. Définition de l’indicateur global `false` est utile pour les composants, tels que les contrôles, les minuteries et les boîtes de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType></xref:System.ComponentModel.ToolboxItemFilterType>   
 [Étendre la prise en charge au moment du Design](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
