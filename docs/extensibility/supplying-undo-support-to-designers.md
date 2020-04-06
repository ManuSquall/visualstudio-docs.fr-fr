---
title: Fournir un soutien à l’annulation des designers (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0580f974c362a71c3e400946f2ad34f565ad1232
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699675"
---
# <a name="supply-undo-support-to-designers"></a>Fournir un soutien annuler aux concepteurs

Les concepteurs, comme les éditeurs, doivent généralement prendre en charge les opérations de défaire afin que les utilisateurs puissent inverser leurs modifications récentes lors de la modification d’un élément de code.

La plupart des concepteurs mis en œuvre dans Visual Studio ont "annuler" le support automatiquement fourni par l’environnement.

Implémentations de concepteur qui doivent fournir le soutien pour la fonction annuler:

- Fournir une gestion annuler en mettant en œuvre la classe de base abstraite<xref:System.ComponentModel.Design.UndoEngine>

- Persistance de l’offre et <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> soutien <xref:System.ComponentModel.Design.IComponentChangeService> CodeDOM par la mise en œuvre de la et des classes.

Pour plus d’informations sur les concepteurs d’écriture en utilisant .NET Framework, voir [Extend Design-Time Support](/previous-versions/37899azc(v=vs.140)).

Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit une infrastructure de défaire par défaut en :

- Fournir des implémentations de gestion non faits par le biais de la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> et <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> des classes.

- Fournir la persistance et le <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> soutien <xref:System.ComponentModel.Design.IComponentChangeService> CodeDOM par le biais de la valeur par défaut et les implémentations.

## <a name="obtain-undo-support-automatically"></a>Obtenir automatiquement un soutien annuler

Tout designer créé dans Visual Studio a un support automatique et complet annuler si, le concepteur:

- Utilise une <xref:System.Windows.Forms.Control> classe basée pour son interface utilisateur.

- Utilise le système standard de génération de code basé sur CodeDOM et d’analyse pour la génération de code et la persistance.

   Pour plus d’informations sur le travail avec le support Visual Studio CodeDOM, voir [Dynamic Source Code Generation and Compilation](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Quand utiliser le support d’annulation de concepteur explicite
 Les concepteurs doivent fournir leur propre gestion annuler s’ils utilisent une interface utilisateur graphique, <xref:System.Windows.Forms.Control>appelée un adaptateur de vue, autre que celui fourni par .

 Un exemple de ceci pourrait être la création d’un produit avec une interface graphique basée sur le Web plutôt qu’une interface graphique basée sur le cadre .NET.

 Dans de tels cas, il faudrait enregistrer cet <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>adaptateur de vue avec Visual Studio à l’aide , et fournir une gestion explicite annuler.

 Les concepteurs doivent fournir CodeDOM et support de persistance s’ils <xref:System.CodeDom> n’utilisent pas le modèle de génération de code Visual Studio fourni dans l’espace de nom.

## <a name="undo-support-features-of-the-designer"></a>Annuler les caractéristiques de support du designer
 L’Environnement SDK fournit des implémentations par défaut des interfaces <xref:System.Windows.Forms.Control> nécessaires pour fournir un support annuler qui peut être utilisé par les concepteurs ne pas utiliser des classes basées pour leurs interfaces utilisateur ou le codeDOM standard et le modèle de persistance.

 La <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe dérive de la <xref:System.ComponentModel.Design.UndoEngine> classe cadre .NET en utilisant une mise en œuvre de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe pour gérer les opérations annuler.

 Visual Studio fournit la fonctionnalité suivante à designer annuler:

- Fonctionnalité d’annulation liée à plusieurs designers.

- Les unités d’enfants au sein d’un concepteur peuvent interagir avec leurs parents en <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> mettant en œuvre et <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> sur <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.

Le SDK environnement fournit codeDOM et soutien à la persistance en fournissant :

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>en tant que mise en œuvre de la<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- A <xref:System.ComponentModel.Design.IComponentChangeService> fourni par l’hôte de design Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Utilisez les fonctionnalités SDK de l’environnement pour fournir un support annuler

Pour obtenir un soutien annuler, un objet mettant en œuvre <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> un concepteur <xref:System.IServiceProvider> doit instantanéiser et initialiser une instance de la classe avec une mise en œuvre valide. Cette <xref:System.IServiceProvider> classe doit fournir les services suivants :

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Les concepteurs utilisant Visual Studio CodeDOM sérialisation peuvent choisir d’utiliser <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> fourni avec la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] mise en œuvre de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.

   Dans ce cas, la <xref:System.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe fournie au constructeur doit retourner <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> cet objet comme une mise en œuvre de la classe.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Les concepteurs <xref:System.ComponentModel.Design.DesignSurface> utilisant la valeur par défaut fournie par l’hôte de conception Visual Studio sont garantis d’avoir une implémentation par défaut de la <xref:System.ComponentModel.Design.IComponentChangeService> classe.

Les concepteurs <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> qui mettent en œuvre un mécanisme de défaire basé suit automatiquement les changements si :

- Des modifications de <xref:System.ComponentModel.TypeDescriptor> propriété sont apportées à travers l’objet.

- <xref:System.ComponentModel.Design.IComponentChangeService>les événements sont générés manuellement lorsqu’un changement indossible est commis.

- Modification sur le concepteur a été <xref:System.ComponentModel.Design.DesignerTransaction>créé dans le cadre d’un .

- Le concepteur choisit de créer explicitement des unités annuler en utilisant <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> soit l’unité de <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>défaire standard <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> fournie par une <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> mise <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>en œuvre ou la mise en œuvre visual studio spécifique , qui dérive de et fournit également une mise en œuvre des deux et .

## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Étendre le support Design-Time](/previous-versions/37899azc(v=vs.140))
