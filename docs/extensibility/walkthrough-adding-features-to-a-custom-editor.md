---
title: "Proc&#233;dure pas &#224; pas : Ajout de fonctionnalit&#233;s &#224; un &#233;diteur personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), personnalisés - ajouter des fonctionnalités"
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 38
---
# Proc&#233;dure pas &#224; pas : Ajout de fonctionnalit&#233;s &#224; un &#233;diteur personnalis&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Après avoir créé un éditeur personnalisé, vous pouvez ajouter plus de fonctionnalités à celui\-ci.  
  
### Pour créer un éditeur pour un VSPackage  
  
1.  Créer un éditeur personnalisé à l'aide du modèle de projet de Package Visual Studio.  
  
     Pour plus d'informations, consultez [Procédure pas à pas : Création d'un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Décider si vous souhaitez que votre éditeur pour prendre en charge un seul ou plusieurs vues.  
  
     Un éditeur qui prend en charge les **nouvelle fenêtre** de commande, ou a mode formulaire et en mode code, requiert des objets de données de document distinct et les objets de vue de document. Dans un éditeur qui prend en charge une seule vue, l'objet de données de document et l'objet de vue de document peuvent être implémentées sur le même objet.  
  
     Pour obtenir un exemple de plusieurs vues, consultez [Prend en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implémenter une fabrique d'éditeur en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface.  
  
     Pour plus d'informations, consultez [Fabriques d'éditeur](../extensibility/editor-factories.md).  
  
