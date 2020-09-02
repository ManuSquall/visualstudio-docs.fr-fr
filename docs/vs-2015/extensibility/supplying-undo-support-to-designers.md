---
title: Fourniture de la prise en charge de l’annulation aux concepteurs | Microsoft Docs
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
ms.openlocfilehash: 6136caaec0cb8f0d79e3fb7b96245fc3fd070710
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675338"
---
# <a name="supplying-undo-support-to-designers"></a>Fourniture de la prise en charge de l’annulation pour les concepteurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les concepteurs, comme les éditeurs, doivent généralement prendre en charge les opérations d’annulation afin que les utilisateurs puissent annuler leurs modifications récentes lors de la modification d’un élément de code.  
  
 La plupart des concepteurs implémentés dans Visual Studio ont une prise en charge de l’annulation automatique fournie par l’environnement.  
  
 Implémentations de concepteur qui doivent assurer la prise en charge de la fonctionnalité d’annulation :  
  
- Fournir la gestion des annulations en implémentant la classe de base abstraite <xref:System.ComponentModel.Design.UndoEngine>  
  
- Fournir la prise en charge de la persistance et de CodeDOM en implémentant les <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> classes et.  
  
  Pour plus d’informations sur l’écriture de concepteurs à l’aide de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , consultez extension de la [prise en charge au moment du design](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  Le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] fournit une infrastructure d’annulation par défaut en procédant comme suit :  
  
- Fournir des implémentations de gestion des annulations via les <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classes et.  
  
- Fourniture de la persistance et de la prise en charge de CodeDOM par le biais des <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> implémentations et par défaut <xref:System.ComponentModel.Design.IComponentChangeService> .  
  
## <a name="obtaining-undo-support-automatically"></a>Obtention automatique de la prise en charge de l’annulation  
 Tout concepteur créé dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a une prise en charge de l’annulation automatique et complète si, le concepteur :  
  
- Utilise une classe de <xref:System.Windows.Forms.Control> base pour son interface utilisateur.  
  
- Utilise le système de génération et d’analyse de code basé sur CodeDOM standard pour la génération et la persistance de code.  
  
     Pour plus d’informations sur l’utilisation de la prise en charge de Visual Studio CodeDOM, consultez [génération et compilation de code source dynamique](https://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Quand utiliser la prise en charge de l’annulation explicite du concepteur  
 Les concepteurs doivent fournir leur propre gestion des annulations s’ils utilisent une interface utilisateur graphique, appelée adaptateur de vue, autre que celle fournie par <xref:System.Windows.Forms.Control> .  
  
 Par exemple, vous pouvez créer un produit avec une interface de conception graphique basée sur le Web plutôt qu’une [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] interface graphique de base.  
  
 Dans ce cas, vous devez inscrire cet adaptateur d’affichage avec [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] à l’aide de <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> , et fournir une gestion des annulations explicite.  
  
 Les concepteurs doivent fournir CodeDOM et la prise en charge de la persistance s’ils n’utilisent pas le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modèle de génération de code fourni dans l' <xref:System.CodeDom> espace de noms.  
  
## <a name="undo-support-features-of-the-designer"></a>Annuler les fonctionnalités de prise en charge du concepteur  
 Le kit de développement logiciel (SDK) Environment fournit des implémentations par défaut des interfaces nécessaires pour fournir une prise en charge de l’annulation qui peut être utilisée par les concepteurs qui n’utilisent pas <xref:System.Windows.Forms.Control> de classes basées pour leurs interfaces utilisateur ou le modèle de persistance et CodeDom standard.  
  
 La <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe dérive de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> classe à l’aide d’une implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe pour gérer les opérations d’annulation.  
  
 Visual Studio fournit la fonctionnalité suivante pour annuler le concepteur :  
  
- Fonctionnalité d’annulation liée entre plusieurs concepteurs.  
  
- Les unités enfants au sein d’un concepteur peuvent interagir avec leurs parents en implémentant <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> sur <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .  
  
  Le kit de développement logiciel (SDK) Environment fournit la prise en charge de CodeDOM et de la persistance en fournissant :  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> en tant qu’implémentations du <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  <xref:System.ComponentModel.Design.IComponentChangeService>Fourni par l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hôte de conception «».  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Utilisation des fonctionnalités du kit de développement logiciel pour fournir une prise en charge de l’annulation  
 Pour obtenir la prise en charge de l’annulation, un objet qui implémente un concepteur doit :  
  
- Instanciez et initialisez une instance de la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe avec une <xref:System.IServiceProvider> implémentation valide.  
  
- Cette <xref:System.IServiceProvider> classe doit fournir les services suivants :  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       Les concepteurs qui utilisent [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la sérialisation CodeDom peuvent choisir d’utiliser <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> fourni avec [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] comme implémentation de <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .  
  
       Dans ce cas, la <xref:System.IServiceProvider> classe fournie au <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> constructeur doit retourner cet objet en tant qu’implémentation de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classe.  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       Les concepteurs utilisant la valeur par défaut <xref:System.ComponentModel.Design.DesignSurface> fournie par l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hôte de conception sont assurés d’avoir une implémentation par défaut de la <xref:System.ComponentModel.Design.IComponentChangeService> classe.  
  
  Les concepteurs qui implémentent un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mécanisme d’annulation basé automatiquement effectue le suivi des modifications dans les cas suivants :  
  
- Les modifications de propriété sont effectuées via l' <xref:System.ComponentModel.TypeDescriptor> objet.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> les événements sont générés manuellement lorsqu’une modification pouvant être annulée est validée.  
  
- La modification apportée au concepteur a été créée dans le contexte d’un <xref:System.ComponentModel.Design.DesignerTransaction> .  
  
- Le concepteur choisit explicitement de créer des unités d’annulation à l’aide de l’unité d’annulation standard fournie par une implémentation de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> ou de l’implémentation spécifique à Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> , qui dérive de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> et fournit également une implémentation de <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> et de <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Extension de la prise en charge au moment du design](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
