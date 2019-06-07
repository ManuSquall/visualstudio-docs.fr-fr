---
title: En fournissant annuler la prise en charge pour les concepteurs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e243ccfc92c5e17dd25e6d77dede439daac08761
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747729"
---
# <a name="supply-undo-support-to-designers"></a>Annulation prise en charge pour les concepteurs

En général, les concepteurs, tels que des éditeurs, ont besoin prendre en charge les opérations d’annulation afin que vous pouvez procéder à leurs modifications récentes lorsque vous modifiez un élément de code.

La plupart des concepteurs implémenté dans Visual Studio ont prises en charge automatiquement par l’environnement « annulation ».

Implémentations concepteurs dont avez besoin pour prendre en charge la fonctionnalité d’annulation :

- Fournir la gestion d’annulation en implémentant la classe de base abstraite <xref:System.ComponentModel.Design.UndoEngine>

- Persistance fournissez et CodeDOM prend en charge en implémentant la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> et <xref:System.ComponentModel.Design.IComponentChangeService> classes.

Pour plus d’informations sur l’écriture de concepteurs à l’aide de .NET Framework, consultez [étendre la prise en charge au moment du Design](/previous-versions/37899azc(v=vs.140)).

Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit une infrastructure d’annulation par défaut par :

- Fournissant annuler des implémentations de gestion via la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> et <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classes.

- En fournissant la persistance et la prise en charge de CodeDOM via la valeur par défaut <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> et <xref:System.ComponentModel.Design.IComponentChangeService> implémentations.

## <a name="obtain-undo-support-automatically"></a>Obtenir automatiquement de prise en charge de l’annulation

N’importe quel concepteur créé dans Visual Studio a prise en charge de l’annulation automatique et complète if, le concepteur :

- Utilise un <xref:System.Windows.Forms.Control> basé sur la classe pour son interface utilisateur.

- Utilise la génération de code basé sur CodeDOM standard et de système d’analyse pour la persistance et la génération de code.

   Pour plus d’informations sur l’utilisation de la prise en charge de Visual Studio CodeDOM, consultez [Compilation et génération de Code Source dynamique](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Quand utiliser la prise en charge de l’annulation de concepteur explicite
 Concepteurs doivent fournir leur propre gestion de l’annulation s’ils utilisent une interface graphique utilisateur, appelée un adaptateur de vue, autre que celui fourni par <xref:System.Windows.Forms.Control>.

 Un exemple de ceci peut créer un produit avec une interface basée sur le web de conception graphique plutôt qu’une interface graphique basée sur .NET Framework.

 Dans ce cas, un doit inscrire cet adaptateur de vue avec Visual Studio en utilisant <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>et fournir une gestion d’annulation explicite.

 Les concepteurs ont besoin fournir le CodeDOM persistance prise en charge et si elles n’utilisent pas le modèle de génération de code Visual Studio fourni dans le <xref:System.CodeDom> espace de noms.

## <a name="undo-support-features-of-the-designer"></a>Annuler les fonctionnalités de prise en charge du Concepteur
 Le SDK de l’environnement fournit des implémentations par défaut des interfaces nécessaires pour fournir annuler la prise en charge qui peut être utilisé par les concepteurs ne pas à l’aide de <xref:System.Windows.Forms.Control> en fonction des classes pour leurs interfaces utilisateur ou le modèle de persistance et de CodeDOM standard.

 Le <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe dérive de .NET Framework <xref:System.ComponentModel.Design.UndoEngine> classe à l’aide d’une implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe pour gérer les opérations d’annulation.

 Visual Studio fournit la fonctionnalité suivante pour annuler concepteur :

- Fonctionnalité d’annulation lié entre plusieurs concepteurs.

- Unités enfants au sein d’un concepteur peuvent interagir avec leurs parents en implémentant <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> sur <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.

Le SDK de l’environnement fournit la prise en charge de CodeDOM et persistance en fournissant :

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> en tant qu’implémentation de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Un <xref:System.ComponentModel.Design.IComponentChangeService> fourni par l’hôte de conception de Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Utiliser les fonctionnalités de kit de développement logiciel d’environnement pour fournir la prise en charge de l’annulation

Pour obtenir la prise en charge de l’annulation, un objet qui implémente un concepteur doit instancier et initialiser une instance de la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe avec valide <xref:System.IServiceProvider> implémentation. Cela <xref:System.IServiceProvider> classe doit fournir les services suivants :

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   À l’aide de la sérialisation de Visual Studio CodeDOM de concepteurs peuvent choisir d’utiliser <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> fourni avec le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] comme son implémentation de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.

   Dans ce cas, le <xref:System.IServiceProvider> classe fournie à la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> constructeur doit retourner cet objet en tant qu’implémentation de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classe.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   À l’aide de la valeur par défaut des concepteurs <xref:System.ComponentModel.Design.DesignSurface> fournie par la conception de Visual Studio hôte forment une implémentation par défaut de la <xref:System.ComponentModel.Design.IComponentChangeService> classe.

Concepteurs d’implémenter un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mécanisme d’annulation en suit automatiquement les modifications apportées si :

- Les modifications de propriété sont apportées via la <xref:System.ComponentModel.TypeDescriptor> objet.

- <xref:System.ComponentModel.Design.IComponentChangeService> événements sont générés manuellement lorsqu’une modification annulable est validée.

- Aucune modification sur le concepteur a été créée dans le contexte d’un <xref:System.ComponentModel.Design.DesignerTransaction>.

- Le concepteur choisit de créer explicitement des unités d’annulation à l’aide l’unité d’annulation standard fournie par une implémentation de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> ou de l’implémentation spécifique de Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, qui dérive à son <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> et fournit également un implémentation des deux <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.

## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Étendre la prise en charge au moment du Design](/previous-versions/37899azc(v=vs.140))