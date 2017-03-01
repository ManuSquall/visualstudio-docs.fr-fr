---
title: En fournissant Annuler prise en charge pour les concepteurs | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 17
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
ms.openlocfilehash: 95e6873d0a3b254fa8f34144253a44c0a8cab60d
ms.lasthandoff: 02/22/2017

---
# <a name="supplying-undo-support-to-designers"></a>Fournissant la prise en charge de l’annulation pour les concepteurs
Concepteurs, tels que les éditeurs, avez généralement besoin de prendre en charge les opérations d’annulation afin que les utilisateurs peuvent annuler leurs modifications récentes lors de la modification d’un élément de code.  
  
 La plupart des concepteurs implémenté dans Visual Studio dispose du support d’annulation fournie automatiquement par l’environnement.  
  
 Implémentations concepteurs qui doivent prendre en charge la fonctionnalité d’annulation :  
  
-   Gérer l’annulation par l’implémentation de la classe de base abstraite<xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>  
  
-   Persistance d’approvisionnement et de CodeDOM prennent en charge en implémentant la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>et le <xref:System.ComponentModel.Design.IComponentChangeService>classes.</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 Pour plus d’informations sur l’écriture à l’aide des concepteurs [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], consultez [étendre la prise en charge au moment du Design](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit une infrastructure d’annulation par défaut par :  
  
-   Fournissant annuler des implémentations de gestion via le <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>et <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>classes.</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   En fournissant la prise en charge de CodeDOM à la valeur par défaut et de persistance <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>et <xref:System.ComponentModel.Design.IComponentChangeService>implémentations.</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
## <a name="obtaining-undo-support-automatically"></a>Obtention d’un Support de restauration automatiquement  
 Tout concepteur créé dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prend en charge la restauration automatique et complète if, le concepteur :  
  
-   Utilise un <xref:System.Windows.Forms.Control>basé sur la classe pour son interface utilisateur.</xref:System.Windows.Forms.Control>  
  
-   Utilise le système d’analyse et de génération de code basé sur CodeDOM standard pour la génération de code et de persistance.  
  
     Pour plus d’informations sur l’utilisation de la prise en charge de Visual Studio CodeDOM, consultez [Compilation et génération de Code Source dynamique](http://msdn.microsoft.com/Library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Quand utiliser la prise en charge de l’annulation de concepteur explicite  
 Concepteurs doivent fournir leur propre gestion de l’annulation s’ils utilisent une interface utilisateur graphique, appelée un adaptateur de vue, autre que celui fourni par <xref:System.Windows.Forms.Control>.</xref:System.Windows.Forms.Control>  
  
 Un exemple peut être création d’un produit avec une interface de conception graphique web plutôt qu’un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en fonction d’interface graphique.  
  
 Dans ce cas, vous devez inscrire cet adaptateur de vue avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à l’aide de <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>et fournir une gestion de l’annulation explicite.</xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>  
  
 Concepteurs ont besoin de fournir le CodeDOM et persistance prennent en charge s’ils n’utilisent pas le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modèle de génération de code fourni dans le <xref:System.CodeDom>espace de noms.</xref:System.CodeDom>  
  
## <a name="undo-support-features-of-the-designer"></a>Annuler les fonctionnalités de prise en charge du Concepteur  
 Le Kit de développement environnement fournit des implémentations par défaut des interfaces nécessaires pour fournir Annuler prise en charge qui peut être utilisé par les concepteurs ne pas à l’aide de <xref:System.Windows.Forms.Control>en fonction des classes pour leurs interfaces utilisateur ou le modèle de persistance et de CodeDOM standard.</xref:System.Windows.Forms.Control>  
  
 La <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>classe dérive de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine>classe à l’aide d’une implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>classe pour gérer les opérations d’annulation.</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> </xref:System.ComponentModel.Design.UndoEngine> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
 Visual Studio fournit les fonctionnalités suivantes pour annuler concepteur :  
  
-   Fonctionnalité d’annulation lié entre plusieurs concepteurs.  
  
-   Unités enfants au sein d’un concepteur peuvent interagir avec leurs parents par l’implémentation <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>et <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>le <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>  
  
 Le Kit de développement environnement fournit la prise en charge de CodeDOM et la persistance en fournissant :  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>comme des implémentations de la<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
 Un <xref:System.ComponentModel.Design.IComponentChangeService>fournie par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'' hôte de conception.</xref:System.ComponentModel.Design.IComponentChangeService>  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Avec les fonctionnalités de kit de développement logiciel d’environnement pour fournir la prise en charge de l’annulation  
 Pour obtenir la prise en charge de l’annulation, un objet qui implémente un concepteur doit :  
  
-   Instancier et d’initialiser une instance de la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>classe avec un nom <xref:System.IServiceProvider>implémentation.</xref:System.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Cela <xref:System.IServiceProvider>classe doit fournir les services suivants :</xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.</xref:System.ComponentModel.Design.IDesignerHost>  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         À l’aide des concepteurs [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sérialisation CodeDOM peut-être choisir d’utiliser <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>fourni avec les [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] en tant que sa mise en oeuvre du <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
         Dans ce cas, la <xref:System.IServiceProvider>classe fournie pour le <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>constructeur doit retourner cet objet en tant qu’implémentation de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>classe.</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> </xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService></xref:System.ComponentModel.Design.IComponentChangeService>  
  
         À l’aide de la valeur par défaut des concepteurs <xref:System.ComponentModel.Design.DesignSurface>fournie par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hôte de conception sont la garantie d’avoir une implémentation par défaut de la <xref:System.ComponentModel.Design.IComponentChangeService>classe</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.DesignSurface>  
  
 Concepteurs d’implémenter un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>mécanisme d’annulation en fonction suit automatiquement les modifications si :</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Les modifications de propriété sont apportées via le <xref:System.ComponentModel.TypeDescriptor>objet.</xref:System.ComponentModel.TypeDescriptor>  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>les événements sont générés manuellement lorsqu’une modification annulable est validée.</xref:System.ComponentModel.Design.IComponentChangeService>  
  
-   Modification dans le concepteur a été créée dans le contexte d’un <xref:System.ComponentModel.Design.DesignerTransaction>.</xref:System.ComponentModel.Design.DesignerTransaction>  
  
-   Le concepteur choisit de créer explicitement des unités d’annulation à l’aide de l’unité undo standard fournie par une implémentation de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit>la mise en œuvre de spécifique de Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>qui dérive <xref:System.ComponentModel.Design.UndoEngine.UndoUnit>et fournit également une implémentation de deux <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>et <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> </xref:System.ComponentModel.Design.UndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:System.ComponentModel.Design.UndoEngine.UndoUnit>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine></xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Étendre la prise en charge au moment du Design](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
