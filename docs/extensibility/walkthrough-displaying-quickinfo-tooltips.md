---
title: 'Procédure pas à pas : Affichage des info-bulles Info express | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 42ad89e544727a67611a305444f85ff022f6b2ff
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500028"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Procédure pas à pas : Info-bulles Info Express d’affichage
Info Express est une fonctionnalité IntelliSense qui affiche les signatures de méthode et descriptions lorsqu’un utilisateur déplace le pointeur sur un nom de méthode. Vous pouvez implémenter des fonctionnalités reposant sur le langage comme info Express en définissant les identificateurs pour lequel vous souhaitez fournir des descriptions d’info Express et puis en créant une info-bulle dans lequel afficher le contenu. Vous pouvez définir des info Express dans le contexte d’un service de langage, ou vous pouvez définir votre propre type de contenu et d’extension de nom fichier et afficher l’info Express pour uniquement ce type, ou vous pouvez afficher des info Express pour un type de contenu existant (par exemple, « text »). Cette procédure pas à pas montre comment afficher des info Express pour le type de contenu « texte ».  
  
 L’exemple d’info Express dans cette procédure pas à pas affiche les info-bulles quand un utilisateur déplace le pointeur sur un nom de méthode. Cette conception vous oblige à mettre en œuvre de ces quatre interfaces :  
  
-   interface de source  
  
-   interface du fournisseur de source  
  
-   interface de contrôleur  
  
-   interface du fournisseur de contrôleur  
  
 Les fournisseurs de source et de contrôleur sont des composants de Managed Extensibility Framework (MEF), responsables pour exporter les classes source et le contrôleur et sont l’importation de services et de répartiteurs comme le <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, ce qui crée le texte d’info-bulle mémoire tampon et le <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, ce qui déclenche la session info Express.  
  
 Dans cet exemple, la source info Express utilise une liste codée en dur des noms de méthodes et des descriptions, mais dans des implémentations complètes, le service de langage et de la documentation du langage doivent fournir ce contenu.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’avez pas besoin d’installer le SDK Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Créer un projet MEF  
  
### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF  
  
1.  Créez un projet c# VSIX. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `QuickInfoTest`.  
  
2.  Ajouter un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [créer une extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
## <a name="implement-the-quickinfo-source"></a>Implémenter la source info Express  
 La source info Express est responsable de la collecte de l’ensemble des identificateurs et leurs descriptions et en ajoutant le contenu à la mémoire tampon de texte info-bulle lorsqu’un des identificateurs est rencontré. Dans cet exemple, les identificateurs et leurs descriptions sont simplement ajoutées dans le constructeur de la source.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Pour implémenter la source info Express  
  
1.  Ajoutez un fichier de classe et nommez-le `TestQuickInfoSource`.  
  
2.  Ajoutez une référence à *Microsoft.VisualStudio.Language.IntelliSense*.  
  
3.  Ajoutez les importations ci-après.  
  
     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  Déclarez une classe qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>et nommez-le `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  Ajouter des champs pour le fournisseur de code source info Express, la mémoire tampon de texte et un ensemble de noms de méthode et les signatures de méthode. Dans cet exemple, les noms de méthode et les signatures sont initialisés dans le `TestQuickInfoSource` constructeur.  
  
     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  Ajoutez un constructeur qui définit le fournisseur de code source info Express et la mémoire tampon de texte et remplit l’ensemble des noms de méthode et les signatures de méthode et les descriptions.  
  
     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. Dans cet exemple, la méthode recherche le mot actuel ou le mot précédent si le curseur se trouve à la fin d’une ligne ou une mémoire tampon de texte. Si le mot est un des noms de méthode, la description de ce nom de méthode est ajoutée au contenu Info Express.  
  
     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  Vous devez également implémenter une méthode Dispose(), étant donné que <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implémente <xref:System.IDisposable>:  
  
     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implement-a-quickinfo-source-provider"></a>Implémenter un fournisseur de code source info Express  
 Le fournisseur de la source Info express sert principalement à exporter lui-même en tant que composant MEF et instancier la source info Express. S’agissant d’un composant MEF, qu’il puisse importer d’autres composants MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Pour implémenter un fournisseur de code source info Express  
  
1.  Déclarer un fournisseur de code source Info express nommé `TestQuickInfoSourceProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>et exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « Info-bulle Info express Source », un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> d’avant = « default » et un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « texte ».  
  
     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  Importer les deux services de l’éditeur, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> et <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, en tant que propriétés de `TestQuickInfoSourceProvider`.  
  
     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  Implémentez <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> pour retourner une nouvelle `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implement-a-quickinfo-controller"></a>Implémenter un contrôleur info Express  
 Info express contrôleurs déterminent quand info Express s’affiche. Dans cet exemple, Info Express s’affiche lorsque le pointeur est sur un mot qui correspond à un des noms de méthode. Le contrôleur Info express implémente un gestionnaire d’événements de pointage de souris qui déclenche une session info Express.  
  
### <a name="to-implement-a-quickinfo-controller"></a>Pour implémenter un contrôleur info Express  
  
1.  Déclarez une classe qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>et nommez-le `TestQuickInfoController`.  
  
     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  Ajouter des champs privés pour l’affichage de texte, les mémoires tampons de texte représentés dans l’affichage de texte, la session info Express et le fournisseur de contrôleur info Express.  
  
     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  Ajoutez un constructeur qui définit les champs et ajoute le Gestionnaire d’événements de pointage avec la souris.  
  
     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  Ajoutez le Gestionnaire d’événements de pointage de souris qui déclenche la session info Express.  
  
     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> méthode afin qu’elle supprime le Gestionnaire d’événements de pointage avec la souris lorsque le contrôleur est détaché de l’affichage de texte.  
  
     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  Implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> (méthode) et le <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> méthode en tant que méthodes vides pour cet exemple.  
  
     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implémentation d’un fournisseur de contrôleur info Express  
 Le fournisseur du contrôleur Info express sert principalement à exporter lui-même en tant que composant MEF et instancier le contrôleur info Express. S’agissant d’un composant MEF, qu’il puisse importer d’autres composants MEF.  
  
### <a name="to-implement-the-quickinfo-controller-provider"></a>Pour implémenter le fournisseur de contrôleur info Express  
  
1.  Déclarez une classe nommée `TestQuickInfoControllerProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>et exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « Info-bulle Info express Controller » et un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « texte » :  
  
     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  Importer le <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> en tant que propriété.  
  
     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> méthode en instanciant le contrôleur info Express.  
  
     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="build-and-test-the-code"></a>Générer et tester le Code  
 Pour tester ce code, générez la solution QuickInfoTest et exécutez-le dans l’instance expérimentale.  
  
### <a name="to-build-and-test-the-quickinfotest-solution"></a>Pour générer et tester la solution QuickInfoTest  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.  
  
3.  Créez un fichier texte et type du texte qui inclut les mots « Ajouter » et « soustraire ».  
  
4.  Déplacez le pointeur sur une des occurrences de « Ajouter ». La signature et la description de la `add` méthode doit être affichée.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Lier un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)