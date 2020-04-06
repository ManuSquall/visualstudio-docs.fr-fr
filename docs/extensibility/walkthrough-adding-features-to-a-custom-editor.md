---
title: 'Procédure pas à pas : Ajout de fonctionnalités à un éditeur personnalisé ( Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b145dd4d82887122009553afd883abb6cade849e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697787"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Procédure pas à pas : Ajoutez des fonctionnalités à un éditeur personnalisé
Après avoir créé un éditeur personnalisé, vous pouvez y ajouter plus de fonctionnalités.

## <a name="to-create-an-editor-for-a-vspackage"></a>Créer un éditeur pour un VSPackage

1. Créez un éditeur personnalisé en utilisant le modèle de projet Visual Studio Package.

     Pour plus d’informations, voir [Procédure pas à pas: Créer un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Décidez si vous voulez que votre éditeur supporte une vue unique ou plusieurs vues.

     Un éditeur qui prend en charge la commande **New Window,** ou qui a une vue de formulaire et un code, nécessite des objets de données de documents distincts et des objets de vue de documents. Dans un éditeur qui ne prend en charge qu’une seule vue, l’objet de données de document et l’objet de vue de document peuvent être implémenté sur le même objet.

     Pour un exemple de vues multiples, voir [Prendre en charge plusieurs vues de documents](../extensibility/supporting-multiple-document-views.md).

3. Implémentez une usine <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> d’éditeurs en installant l’interface.

     Pour plus d’informations, voir [Editor factories](../extensibility/editor-factories.md).

4. Décidez si vous souhaitez que votre éditeur utilise l’activation sur place ou l’intégration simplifiée pour gérer la fenêtre d’objet de vue de document.

     Une fenêtre d’éditeur d’intégration simplifiée héberge une vue de document standard, tandis qu’une fenêtre d’éditeur d’activation sur place héberge un contrôle ActiveX ou un autre objet actif comme vue de document. Pour plus d’informations, voir [l’intégration simplifiée](../extensibility/simplified-embedding.md) et [l’activation sur place](/visualstudio/misc/in-place-activation?view=vs-2015).

5. Implémentez l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pour gérer les commandes.

6. Fournir la persistance des documents et la réponse aux modifications externes des fichiers :

    1. Pour persévérer le fichier, implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> et <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> sur l’objet de données de document de votre éditeur.

    2. Pour répondre aux modifications <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> de fichiers externes, implémentez et sur l’objet de données de votre éditeur.

        > [!NOTE]
        > Faites `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> appel pour obtenir `IVsFileChangeEx`un pointeur à .

7. Coordonner les événements d’édition de documents avec le contrôle du code source. Procédez comme suit :

    1. Obtenez un `IVsQueryEditQuerySave2` pointeur `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>à en faisant appel à .

    2. Lorsque le premier événement de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> modification se produit, appelez la méthode.

         Cette méthode invite l’utilisateur à vérifier le fichier si elle n’est pas déjà vérifiée. Assurez-vous de gérer une condition de « fichier non vérifié » pour éviter les erreurs.

    3. De même, avant d’enregistrer le fichier, appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> méthode.

         Cette méthode incite l’utilisateur à enregistrer le fichier s’il n’a pas été enregistré ou s’il a changé depuis le dernier enregistrement.

8. Activez la fenêtre **Properties** pour afficher les propriétés pour le texte sélectionné dans l’éditeur. Procédez comme suit :

    1. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> chaque fois que la sélection <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>de texte change, en passant dans votre mise en œuvre de .

    2. Faites `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> appel au service <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>pour obtenir un pointeur à .

9. Permettre aux utilisateurs de faire glisser et de laisser tomber les éléments entre l’éditeur et la **boîte à outils**, ou entre les éditeurs externes (comme Microsoft Word) et la boîte à **outils**. Procédez comme suit :

    1. Implémentez `IDropTarget` votre éditeur pour alerter l’IDE que votre éditeur est une cible de drop.

    2. Implémentez l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> sur la vue afin que votre éditeur puisse activer et désactiver les éléments dans la **boîte à outils**.

    3. Implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> et faire appel `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> au <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> service pour obtenir un pointeur sur les interfaces et les interfaces.

         Ces étapes permettent à votre VSPackage d’ajouter de nouveaux éléments à la boîte à **outils**.

10. Décidez si vous voulez d’autres fonctionnalités facultatives pour votre éditeur.

    - Si vous voulez que votre éditeur supporte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>trouver et remplacer les commandes, implémentez .

    - Si vous souhaitez utiliser une fenêtre d’outil `IVsDocOutlineProvider`de contour de document dans votre éditeur, implémentez .

    - Si vous souhaitez utiliser une barre de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> statut `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> dans votre éditeur, implémentez et appelez pour obtenir un pointeur à `IVsStatusBar`.

         Par exemple, un éditeur peut afficher des informations de ligne/colonne, mode de sélection (flux/boîte) et mode d’insertion (insérer / sur-attaque).

    - Si vous voulez que `Undo` votre éditeur supporte la commande, la méthode recommandée est d’utiliser le modèle OLE annuler gestionnaire. Comme alternative, vous pouvez faire `Undo` gérer directement la commande par l’éditeur.

11. Créez des informations sur le registre, y compris les GUIDs pour le VSPackage, les menus, l’éditeur et d’autres fonctionnalités.

     Ce qui suit est un exemple générique de code que vous mettez dans votre script de fichier *.rgs* pour démontrer comment enregistrer correctement un éditeur.

    ```csharp
    NoRemove Editors
    {
          ForceRemove {...guidEditor...} = s 'RTF Editor'
          {
             val Package = s '{...guidVsPackage...}'
             ForceRemove Extensions
             {
                val rtf = d 50
             }
          }
    }
    NoRemove Menus
    {
          val {...guidVsPackage...} = s ',203,11'
    }
    ```

12. Mettre en œuvre un support d’aide sensible au contexte.

     Cette étape vous permet de fournir un support de fenêtre D1 Help and Dynamic Help pour les articles de votre éditeur. Pour plus d’informations, voir [Comment : Fournir un contexte pour les éditeurs](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015).

13. Exposez un modèle d’objet d’automatisation de votre éditeur en implémentant l’interface. `IDispatch`

     Pour plus d'informations, consultez [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Programmation fiable

- L’instance de l’éditeur est <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> créée lorsque l’IDE appelle la méthode. Si l’éditeur prend `CreateEditorInstance` en charge plusieurs vues, crée à la fois les données de document et les objets de vue du document. Si l’objet de données de document `punkDocDataExisting` est déjà `IVsEditorFactory::CreateEditorInstance`ouvert, une valeur non nulle est transmise à . Votre implémentation d’usine d’éditeur doit déterminer si un objet de données de document existant est compatible en interrogeant les interfaces appropriées sur elle. Pour plus d’informations, voir [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).

- Si vous utilisez l’approche d’intégration simplifiée, implémentez l’interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>

- Si vous décidez d’utiliser l’activation sur place, implémentez les interfaces suivantes :

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > L’interface `IOleInPlaceComponent` est utilisée pour éviter la fusion du menu OLE 2.

   Votre `IOleCommandTarget` implémentation gère des commandes telles que **Cut**, **Copy**, et **Paste**. Lors de `IOleCommandTarget`la mise en œuvre , décider si votre éditeur a besoin de son [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]propre fichier *.vsct* pour définir sa propre structure de menu de commande ou si elle peut implémenter des commandes standard définies par . En règle générale, les éditeurs utilisent et étendent les menus de l’IDE et définissent leurs propres barres d’outils. Cependant, il est souvent nécessaire pour un éditeur de définir ses propres commandes spécifiques en plus d’utiliser l’ensemble de commande standard de l’IDE. Votre éditeur doit déclarer les commandes standard qu’il utilise, puis définir les nouvelles commandes, les menus contextuels, les menus de haut niveau et les barres d’outils dans un fichier *.vsct.* Si vous créez un éditeur d’activation sur place, implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> et définissez les menus et les barres d’outils pour l’éditeur dans un fichier *.vsct* au lieu d’utiliser la fusion du menu OLE 2.

- Pour éviter l’encombrement des commandes de menu dans l’interface utilisateur, vous devez utiliser les commandes existantes dans l’IDE avant d’inventer de nouvelles commandes. Les commandes partagées sont définies dans *SharedCmdDef.vsct* et *ShellCmdDef.vsct*. Ces fichiers sont installés par défaut dans la sous-direction de votre [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] installation VisualStudioIntegration-Common-Inc.

- `ISelectionContainer`peut exprimer des sélections simples et multiples. Chaque objet sélectionné est `IDispatch` implémenté comme objet.

- L’IDE `IOleUndoManager` s’agit d’un service accessible à partir d’un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> ou d’un objet qui peut être instantané à travers <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Votre éditeur implémente l’interface `IOleUndoUnit` pour chaque `Undo` action.

- Il y a deux endroits où un éditeur personnalisé peut exposer des objets d’automatisation :

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Voir aussi

- [Contribuer au modèle d’automatisation](../extensibility/internals/contributing-to-the-automation-model.md)
