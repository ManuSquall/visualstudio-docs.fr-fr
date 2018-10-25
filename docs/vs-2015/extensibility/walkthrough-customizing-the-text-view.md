---
title: 'Procédure pas à pas : Personnalisation de l’affichage de texte | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8474190b6b140883a43555f5dc35091daecebe7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923197"
---
# <a name="walkthrough-customizing-the-text-view"></a>Procédure pas à pas : personnalisation de l’affichage du texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez personnaliser un affichage de texte en modifiant les propriétés suivantes dans sa table de format de l’éditeur :  
  
-   Marge des indicateurs  
  
-   Signe d’insertion  
  
-   Remplacer le signe insertion  
  
-   Texte sélectionné  
  
-   Texte sélectionné inactif (autrement dit, les texte sélectionné qui a perdu le focus)  
  
-   Espace blanc visible  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Création d’un projet MEF  
  
1.  Créez un projet c# VSIX. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `ViewPropertyTest`.  
  
2.  Ajouter un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [création d’une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
## <a name="defining-the-content-type"></a>La définition du Type de contenu  
  
1. Ajoutez un fichier de classe et nommez-le `ViewPropertyModifier`.  
  
2. Ajoutez le code suivant `using` directives :  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Déclarez une classe nommée `TestViewCreationListener` qui hérite de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Exporter cette classe avec les attributs suivants :  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Pour spécifier le type de contenu auquel s’applique cet écouteur.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Pour spécifier le rôle de cet écouteur.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. Dans cette classe, importez le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Modification des propriétés d’affichage  
  
1.  Implémentez la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> méthode afin que les propriétés d’affichage sont modifiées lorsque la vue est ouvert. Pour apporter la modification, commencez par rechercher le <xref:System.Windows.ResourceDictionary> qui correspond à l’aspect de la vue que vous souhaitez rechercher. Changez la propriété appropriée dans le dictionnaire de ressources, puis définissez les propriétés. Par lot les appels à la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> méthode en appelant le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> méthode avant de définir les propriétés, puis le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> après avoir défini les propriétés.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
  
1.  Générez la solution.  
  
     Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
2.  Créez un fichier texte et tapez du texte.  
  
    -   Le signe d’insertion doit être magenta et le signe insertion de remplacement doit être turquoise.  
  
    -   La marge des indicateurs (à gauche de l’affichage de texte) doit être le voyant vert.  
  
3.  Sélectionnez le texte que vous venez de saisir. La couleur du texte sélectionné doit être clair rose.  
  
4.  Le texte est sélectionné, cliquez n’importe où en dehors de la fenêtre texte. La couleur du texte sélectionné doit être rose sombre.  
  
5.  Allumez l’espace blanc visible. (Sur le **modifier** menu, pointez sur **avancé** puis cliquez sur **afficher les espaces**). Tapez le texte des onglets. Les flèches rouges qui représentent les onglets doivent être affichés.  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)

