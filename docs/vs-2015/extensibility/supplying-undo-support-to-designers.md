---
title: En fournissant annuler la prise en charge pour les concepteurs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e0ee2059c6a2bc1c5456cc949cf05b921c874cd3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938563"
---
# <a name="supplying-undo-support-to-designers"></a>Fourniture de la prise en charge de l’annulation pour les concepteurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En général, les concepteurs, tels que des éditeurs, ont besoin prendre en charge les opérations d’annulation afin que vous pouvez procéder à leurs modifications récentes lorsque vous modifiez un élément de code.  
  
 La plupart des concepteurs implémenté dans Visual Studio dispose du support d’annulation fourni automatiquement par l’environnement.  
  
 Implémentations concepteurs dont avez besoin pour prendre en charge la fonctionnalité d’annulation :  
  
- Fournir la gestion d’annulation en implémentant la classe de base abstraite <xref:System.ComponentModel.Design.UndoEngine>  
  
- Persistance fournissez et CodeDOM prend en charge en implémentant la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> et <xref:System.ComponentModel.Design.IComponentChangeService> classes.  
  
  Pour plus d’informations sur l’écriture à l’aide de concepteurs [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], consultez [Extending Design-Time Support](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  Le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] fournit une infrastructure d’annulation par défaut par :  
  
- Fournissant annuler des implémentations de gestion via la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> et <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classes.  
  
- En fournissant la persistance et la prise en charge de CodeDOM via la valeur par défaut <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> et <xref:System.ComponentModel.Design.IComponentChangeService> implémentations.  
  
## <a name="obtaining-undo-support-automatically"></a>Obtention de possibilité d’annuler automatiquement  
 N’importe quel concepteur créé dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prend en charge de l’annulation automatique et complète if, le concepteur :  
  
-   Utilise un <xref:System.Windows.Forms.Control> basé sur la classe pour son interface utilisateur.  
  
-   Utilise la génération de code basé sur CodeDOM standard et de système d’analyse pour la persistance et la génération de code.  
  
     Pour plus d’informations sur l’utilisation avec prise en charge de Visual Studio CodeDOM, consultez [Compilation et génération de Code Source dynamique](http://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Quand utiliser la prise en charge de l’annulation de concepteur explicite  
 Concepteurs doivent fournir leur propre gestion de l’annulation s’ils utilisent une interface graphique utilisateur, appelée un adaptateur de vue, autre que celui fourni par <xref:System.Windows.Forms.Control>.  
  
 Un exemple de ce peut être création d’un produit avec une interface de conception graphique web au lieu d’un [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] en fonction d’interface graphique.  
  
 Dans ce cas, un doit inscrire cet adaptateur de vue avec [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] à l’aide de <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>et fournir une gestion d’annulation explicite.  
  
 Les concepteurs ont besoin fournir le CodeDOM persistance prise en charge et si elles n’utilisent pas le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modèle de génération de code fourni dans le <xref:System.CodeDom> espace de noms.  
  
## <a name="undo-support-features-of-the-designer"></a>Annuler les fonctionnalités de prise en charge du Concepteur  
 Le SDK de l’environnement fournit des implémentations par défaut des interfaces nécessaires pour fournir annuler la prise en charge qui peut être utilisé par les concepteurs ne pas à l’aide de <xref:System.Windows.Forms.Control> en fonction des classes pour leurs interfaces utilisateur ou le modèle de persistance et de CodeDOM standard.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe dérive de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> classe à l’aide d’une implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe pour gérer les opérations d’annulation.  
  
 Visual Studio fournit la fonctionnalité suivante pour annuler concepteur :  
  
- Fonctionnalité d’annulation lié entre plusieurs concepteurs.  
  
- Unités enfants au sein d’un concepteur peuvent interagir avec leurs parents en implémentant <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> sur <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
  Le SDK de l’environnement fournit la prise en charge de CodeDOM et persistance en fournissant :  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> comme des implémentations de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  Un <xref:System.ComponentModel.Design.IComponentChangeService> fournie par le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]'' hôte de conception.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>À l’aide des fonctionnalités du SDK d’environnement pour fournir la prise en charge de l’annulation  
 Pour obtenir la prise en charge de l’annulation, un objet qui implémente un concepteur doit :  
  
- Instancier et initialiser une instance de la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe avec valide <xref:System.IServiceProvider> implémentation.  
  
- Cela <xref:System.IServiceProvider> classe doit fournir les services suivants :  
  
  -   <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       À l’aide de concepteurs [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sérialisation CodeDOM peut choisir d’utiliser <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> fourni avec le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] comme son implémentation de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
       Dans ce cas, le <xref:System.IServiceProvider> classe fournie à la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> constructeur doit retourner cet objet en tant qu’implémentation de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classe.  
  
  -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       À l’aide de la valeur par défaut des concepteurs <xref:System.ComponentModel.Design.DesignSurface> fournie par le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hôte de conception sont la garantie d’avoir une implémentation par défaut de la <xref:System.ComponentModel.Design.IComponentChangeService> classe.  
  
  Concepteurs d’implémenter un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mécanisme d’annulation en suit automatiquement les modifications apportées si :  
  
- Les modifications de propriété sont apportées via la <xref:System.ComponentModel.TypeDescriptor> objet.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> événements sont générés manuellement lorsqu’une modification annulable est validée.  
  
- Aucune modification sur le concepteur a été créée dans le contexte d’un <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
- Le concepteur choisit de créer explicitement des unités d’annulation à l’aide l’unité d’annulation standard fournie par une implémentation de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> ou de l’implémentation spécifique de Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, qui dérive à son <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> et fournit également un implémentation des deux <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Extension de la prise en charge au moment du design](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