4.  Décider si vous souhaitez que votre éditeur pour utiliser l'activation sur place ou simplifié l'incorporation pour gérer la fenêtre vue de l'objet document.  
  
     Une fenêtre d'éditeur incorporation simplifié héberge un mode d'affichage standard, pendant une fenêtre de l'éditeur d'activation sur place héberge un contrôle ActiveX ou un autre objet comme sa vue de document actif. Pour plus d’informations, consultez [Simplifié l'incorporation](../extensibility/simplified-embedding.md) et [activation sur place](../misc/in-place-activation.md).  
  
5.  Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> permettant de gérer les commandes.  
  
6.  Fournissent la persistance de document et réponse aux modifications apportées au fichier externe en procédant comme suit :  
  
    1.  Pour conserver le fichier, vous devez implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> et <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> sur l'objet de données de l'éditeur votre document.  
  
    2.  Pour répondre aux modifications apportées au fichier externe, implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> sur l'objet de données de l'éditeur votre document.  
  
        > [!NOTE]
        >  Appeler `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> pour obtenir un pointeur vers `IVsFileChangeEx`.  
  
7.  Coordonner les événements de modification de document avec contrôle de code source. Pour ce faire :  
  
    1.  Obtenir un pointeur vers `IVsQueryEditQuerySave2` en appelant `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Lorsque le premier événement de modification se produit, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> \(méthode\).  
  
         Cette invite l'utilisateur à consulter le fichier s'il n'a pas déjà été extrait. Veillez à gérer une condition « fichier non extrait » à éviter des erreurs  
  
    3.  De même, avant d'enregistrer le fichier, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> \(méthode\).  
  
         Cette méthode invite l'utilisateur à enregistrer le fichier s'il n'a pas été enregistré ou s'il a été modifié depuis le dernier enregistrement.  
  
8.  Activer la **propriétés** fenêtre pour afficher les propriétés pour le texte sélectionné dans l'éditeur. Pour ce faire :  
  
    1.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> chaque sélection de texte heure change, en passant dans votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Appeler `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> service pour obtenir un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Permettre aux utilisateurs de faire glisser des éléments entre l'éditeur et le **boîte à outils**, ou entre des éditeurs externes \(tels que Microsoft Word\) et le **boîte à outils**. Pour ce faire :  
  
    1.  Implémentez `IDropTarget` sur votre éditeur afin d'alerter l'IDE que votre éditeur est une cible de déplacement.  
  
    2.  Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interface sur l'affichage pour votre éditeur peut activer et désactiver des éléments dans le **boîte à outils**.  
  
    3.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> et appelez `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> service pour obtenir un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfaces.  
  
         Cela permet à votre package VS ajouter de nouveaux éléments à la **boîte à outils**.  
  
10. Si vous décidez d'autres fonctionnalités facultatives de votre éditeur.  
  
    -   Si vous souhaitez que votre éditeur pour prendre en charge rechercher et remplacer des commandes, implémenter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Si vous souhaitez utiliser une fenêtre outil structure du document dans votre éditeur, implémenter `IVsDocOutlineProvider`.  
  
    -   Si vous souhaitez utiliser une barre d'état dans votre éditeur, implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> et appelez `QueryService` pour <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> pour obtenir un pointeur vers `IVsStatusBar`.  
  
         Par exemple, un éditeur peut afficher la ligne \/ informations de colonne, le mode de sélection \(flux \/ zone\) et le mode d'insertion \(insert \/ \/overstrike\).  
  
    -   Si vous souhaitez que votre éditeur pour prendre en charge le `Undo` de commande, la méthode recommandée consiste à utiliser le modèle de gestionnaire d'annulation OLE. Comme alternative, vous pouvez avoir le handle de l'Éditeur du `Undo` commande directement.  
  
11. Créez plus d'informations, y compris les GUID pour le VSPackage, les menus, l'éditeur et d'autres fonctionnalités de Registre.  
  
     Voici un exemple de code que vous devez placer dans votre script de fichier .rgs pour montrer comment enregistrer correctement un éditeur générique.  
  
    ```  
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
  
12. Implémenter l'aide contextuelle.  
  
     Cela vous permet à la touche F1 et aide dynamique la prise en charge pour les éléments dans votre éditeur. Pour plus d'informations, consultez [Comment : fournir un contexte pour les éditeurs](../Topic/How%20to:%20Provide%20Context%20for%20Editors.md).  
  
13. Exposer un modèle d'objet Automation à partir de votre éditeur en implémentant le `IDispatch` interface.  
  
     Pour plus d'informations, consultez [Qui contribuent au modèle Automation](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## Programmation fiable  
  
-   L'instance d'éditeur est créé lorsque l'IDE appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode. Si l'éditeur prend en charge plusieurs vues, `CreateEditorInstance` crée les données du document et les objets de vue de document. Si l'objet de données de document est déjà ouvrir, non null `punkDocDataExisting` la valeur est passée à `IVsEditorFactory::CreateEditorInstance`. Votre implémentation de fabrique d'éditeur doit déterminer si un objet de données de document est compatible en interrogeant des interfaces appropriées sur celui\-ci. Pour plus d'informations, consultez [Prend en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md).  
  
-   Si vous utilisez l'approche simplifiée de l'incorporation, implémentez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface.  
  
-   Si vous décidez d'utiliser l'activation sur place, implémenter les interfaces suivantes :  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  Le `IOleInPlaceComponent` interface est utilisée pour éviter la fusion de menus OLE 2.  
  
     Votre `IOleCommandTarget` implémentation gère des commandes telles que **Couper**, **copie**, et **Coller**. Lors de l'implémentation `IOleCommandTarget`, décidez si votre éditeur requiert son propre fichier .vsct pour définir sa propre structure de menu de commande ou si elle peut implémenter les commandes standards définies par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En règle générale, les éditeurs utilisent et d'étendent les menus de l'IDE et définissent leurs propres barres d'outils. Toutefois, il est souvent nécessaire pour un éditeur définir ses propres commandes spécifiques en plus d'utiliser le jeu de commandes standard de l'IDE. Pour ce faire, votre éditeur doit déclarer les commandes standard, il utilise et définissez ensuite les nouvelles commandes, les menus contextuels, les menus de niveau supérieur et les barres d'outils dans un fichier .vsct. Si vous créez une activation en place de l'éditeur, puis implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> et définir les menus et les barres d'outils de l'éditeur dans un fichier .vsct au lieu d'utiliser la fusion de menus OLE 2.  
  
-   Pour empêcher la commande de menu charger dans l'interface utilisateur, vous devez utiliser les commandes existantes dans l'IDE avant d'inventer de nouvelles commandes. Commandes partagées sont définies dans SharedCmdDef.vsct et ShellCmdDef.vsct. Ces fichiers sont installés par défaut dans le sous\-répertoire VisualStudioIntegration\\Common\\Inc de votre [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] installation.  
  
-   `ISelectionContainer` peuvent exprimer des sélections uniques et multiples. Chaque objet sélectionné est implémenté comme un `IDispatch` objet.  
  
-   Implémente l'interface IDE `IOleUndoManager` en tant que service accessible à partir d'un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> ou comme un objet qui peut être instancié via <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Votre éditeur implémente la `IOleUndoUnit` interface pour chaque `Undo` action.  
  
-   Il existe deux emplacements un éditeur personnalisé peut exposer des objets automation :  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## Voir aussi  
 [Qui contribuent au modèle Automation](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Comment : fournir un contexte pour les éditeurs](../Topic/How%20to:%20Provide%20Context%20for%20Editors.md)