---
title: "Procédure pas à pas : Personnalisation de l’affichage de texte | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e40368ed6aaf68b747f19cffe4e378a89ff6c0b5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-customizing-the-text-view"></a>Procédure pas à pas : Personnalisation de l’affichage de texte
Vous pouvez personnaliser une vue de texte en modifiant les propriétés suivantes dans son plan de format de l’éditeur :  
  
-   Marge des indicateurs  
  
-   Signe d’insertion  
  
-   Remplacer le signe insertion  
  
-   Texte sélectionné  
  
-   Texte sélectionné inactif (autrement dit, texte sélectionné a perdu le focus)  
  
-   Espace blanc visible  
  
## <a name="prerequisites"></a>Conditions préalables  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d’informations, consultez [l’installation du Kit de développement logiciel Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Création d’un projet MEF  
  
1.  Créez un projet VSIX c#. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual C# / extensibilité**, puis **projet VSIX**.) Nommez la solution `ViewPropertyTest`.  
  
2.  Ajouter un modèle d’élément éditeur classifieur au projet. Pour plus d’informations, consultez [avec un éditeur de modèle d’élément pour créer une Extension](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
## <a name="defining-the-content-type"></a>Définition du Type de contenu  
  
1.  Ajoutez un fichier de classe et nommez-le `ViewPropertyModifier`.  
  
2.  Ajoutez le code suivant `using` directives :  
  
     [!code-cs[N °&1; de VSSDKViewPropertyTest](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs) ] 
     [!code-vb [VSSDKViewPropertyTest n °&1;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  Déclarez une classe nommée `TestViewCreationListener` qui hérite de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> Exporter cette classe avec les attributs suivants :  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>Pour spécifier le type de contenu auquel s’applique cet écouteur.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>Pour spécifier le rôle de cet écouteur.</xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>  
  
     [!code-cs[VSSDKViewPropertyTest n °&2;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest n °&2;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  Dans cette classe, importez le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>  
  
     [!code-cs[VSSDKViewPropertyTest n °&3;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs) ] 
     [!code-vb [VSSDKViewPropertyTest n°&3;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>Modifier les propriétés d’affichage  
  
1.  Implémentez la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>méthode afin que les propriétés d’affichage sont modifiées lorsque la vue est ouverte.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Pour apporter la modification, commencez par rechercher la <xref:System.Windows.ResourceDictionary>qui correspond à l’aspect de la vue que vous souhaitez rechercher.</xref:System.Windows.ResourceDictionary> Changez la propriété appropriée dans le dictionnaire de ressources, puis définir les propriétés. Par lot les appels à la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>en appelant le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>méthode avant de définir les propriétés, puis le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>après avoir défini les propriétés.</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>  
  
     [!code-cs[VSSDKViewPropertyTest n °&4;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs) ] 
     [!code-vb [VSSDKViewPropertyTest n °&4;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
  
1.  Générez la solution.  
  
     Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
2.  Créez un fichier texte et tapez du texte.  
  
    -   Le signe d’insertion doit être magenta et le signe insertion de remplacement doit être turquoise.  
  
    -   La marge des indicateurs (à gauche de l’affichage de texte) doit être le voyant vert.  
  
3.  Sélectionnez le texte que vous venez de saisir. La couleur du texte sélectionné doit être clair rose.  
  
4.  Le texte est sélectionné, cliquez n’importe où en dehors de la fenêtre texte. La couleur du texte sélectionné doit être rose foncé.  
  
5.  Espace blanc visible sous tension. (Sur le **modifier** menu, pointez sur **avancé** , puis **afficher les espaces**). Tapez le texte des onglets. Les flèches rouges qui représentent les onglets doivent être affichés.  
  
## <a name="see-also"></a>Voir aussi  
 [Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md)
