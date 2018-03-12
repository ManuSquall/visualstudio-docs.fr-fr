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
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 98243c15f5f69a9aecba589b966d56a68201ab2a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="supplying-undo-support-to-designers"></a>En fournissant la prise en charge de l’annulation pour les concepteurs
En général, les concepteurs, tels que les éditeurs, doivent prendre en charge les opérations d’annulation afin que les utilisateurs peuvent annuler leurs modifications récentes lors de la modification d’un élément de code.  
  
 La plupart des concepteurs implémentés dans Visual Studio ont prise en charge de l’annulation fournie automatiquement par l’environnement.  
  
 Implémentations concepteur que vous avez besoin pour prendre en charge la fonctionnalité d’annulation :  
  
-   Fournir la gestion de l’annulation en implémentant la classe de base abstraite<xref:System.ComponentModel.Design.UndoEngine>  
  
-   Persistance fournissez et CodeDOM prend en charge en implémentant la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> et <xref:System.ComponentModel.Design.IComponentChangeService> classes.  
  
 Pour plus d’informations sur l’écriture à l’aide des concepteurs [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], consultez [étendre la prise en charge au moment du Design](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit une infrastructure d’annulation par défaut par :  
  
-   Fournissant annuler les implémentations de gestion via le <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> et <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classes.  
  
-   En fournissant la prise en charge de CodeDOM via la valeur par défaut et de persistance <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> et <xref:System.ComponentModel.Design.IComponentChangeService> implémentations.  
  
## <a name="obtaining-undo-support-automatically"></a>Obtenir automatiquement de prise en charge de l’annulation  
 Tout concepteur créé dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prend en charge la restauration automatique et complètes if, le concepteur :  
  
-   Utilise un <xref:System.Windows.Forms.Control> basé sur la classe pour son interface utilisateur.  
  
-   Utilise la génération de code basé sur le CodeDOM de standard et le système d’analyse pour la persistance et la génération de code.  
  
     Pour plus d’informations sur l’utilisation de la prise en charge de Visual Studio CodeDOM, consultez [la génération de Code Source dynamique et la Compilation](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Quand utiliser la prise en charge de l’annulation de concepteur explicite  
 Concepteurs doivent fournir leur propre gestion de l’annulation s’ils utilisent une interface utilisateur graphique, visée une carte de vue, différente de celle fournie par <xref:System.Windows.Forms.Control>.  
  
 Un exemple peut être création d’un produit avec une interface de conception graphique web plutôt qu’un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en fonction d’interface graphique.  
  
 Dans ce cas, vous devez inscrire cet adaptateur de vue avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à l’aide de <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>et fournir une gestion de l’annulation explicite.  
  
 Des concepteurs doivent prennent en charge par CodeDOM et persistance s’ils n’utilisent pas le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modèle de génération de code fourni dans le <xref:System.CodeDom> espace de noms.  
  
## <a name="undo-support-features-of-the-designer"></a>Annuler les fonctionnalités de prise en charge du Concepteur  
 Le SDK de l’environnement fournit des implémentations par défaut des interfaces nécessaires pour fournir des Annuler prise en charge qui peut être utilisé par les concepteurs ne pas à l’aide de <xref:System.Windows.Forms.Control> en fonction des classes pour leurs interfaces utilisateur ou le modèle CodeDOM et de persistance standard.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe dérive de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine> classe à l’aide d’une implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe pour gérer les opérations d’annulation.  
  
 Visual Studio fournit la fonctionnalité suivante pour annuler concepteur :  
  
-   Fonctionnalité d’annulation liée entre plusieurs concepteurs.  
  
-   Unités enfants dans un concepteur peuvent interagir avec leurs parents en implémentant <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> sur <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
 Le SDK de l’environnement fournit la prise en charge de CodeDOM et persistance en fournissant :  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>comme des implémentations de la<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 A <xref:System.ComponentModel.Design.IComponentChangeService> fournie par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'' hôte de conception.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>À l’aide des fonctionnalités du SDK d’environnement pour fournir la prise en charge de l’annulation  
 Pour obtenir la prise en charge de l’annulation, un objet qui implémente un concepteur doit :  
  
-   Instancier et initialiser une instance de la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe avec valide <xref:System.IServiceProvider> implémentation.  
  
-   Cela <xref:System.IServiceProvider> classe doit fournir les services suivants :  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         À l’aide des concepteurs [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sérialisation CodeDOM peut-être choisir d’utiliser <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> fourni avec le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] en tant que son implémentation de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
         Dans ce cas, le <xref:System.IServiceProvider> classe fournie pour le <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> constructeur doit retourner cet objet en tant qu’implémentation de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classe.  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
         À l’aide de la valeur par défaut des concepteurs <xref:System.ComponentModel.Design.DesignSurface> fournie par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hôte de conception sont la garantie d’avoir une implémentation par défaut de la <xref:System.ComponentModel.Design.IComponentChangeService> classe.  
  
 Concepteurs qui implémentent un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mécanisme d’annulation en fonction suit automatiquement les modifications si :  
  
-   Modifications apportées aux propriétés sont effectuées via le <xref:System.ComponentModel.TypeDescriptor> objet.  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>les événements sont générés manuellement lorsqu’une modification irréalisable est validée.  
  
-   La modification sur le concepteur a été créée dans le contexte d’un <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
-   Le concepteur choisit de créer explicitement des unités d’annulation à l’aide d’une unité undo standard fournie par une implémentation de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> ou l’implémentation spécifique de Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, lequel dérive <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> et fournit également un implémentation des deux <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Extension de la prise en charge au moment du design](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)