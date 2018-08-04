---
title: 'Procédure pas à pas : Ajout de fonctionnalités à un éditeur personnalisé | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d93861fc6238949d8666072b0bf5a5cc7efdb87b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498939"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Procédure pas à pas : Ajout de fonctionnalités à un éditeur personnalisé
Après avoir créé un éditeur personnalisé, vous pouvez ajouter davantage de fonctionnalités à ce dernier.  
  
## <a name="to-create-an-editor-for-a-vspackage"></a>Pour créer un éditeur pour un VSPackage  
  
1.  Créer un éditeur personnalisé en utilisant le modèle de projet de Package Visual Studio.  
  
     Pour plus d’informations, consultez [procédure pas à pas : créer un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Décidez si vous souhaitez que votre éditeur pour prendre en charge un seul ou plusieurs vues.  
  
     Un éditeur qui prend en charge la **nouvelle fenêtre** commande, ou a le mode formulaire et en mode code, nécessite des objets de données de document distinct et les objets de vue de document. Dans un éditeur qui prend en charge qu’une seule vue, l’objet de données de document et l’objet de vue de document peuvent être implémentés sur le même objet.  
  
     Pour obtenir un exemple de plusieurs vues, consultez [prendre en charge plusieurs vues de document](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implémenter une fabrique d’éditeur en configurant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface.  
  
     Pour plus d’informations, consultez [fabriques d’éditeur](../extensibility/editor-factories.md).  
  
4.  Décider si vous souhaitez que votre éditeur à utiliser l’activation sur place ou incorporation pour gérer la fenêtre des objets document vue simplifiée.  
  
     Une fenêtre d’éditeur incorporation simplifiée héberge une vue de document standard, pendant une fenêtre d’éditeur d’activation sur place héberge un contrôle ActiveX ou un autre objet active en tant que document vue. Pour plus d’informations, consultez [simplifié incorporation](../extensibility/simplified-embedding.md) et [In situ d’activation](../extensibility/in-place-activation.md).  
  
5.  Implémentez le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface pour gérer les commandes.  
  
6.  Fournir la persistance de document et de réponse aux modifications de fichier externe :  
  
    1.  Pour conserver le fichier, vous devez implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> et <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> sur l’objet de données de document de votre éditeur.  
  
    2.  Pour répondre aux modifications de fichier externe, implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> sur l’objet de données de document de votre éditeur.  
  
        > [!NOTE]
        >  Appelez `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> pour obtenir un pointeur vers `IVsFileChangeEx`.  
  
7.  Coordonner les événements de modification de document avec contrôle de code source. Procédez comme suit :  
  
    1.  Obtenir un pointeur vers `IVsQueryEditQuerySave2` en appelant `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Lorsque le premier événement de modification se produit, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (méthode).  
  
         Cette méthode invite l’utilisateur à extraire le fichier si elle n’est pas déjà extrait. Veillez à gérer une condition « fichier non extrait » pour éviter des erreurs.  
  
    3.  De même, avant d’enregistrer le fichier, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> (méthode).  
  
         Cette méthode invite l’utilisateur à enregistrer le fichier s’il n’a pas été enregistré ou si elle a changé depuis le dernier enregistrement.  
  
8.  Activer la **propriétés** fenêtre pour afficher les propriétés pour le texte sélectionné dans l’éditeur. Procédez comme suit :  
  
    1.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> chaque sélection de texte temps change, en passant dans votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Appelez `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> service pour obtenir un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Permettre aux utilisateurs de faire glisser des éléments entre l’éditeur et le **boîte à outils**, ou entre des éditeurs externes (tels que Microsoft Word) et le **boîte à outils**. Procédez comme suit :  
  
    1.  Implémentez `IDropTarget` sur votre éditeur pour alerter l’IDE que votre éditeur est une cible de dépôt.  
  
    2.  Implémentez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interface sur la vue afin de votre éditeur peut activer et désactiver des éléments dans le **boîte à outils**.  
  
    3.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> et appelez `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> service pour obtenir un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfaces.  
  
         Ces étapes permettent à votre VSPackage à ajouter de nouveaux éléments à la **boîte à outils**.  
  
10. Si vous décidez d’autres fonctionnalités facultatives pour votre éditeur.  
  
    -   Si vous souhaitez que votre éditeur pour prendre en charge les rechercher et remplacer des commandes, implémenter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Si vous souhaitez utiliser une fenêtre outil structure du document dans votre éditeur, implémenter `IVsDocOutlineProvider`.  
  
    -   Si vous souhaitez utiliser une barre d’état dans votre éditeur, implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> et appelez `QueryService` pour <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> pour obtenir un pointeur vers `IVsStatusBar`.  
  
         Par exemple, un éditeur peut afficher la ligne / informations sur les colonnes, le mode de sélection (diffuser en continu / zone) et le mode d’insertion (insert / /overstrike).  
  
    -   Si vous souhaitez que votre éditeur pour prendre en charge la `Undo` commande, la méthode recommandée consiste à utiliser le modèle de gestionnaire d’annulation OLE. Comme alternative, vous pouvez avoir le handle de l’éditeur le `Undo` commande directement.  
  
11. Créer un registre d’informations, y compris les GUID pour le VSPackage, les menus, l’éditeur et autres fonctionnalités.  
  
     Voici un exemple générique de code que vous devez placer dans votre *.rgs* script pour montrer comment inscrire correctement un éditeur de fichiers.  
  
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
  
12. Implémenter la prise en charge d’aide contextuelle.  
  
     Cette étape vous permet de fournir l’aide (F1) et la fenêtre Aide dynamique prennent en charge pour les éléments dans votre éditeur. Pour plus d’informations, consultez [Comment : fournir un contexte pour les éditeurs](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Exposer un modèle d’objet Automation à partir de votre éditeur en implémentant le `IDispatch` interface.  
  
     Pour plus d’informations, consultez [qui contribuent au modèle Automation](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Programmation fiable  
  
-   L’instance d’éditeur est créé lors de l’IDE appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (méthode). Si l’éditeur prend en charge plusieurs vues, `CreateEditorInstance` crée les données de document et les objets de vue de document. Si l’objet de données de document est déjà ouvrir, une valeur non null `punkDocDataExisting` valeur est passée à `IVsEditorFactory::CreateEditorInstance`. Votre implémentation de fabrique d’éditeur doit déterminer si un objet de données de document existant est compatible en recherchant des interfaces appropriées sur celui-ci. Pour plus d’informations, consultez [prenant en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md).  
  
-   Si vous utilisez l’approche d’incorporation simplifiée, implémentez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface.  
  
-   Si vous décidez d’utiliser l’activation sur place, implémenter les interfaces suivantes :  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  Le `IOleInPlaceComponent` interface est utilisée pour éviter la fusion de menus OLE 2.  
  
     Votre `IOleCommandTarget` implémentation gère les commandes telles que **couper**, **copie**, et **coller**. Lors de l’implémentation `IOleCommandTarget`, décidez si votre éditeur requiert son propre *.vsct* fichier pour définir sa propre structure de menu de commande ou si elle peut implémenter des commandes standards définies par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En règle générale, les éditeurs utilisent et d’étendent les menus de l’IDE et définissent leurs propres barres d’outils. Toutefois, il est souvent nécessaire pour un éditeur définir leurs propres commandes spécifiques en plus à l’aide du jeu de commandes standard de l’IDE. Votre éditeur doit déclarer les commandes standards, il utilise et ensuite définir n’importe quel nouvelles commandes, les menus contextuels, les menus de niveau supérieur et les barres d’outils dans un *.vsct* fichier. Si vous créez une activation sur place de l’éditeur, implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> et définir les menus et les barres d’outils de l’éditeur dans un *.vsct* fichier au lieu d’utiliser la fusion de menus OLE 2.  
  
-   Pour éviter de charger dans l’interface utilisateur de commande de menu, vous devez utiliser les commandes existantes dans l’IDE avant d’inventer de nouvelles commandes. Commandes partagées sont définies dans *SharedCmdDef.vsct* et *ShellCmdDef.vsct*. Ces fichiers sont installés par défaut dans le sous-répertoire VisualStudioIntegration\Common\Inc de votre [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] installation.  
  
-   `ISelectionContainer` pouvez exprimer des sélections uniques et multiples. Chaque objet sélectionné est implémenté comme un `IDispatch` objet.  
  
-   L’IDE implémente `IOleUndoManager` en tant que service accessible à partir d’un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> ou en tant qu’objet qui peut être instancié par <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Votre éditeur implémente le `IOleUndoUnit` interface pour chaque `Undo` action.  
  
-   Il existe deux emplacements un éditeur personnalisé peut exposer des objets automation :  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>Voir aussi  
 [Contribuer au modèle automation](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Comment : fournir un contexte pour les éditeurs](../extensibility/how-to-provide-context-for-editors.md)