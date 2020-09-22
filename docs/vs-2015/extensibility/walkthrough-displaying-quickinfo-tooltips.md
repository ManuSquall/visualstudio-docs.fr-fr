---
title: 'Procédure pas à pas : affichage des info-bulles Info-bulle | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b349f0293071dfa30677b7558ca93985d16d55e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839766"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Procédure pas à pas : affichage d’info-bulles Info express
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Info Express est une fonctionnalité IntelliSense qui affiche des signatures et des descriptions de méthode lorsqu’un utilisateur déplace le pointeur sur un nom de méthode. Vous pouvez implémenter des fonctionnalités basées sur le langage, telles que Info Express, en définissant les identificateurs pour lesquels vous souhaitez fournir des descriptions Info Express, puis en créant une info-bulle dans laquelle afficher le contenu. Vous pouvez définir Info Express dans le contexte d’un service de langage, ou vous pouvez définir votre propre extension de nom de fichier et type de contenu et afficher l’info-automatique pour ce type, ou vous pouvez afficher info Express pour un type de contenu existant (tel que « texte »). Cette procédure pas à pas montre comment afficher info Express pour le type de contenu « texte ».  
  
 L’exemple info-bulle de cette procédure pas à pas affiche les info-bulles lorsqu’un utilisateur déplace le pointeur sur un nom de méthode. Cette conception vous oblige à implémenter ces quatre interfaces :  
  
- interface source  
  
- interface du fournisseur source  
  
- interface du contrôleur  
  
- interface du fournisseur de contrôleur  
  
  Les fournisseurs de sources et de contrôleurs sont des composants Managed Extensibility Framework (MEF) et sont responsables de l’exportation des classes source et contrôleur et de l’importation des services et des courtiers tels que le <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , qui crée la mémoire tampon de texte info-bulle et le <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> , qui déclenche la session Info Express.  
  
  Dans cet exemple, la source Info Express utilise une liste codée en dur des noms et des descriptions des méthodes, mais dans les implémentations complètes, le service de langage et la documentation du langage sont responsables de la fourniture de ce contenu.  
  
## <a name="prerequisites"></a>Prérequis  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Création d’un projet MEF  
  
#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF  
  
1. Créez un projet VSIX C#. (Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C#/extensibilité**, puis **projet VSIX**.) Nommez la solution `QuickInfoTest` .  
  
2. Ajoutez un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [création d’une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Supprimez les fichiers de classe existants.  
  
## <a name="implementing-the-quickinfo-source"></a>Implémentation de la source Info Express  
 La source Info Express est chargée de collecter le jeu d’identificateurs et leurs descriptions, et d’ajouter le contenu à la mémoire tampon de texte info-bulle lorsque l’un des identificateurs est rencontré. Dans cet exemple, les identificateurs et leurs descriptions sont simplement ajoutés dans le constructeur source.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Pour implémenter la source Info Express  
  
1. Ajoutez un fichier de classe et nommez-le `TestQuickInfoSource`.  
  
2. Ajoutez une référence à Microsoft. VisualStudio. Language. IntelliSense.  
  
3. Ajoutez les importations suivantes.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4. Déclarez une classe qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> et nommez-la `TestQuickInfoSource` .  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5. Ajoutez des champs pour le fournisseur de source Info Express, la mémoire tampon de texte et un ensemble de noms de méthode et de signatures de méthode. Dans cet exemple, les noms et les signatures de méthode sont initialisés dans le `TestQuickInfoSource` constructeur.  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6. Ajoutez un constructeur qui définit le fournisseur de source Info Express et la mémoire tampon de texte, et remplit l’ensemble de noms de méthodes, ainsi que les signatures et les descriptions de méthode.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. Dans cet exemple, la méthode recherche le mot actuel ou le mot précédent si le curseur se trouve à la fin d’une ligne ou d’une mémoire tampon de texte. Si le mot est l’un des noms de méthode, la description de ce nom de méthode est ajoutée au contenu Info Express.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8. Vous devez également implémenter une méthode Dispose (), puisque <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implémente <xref:System.IDisposable> :  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implémentation d’un fournisseur de source Info Express  
 Le fournisseur de la source Info-Express sert principalement à s’exporter en tant que composant MEF et à instancier la source Info-Express. Étant donné qu’il s’agit d’une partie de composant MEF, elle peut importer d’autres composants MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Pour implémenter un fournisseur de source Info Express  
  
1. Déclarez un fournisseur de source info `TestQuickInfoSourceProvider` -bulle nommé qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> , puis exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « ToolTip source info-bulle », un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de Before = « default » et un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « Text ».  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2. Importez deux services de l’éditeur, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> et <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , en tant que propriétés de `TestQuickInfoSourceProvider` .  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3. Implémentez <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> pour retourner un nouveau `TestQuickInfoSource` .  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implémentation d’un contrôleur Info Express  
 Les contrôleurs d’info-Express déterminent quand l’affichage Express doit être affiché. Dans cet exemple, info Express s’affiche lorsque le pointeur se trouve sur un mot qui correspond à l’un des noms de méthode. Le contrôleur Info-Express implémente un gestionnaire d’événements de pointage de la souris qui déclenche une session Info Express.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Pour implémenter un contrôleur Info Express  
  
1. Déclarez une classe qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> et nommez-la `TestQuickInfoController` .  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2. Ajoutez des champs privés pour l’affichage de texte, les mémoires tampons de texte représentées dans l’affichage de texte, la session Info Express et le fournisseur de contrôleur Info Express.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3. Ajoutez un constructeur qui définit les champs et ajoute le gestionnaire d’événements de pointage de la souris.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4. Ajoutez le gestionnaire d’événements de pointage de la souris qui déclenche la session Info Express.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5. Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> méthode afin qu’elle supprime le gestionnaire d’événements de pointage de la souris lorsque le contrôleur est détaché de la vue de texte.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6. Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> méthode et la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> méthode comme méthodes vides pour cet exemple.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implémentation du fournisseur de contrôleur Info Express  
 Le fournisseur du contrôleur Info-Express sert principalement à s’exporter en tant que composant MEF et à instancier le contrôleur Info Express. Étant donné qu’il s’agit d’une partie de composant MEF, elle peut importer d’autres composants MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Pour implémenter le fournisseur de contrôle d’info-Express  
  
1. Déclarez une classe nommée `TestQuickInfoControllerProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> et exportez-la avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de type « ToolTip info Controller » et un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « Text » :  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2. Importez le <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> en tant que propriété.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3. Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> méthode en instanciant le contrôleur Info Express.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
 Pour tester ce code, générez la solution QuickInfoTest et exécutez-la dans l’instance expérimentale.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Pour générer et tester la solution QuickInfoTest  
  
1. Générez la solution.  
  
2. Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3. Créez un fichier texte et tapez du texte qui comprend les mots « ajouter » et « soustraire ».  
  
4. Déplacez le pointeur sur l’une des occurrences de « Add ». La signature et la description de la `add` méthode doivent être affichées.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
