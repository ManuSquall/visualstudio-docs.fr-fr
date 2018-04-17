---
title: 'Procédure pas à pas : Personnalisation de l’affichage de texte | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4fb4762a422102b91c44d755d387168ab0572f2a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-customizing-the-text-view"></a>Procédure pas à pas : Personnalisation de l’affichage de texte
Vous pouvez personnaliser un affichage de texte en modifiant les propriétés suivantes dans sa table de format de l’éditeur :  
  
-   Marge des indicateurs  
  
-   Signe d’insertion  
  
-   Remplacer le signe insertion  
  
-   Texte sélectionné  
  
-   Texte sélectionné inactif (autrement dit, texte sélectionné a perdu le focus)  
  
-   Espace blanc visible  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Création d’un projet MEF  
  
1.  Créez un projet VSIX c#. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `ViewPropertyTest`.  
  
2.  Ajouter un modèle d’élément classifieur d’éditeur pour le projet. Pour plus d’informations, consultez [création d’une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
## <a name="defining-the-content-type"></a>Définition du Type de contenu  
  
1.  Ajoutez un fichier de classe et nommez-le `ViewPropertyModifier`.  
  
2.  Ajoutez le code suivant `using` directives :  
  
     [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
     [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  Déclarez une classe nommée `TestViewCreationListener` qui hérite de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Exporter cette classe avec les attributs suivants :  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Pour spécifier le type de contenu auquel ce port d’écoute s’applique.  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Pour spécifier le rôle de cet écouteur.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  Dans cette classe, vous devez importer le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
     [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
     [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>Modifier les propriétés d’affichage  
  
1.  Implémentez la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> méthode afin que les propriétés d’affichage sont modifiées lorsque la vue est ouvert. Pour que le changement, tout d’abord de trouver le <xref:System.Windows.ResourceDictionary> qui correspond à l’aspect de la vue que vous souhaitez rechercher. Changez la propriété appropriée dans le dictionnaire de ressources, puis définissez les propriétés. Traiter par lot les appels à la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> en appelant le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> méthode avant de définir les propriétés, puis le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> après avoir défini les propriétés.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
  
1.  Générez la solution.  
  
     Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
2.  Créez un fichier texte et tapez du texte.  
  
    -   Le signe d’insertion doit être à magenta et le signe insertion de remplacement doit être turquoise.  
  
    -   La marge des indicateurs (à gauche de l’affichage de texte) doit être claire vert.  
  
3.  Sélectionnez le texte que vous venez de taper. La couleur du texte sélectionné doit être clair rose.  
  
4.  Le texte est sélectionné, cliquez n’importe où en dehors de la fenêtre de texte. La couleur du texte sélectionné doit être rose foncé.  
  
5.  Espace blanc visible sous tension. (Sur le **modifier** menu, pointez sur **avancé** puis cliquez sur **afficher les espaces**). Tapez le texte des onglets. Les flèches rouges qui représentent les onglets doivent être affichés.  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)