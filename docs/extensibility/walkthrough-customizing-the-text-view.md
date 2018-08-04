---
title: 'Procédure pas à pas : Personnalisation de l’affichage de texte | Microsoft Docs'
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
ms.openlocfilehash: da09f01e602f2d30288bc9f872f761d0bee4fc42
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498404"
---
# <a name="walkthrough-customize-the-text-view"></a>Procédure pas à pas : Personnaliser l’affichage de texte
Vous pouvez personnaliser un affichage de texte en modifiant les propriétés suivantes dans sa table de format de l’éditeur :  
  
-   Marge des indicateurs  
  
-   Signe d’insertion  
  
-   Remplacer le signe insertion  
  
-   Texte sélectionné  
  
-   Texte sélectionné inactif (autrement dit, les texte sélectionné qui a perdu le focus)  
  
-   Espace blanc visible  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Créer un projet MEF  
  
1.  Créez un projet c# VSIX. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `ViewPropertyTest`.  
  
2.  Ajouter un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [créer une extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
## <a name="define-the-content-type"></a>Définir le type de contenu  
  
1.  Ajoutez un fichier de classe et nommez-le `ViewPropertyModifier`.  
  
2.  Ajoutez le code suivant `using` directives :  
  
     [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
     [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  Déclarez une classe nommée `TestViewCreationListener` qui hérite de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Exporter cette classe avec les attributs suivants :  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Pour spécifier le type de contenu auquel s’applique cet écouteur.  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Pour spécifier le rôle de cet écouteur.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  Dans cette classe, importez le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
     [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
     [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="change-the-view-properties"></a>Modifier les propriétés de la vue  
  
1.  Configurer le <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> méthode afin que les propriétés d’affichage sont modifiées lorsque la vue est ouvert. Pour apporter la modification, commencez par rechercher le <xref:System.Windows.ResourceDictionary> qui correspond à l’aspect de la vue que vous souhaitez rechercher. Ensuite, modifiez la propriété appropriée dans le dictionnaire de ressources et définir les propriétés. Par lot les appels à la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> méthode en appelant le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> méthode avant de définir les propriétés, puis le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> après avoir défini les propriétés.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="build-and-test-the-code"></a>Générer et tester le code  
  
1.  Générez la solution.  
  
     Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.  
  
2.  Créez un fichier texte et tapez du texte.  
  
    -   Le signe d’insertion doit être magenta et le signe insertion de remplacement doit être turquoise.  
  
    -   La marge des indicateurs (à gauche de l’affichage de texte) doit être le voyant vert.  
  
3.  Sélectionnez le texte que vous avez tapé. La couleur du texte sélectionné doit être clair rose.  
  
4.  Le texte est sélectionné, cliquez n’importe où en dehors de la fenêtre texte. La couleur du texte sélectionné doit être rose sombre.  
  
5.  Allumez l’espace blanc visible. (Sur le **modifier** menu, pointez sur **avancé** puis cliquez sur **afficher les espaces**). Tapez le texte des onglets. Les flèches rouges qui représentent les onglets doivent être affichés.  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension éditeur et le service de langage](../extensibility/language-service-and-editor-extension-points.md)