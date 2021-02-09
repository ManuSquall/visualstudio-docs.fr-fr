---
title: Fourniture de la prise en charge de l’annulation aux concepteurs | Microsoft Docs
description: Découvrez comment fournir une prise en charge de l’annulation dans les concepteurs, soit automatiquement, soit à l’aide des fonctionnalités du kit de développement logiciel (SDK) Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9e8b7ea0dc29e4f8df9113963a95c363998c758d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850466"
---
# <a name="supply-undo-support-to-designers"></a>Fournir une prise en charge de l’annulation aux concepteurs

Les concepteurs, comme les éditeurs, doivent généralement prendre en charge les opérations d’annulation afin que les utilisateurs puissent annuler leurs modifications récentes lors de la modification d’un élément de code.

La plupart des concepteurs implémentés dans Visual Studio ont une prise en charge de « annuler » automatiquement fournie par l’environnement.

Implémentations de concepteur qui doivent assurer la prise en charge de la fonctionnalité d’annulation :

- Fournir la gestion des annulations en implémentant la classe de base abstraite <xref:System.ComponentModel.Design.UndoEngine>

- Fournir la prise en charge de la persistance et de CodeDOM en implémentant les <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  <xref:System.ComponentModel.Design.IComponentChangeService> classes et.

Pour plus d’informations sur l’écriture de concepteurs à l’aide de .NET Framework, consultez [étendre la prise en charge des Design-Time](/previous-versions/37899azc(v=vs.140)).

Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit une infrastructure d’annulation par défaut en procédant comme suit :

- Fournir des implémentations de gestion des annulations via les <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classes et.

- Fourniture de la persistance et de la prise en charge de CodeDOM par le biais des <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> implémentations et par défaut <xref:System.ComponentModel.Design.IComponentChangeService> .

## <a name="obtain-undo-support-automatically"></a>Obtenir la prise en charge de l’annulation automatiquement

Tout concepteur créé dans Visual Studio dispose d’une prise en charge de l’annulation automatique et complète si, le concepteur :

- Utilise une classe de <xref:System.Windows.Forms.Control> base pour son interface utilisateur.

- Utilise le système de génération et d’analyse de code basé sur CodeDOM standard pour la génération et la persistance de code.

   Pour plus d’informations sur l’utilisation de la prise en charge de Visual Studio CodeDOM, consultez [génération et compilation de code source dynamique](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Quand utiliser la prise en charge de l’annulation explicite du concepteur
 Les concepteurs doivent fournir leur propre gestion des annulations s’ils utilisent une interface utilisateur graphique, appelée adaptateur de vue, autre que celle fournie par <xref:System.Windows.Forms.Control> .

 Par exemple, vous pouvez créer un produit avec une interface de conception graphique basée sur le Web plutôt qu’une interface graphique de type .NET Framework.

 Dans ce cas, vous devez inscrire cet adaptateur d’affichage auprès de Visual Studio à l’aide de <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> , et fournir une gestion d’annulation explicite.

 Les concepteurs doivent fournir la prise en charge de CodeDOM et de la persistance s’ils n’utilisent pas le modèle de génération de code Visual Studio fourni dans l' <xref:System.CodeDom> espace de noms.

## <a name="undo-support-features-of-the-designer"></a>Annuler les fonctionnalités de prise en charge du concepteur
 Le kit de développement logiciel (SDK) Environment fournit des implémentations par défaut des interfaces nécessaires pour fournir une prise en charge de l’annulation qui peut être utilisée par les concepteurs qui n’utilisent pas <xref:System.Windows.Forms.Control> de classes basées pour leurs interfaces utilisateur ou le modèle de persistance et CodeDom standard.

 La <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe dérive de la <xref:System.ComponentModel.Design.UndoEngine> classe .NET Framework à l’aide d’une implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe pour gérer les opérations d’annulation.

 Visual Studio fournit la fonctionnalité suivante pour annuler le concepteur :

- Fonctionnalité d’annulation liée entre plusieurs concepteurs.

- Les unités enfants au sein d’un concepteur peuvent interagir avec leurs parents en implémentant <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> sur <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .

Le kit de développement logiciel (SDK) Environment fournit la prise en charge de CodeDOM et de la persistance en fournissant :

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> en tant qu’implémentation de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- <xref:System.ComponentModel.Design.IComponentChangeService>Fourni par l’hôte de conception Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Utiliser les fonctionnalités du kit de développement logiciel (SDK) pour fournir une prise en charge d’annulation

Pour obtenir la prise en charge de l’annulation, un objet qui implémente un concepteur doit instancier et initialiser une instance de la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe avec une <xref:System.IServiceProvider> implémentation valide. Cette <xref:System.IServiceProvider> classe doit fournir les services suivants :

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Les concepteurs qui utilisent la sérialisation CodeDOM de Visual Studio peuvent choisir d’utiliser <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> fourni avec [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] comme implémentation de <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .

   Dans ce cas, la <xref:System.IServiceProvider> classe fournie au <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> constructeur doit retourner cet objet en tant qu’implémentation de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classe.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Les concepteurs utilisant la valeur par défaut <xref:System.ComponentModel.Design.DesignSurface> fournie par l’hôte de conception Visual Studio sont assurés d’avoir une implémentation par défaut de la <xref:System.ComponentModel.Design.IComponentChangeService> classe.

Les concepteurs qui implémentent un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mécanisme d’annulation basé automatiquement effectue le suivi des modifications dans les cas suivants :

- Les modifications de propriété sont effectuées via l' <xref:System.ComponentModel.TypeDescriptor> objet.

- <xref:System.ComponentModel.Design.IComponentChangeService> les événements sont générés manuellement lorsqu’une modification pouvant être annulée est validée.

- La modification apportée au concepteur a été créée dans le contexte d’un <xref:System.ComponentModel.Design.DesignerTransaction> .

- Le concepteur choisit explicitement de créer des unités d’annulation à l’aide de l’unité d’annulation standard fournie par une implémentation de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> ou de l’implémentation spécifique à Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> , qui dérive de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> et fournit également une implémentation de <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> et de <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .

## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Étendre la prise en charge de Design-Time](/previous-versions/37899azc(v=vs.140))
