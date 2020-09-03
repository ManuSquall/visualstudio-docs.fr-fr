---
title: 'Procédure pas à pas : personnalisation de l’affichage de texte | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e96bb177d3cfa90b2c80304eabfd93d1bea76d5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202026"
---
# <a name="walkthrough-customizing-the-text-view"></a>Procédure pas à pas : personnalisation de l’affichage du texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez personnaliser un affichage de texte en modifiant l’une des propriétés suivantes dans sa carte de format d’éditeur :  
  
- Marge des indicateurs  
  
- Signe insertion  
  
- Remplacer le signe insertion  
  
- Texte sélectionné  
  
- Texte sélectionné inactif (autrement dit, texte sélectionné qui a perdu le focus)  
  
- Espace blanc visible  
  
## <a name="prerequisites"></a>Prérequis  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Création d’un projet MEF  
  
1. Créez un projet VSIX C#. (Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C#/extensibilité**, puis **projet VSIX**.) Nommez la solution `ViewPropertyTest` .  
  
2. Ajoutez un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [création d’une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Supprimez les fichiers de classe existants.  
  
## <a name="defining-the-content-type"></a>Définition du type de contenu  
  
1. Ajoutez un fichier de classe et nommez-le `ViewPropertyModifier`.  
  
2. Ajoutez les directives `using` suivantes :  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Déclarez une classe nommée `TestViewCreationListener` qui hérite de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Exportez cette classe avec les attributs suivants :  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> pour spécifier le type de contenu auquel cet écouteur s’applique.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> pour spécifier le rôle de cet écouteur.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. Dans cette classe, importez le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Modification des propriétés de la vue  
  
1. Implémentez la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> méthode afin que les propriétés de la vue soient modifiées lorsque la vue est ouverte. Pour effectuer la modification, commencez par Rechercher le <xref:System.Windows.ResourceDictionary> qui correspond à l’aspect de la vue que vous souhaitez rechercher. Modifiez ensuite la propriété appropriée dans le dictionnaire de ressources et définissez les propriétés. Traite les appels à la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> méthode en appelant la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> méthode avant de définir les propriétés, puis le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> après avoir défini les propriétés.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
  
1. Générez la solution.  
  
     Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
2. Créez un fichier texte et tapez du texte.  
  
    - Le signe insertion doit être magenta et le signe insertion de remplacement doit être turquoise.  
  
    - La marge des indicateurs (à gauche de l’affichage de texte) doit être verte.  
  
3. Sélectionnez le texte que vous venez de taper. La couleur du texte sélectionné doit être rose clair.  
  
4. Lorsque le texte est sélectionné, cliquez n’importe où en dehors de la fenêtre de texte. La couleur du texte sélectionné doit être rose foncé.  
  
5. Activez les espaces blancs visibles. (Dans le menu **Edition** , pointez sur **avancé** , puis cliquez sur Afficher les espaces **blancs**). Tapez certains onglets dans le texte. Les flèches rouges représentant les onglets doivent être affichées.  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
