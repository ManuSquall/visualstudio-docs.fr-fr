---
title: 'Procédure pas à pas : ajout de fonctionnalités à un éditeur personnalisé | Microsoft Docs'
description: Découvrez comment ajouter d’autres fonctionnalités à un éditeur personnalisé après avoir créé l’éditeur à l’aide de cette procédure pas à pas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c08af63eaf68701f1a6703ac41fec20368d78931
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863199"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Procédure pas à pas : ajouter des fonctionnalités à un éditeur personnalisé
Après avoir créé un éditeur personnalisé, vous pouvez lui ajouter d’autres fonctionnalités.

## <a name="to-create-an-editor-for-a-vspackage"></a>Pour créer un éditeur pour un VSPackage

1. Créez un éditeur personnalisé à l’aide du modèle de projet de package Visual Studio.

     Pour plus d’informations, consultez [procédure pas à pas : création d’un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Décidez si vous souhaitez que votre éditeur prenne en charge une seule vue ou plusieurs vues.

     Un éditeur qui prend en charge la commande **nouvelle fenêtre** , ou en mode formulaire et mode Code, requiert des objets de données de document et des objets de vue de document distincts. Dans un éditeur qui ne prend en charge qu’une seule vue, l’objet de données de document et l’objet de vue de document peuvent être implémentés sur le même objet.

     Pour obtenir un exemple de plusieurs vues, consultez [prendre en charge plusieurs vues de documents](../extensibility/supporting-multiple-document-views.md).

3. Implémentez une fabrique d’éditeur en configurant l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface.

     Pour plus d’informations, consultez [fabriques d’éditeur](/previous-versions/visualstudio/visual-studio-2015/extensibility/editor-factories?preserve-view=true&view=vs-2015).

4. Décidez si vous souhaitez que votre éditeur utilise l’activation sur place ou l’incorporation simplifiée pour gérer la fenêtre de l’objet de vue de document.

     Une fenêtre d’éditeur d’incorporation simplifiée héberge une vue de document standard, tandis qu’une fenêtre d’éditeur d’activation sur place héberge un contrôle ActiveX ou tout autre objet actif comme vue de document. Pour plus d’informations, consultez [intégration simplifiée](../extensibility/simplified-embedding.md) et [activation sur place](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015).

5. Implémentez l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface pour gérer les commandes.

6. Assurer la persistance des documents et la réponse aux modifications de fichiers externes :

    1. Pour rendre le fichier persistant, implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> et <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> sur l’objet de données de document de votre éditeur.

    2. Pour répondre aux modifications de fichiers externes, implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> sur l’objet de données de document de votre éditeur.

        > [!NOTE]
        > Appelez `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> pour obtenir un pointeur vers `IVsFileChangeEx` .

7. Coordonner les événements de modification de document avec le contrôle de code source. Effectuez les étapes suivantes :

    1. Obtient un pointeur vers `IVsQueryEditQuerySave2` en appelant `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> .

    2. Lorsque le premier événement Edit se produit, appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> méthode.

         Cette méthode invite l’utilisateur à extraire le fichier s’il n’est pas déjà extrait. Veillez à gérer la condition « fichier non extrait » pour les erreurs de l’AVERT.

    3. De même, avant d’enregistrer le fichier, appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> méthode.

         Cette méthode invite l’utilisateur à enregistrer le fichier s’il n’a pas été enregistré ou s’il a été modifié depuis le dernier enregistrement.

8. Activez la fenêtre **Propriétés** pour afficher les propriétés du texte sélectionné dans l’éditeur. Effectuez les étapes suivantes :

    1. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> chaque fois que la sélection de texte est modifiée, en passant votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .

    2. Appelez `QueryService` sur le <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> service pour obtenir un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

9. Permet aux utilisateurs de glisser-déplacer des éléments entre l’éditeur et la **boîte à outils**, ou entre des éditeurs externes (tels que Microsoft Word) et la **boîte à outils**. Effectuez les étapes suivantes :

    1. Implémentez `IDropTarget` sur votre éditeur pour alerter l’IDE que votre éditeur est une cible de déplacement.

    2. Implémentez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interface sur la vue afin que votre éditeur puisse activer et désactiver des éléments dans la **boîte à outils**.

    3. Implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> et appeler `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> le service pour obtenir un pointeur vers les <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfaces et.

         Ces étapes permettent à votre VSPackage d’ajouter de nouveaux éléments à la **boîte à outils**.

10. Déterminez si vous souhaitez utiliser d’autres fonctionnalités facultatives pour votre éditeur.

    - Si vous souhaitez que votre éditeur prenne en charge les commandes de recherche et de remplacement, implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> .

    - Si vous souhaitez utiliser une fenêtre outil structure du document dans votre éditeur, implémentez `IVsDocOutlineProvider` .

    - Si vous souhaitez utiliser une barre d’État dans votre éditeur, implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> et appelez `QueryService` pour pour <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> obtenir un pointeur vers `IVsStatusBar` .

         Par exemple, un éditeur peut afficher des informations sur les lignes/colonnes, le mode de sélection (flux/zone) et le mode d’insertion (insertion/Refrappe).

    - Si vous souhaitez que votre éditeur prenne en charge la `Undo` commande, la méthode recommandée consiste à utiliser le modèle de gestionnaire d’annulation OLE. Vous pouvez également faire en sorte que l’éditeur gère `Undo` directement la commande.

11. Créer des informations de Registre, y compris les GUID pour le VSPackage, les menus, l’éditeur et d’autres fonctionnalités.

     Voici un exemple générique de code que vous placez dans votre script de fichier *. RGS* pour illustrer comment inscrire correctement un éditeur.

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

12. Implémentez la prise en charge de l’aide contextuelle.

     Cette étape vous permet de fournir une aide F1 et une prise en charge de la fenêtre d’aide dynamique pour les éléments de votre éditeur. Pour plus d’informations, consultez [Comment : fournir le contexte pour les éditeurs](/previous-versions/visualstudio/visual-studio-2015/extensibility/how-to-provide-context-for-editors?preserve-view=true&view=vs-2015).

13. Exposez un modèle objet Automation à partir de votre éditeur en implémentant l' `IDispatch` interface.

     Pour plus d'informations, consultez [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Programmation fiable

- L’instance de l’éditeur est créée lorsque l’IDE appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode. Si l’éditeur prend en charge plusieurs vues, `CreateEditorInstance` crée les données de document et les objets de vue de document. Si l’objet de données de document est déjà ouvert, une valeur non null `punkDocDataExisting` est passée à `IVsEditorFactory::CreateEditorInstance` . Votre implémentation de fabrique d’éditeur doit déterminer si un objet de données de document existant est compatible en interrogeant les interfaces appropriées sur celui-ci. Pour plus d’informations, consultez [prise en charge de plusieurs vues de documents](../extensibility/supporting-multiple-document-views.md).

- Si vous utilisez l’approche d’incorporation simplifiée, implémentez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface.

- Si vous décidez d’utiliser l’activation sur place, implémentez les interfaces suivantes :

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > L' `IOleInPlaceComponent` interface est utilisée pour éviter la fusion de menus OLE 2.

   Votre `IOleCommandTarget` implémentation gère les commandes telles que **couper**, **copier** et **coller**. Lors `IOleCommandTarget` de l’implémentation de, décidez si votre éditeur requiert son propre fichier *. vsct* pour définir sa propre structure de menu de commandes ou s’il peut implémenter des commandes standard définies par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . En règle générale, les éditeurs utilisent et étendent les menus de l’IDE et définissent leurs propres barres d’outils. Toutefois, il est souvent nécessaire pour un éditeur de définir ses propres commandes spécifiques en plus de l’utilisation du jeu de commandes standard de l’IDE. Votre éditeur doit déclarer les commandes standard qu’il utilise, puis définir les nouvelles commandes, les menus contextuels, les menus de niveau supérieur et les barres d’outils dans un fichier *. vsct* . Si vous créez un éditeur d’activation sur place, implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> et définissez les menus et les barres d’outils de l’éditeur dans un fichier *. vsct* au lieu d’utiliser la fusion de menus OLE 2.

- Pour empêcher la foule de commandes de menu dans l’interface utilisateur, vous devez utiliser les commandes existantes dans l’IDE avant d’inventer de nouvelles commandes. Les commandes partagées sont définies dans *SharedCmdDef. vsct* et *ShellCmdDef. vsct*. Ces fichiers sont installés par défaut dans le sous-répertoire VisualStudioIntegration\Common\Inc de votre [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] installation.

- `ISelectionContainer` peut exprimer à la fois des sélections uniques et multiples. Chaque objet sélectionné est implémenté en tant qu' `IDispatch` objet.

- L’IDE implémente `IOleUndoManager` en tant que service accessible à partir d’un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> ou en tant qu’objet pouvant être instancié par le biais de <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> . Votre éditeur implémente l' `IOleUndoUnit` interface pour chaque `Undo` action.

- Un éditeur personnalisé peut exposer les objets d’automatisation de deux manières :

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Voir aussi

- [Contribuer au modèle Automation](../extensibility/internals/contributing-to-the-automation-model.md)