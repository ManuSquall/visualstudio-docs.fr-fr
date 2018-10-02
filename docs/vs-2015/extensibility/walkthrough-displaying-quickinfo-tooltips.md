---
title: 'Procédure pas à pas : Affichage des info-bulles Info express | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b13dce0ea4f2bb54c802b63fd19f74b8173e94d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504600"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Procédure pas à pas : affichage d’info-bulles Info express
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [procédure pas à pas : affichage des info-bulles Info](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-displaying-quickinfo-tooltips).  
  
Info Express est une fonctionnalité IntelliSense qui affiche les signatures de méthode et descriptions lorsqu’un utilisateur déplace le pointeur sur un nom de méthode. Vous pouvez implémenter des fonctionnalités reposant sur le langage comme info Express en définissant les identificateurs pour lequel vous souhaitez fournir des descriptions d’info Express et puis en créant une info-bulle dans lequel afficher le contenu. Vous pouvez définir des info Express dans le contexte d’un service de langage, ou vous pouvez définir votre propre type de contenu et d’extension de nom fichier et afficher l’info Express pour uniquement ce type, ou vous pouvez afficher des info Express pour un type de contenu existant (par exemple, « text »). Cette procédure pas à pas montre comment afficher des info Express pour le type de contenu « texte ».  
  
 L’exemple d’info Express dans cette procédure pas à pas affiche les info-bulles quand un utilisateur déplace le pointeur sur un nom de méthode. Cette conception vous oblige à mettre en œuvre de ces quatre interfaces :  
  
-   interface de source  
  
-   interface du fournisseur de source  
  
-   interface de contrôleur  
  
-   interface du fournisseur de contrôleur  
  
 Les fournisseurs de source et de contrôleur sont des composants de Managed Extensibility Framework (MEF), responsables pour exporter les classes source et le contrôleur et sont l’importation de services et de répartiteurs comme le <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, ce qui crée le texte d’info-bulle mémoire tampon et le <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, ce qui déclenche la session info Express.  
  
 Dans cet exemple, la source info Express utilise une liste codée en dur des noms de méthodes et des descriptions, mais dans des implémentations complètes, le service de langage et de la documentation du langage doivent fournir ce contenu.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Création d’un projet MEF  
  
#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF  
  
1.  Créez un projet c# VSIX. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `QuickInfoTest`.  
  
2.  Ajouter un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [création d’une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
## <a name="implementing-the-quickinfo-source"></a>Implémentation de la Source info Express  
 La source info Express est responsable de la collecte de l’ensemble des identificateurs et leurs descriptions et en ajoutant le contenu à la mémoire tampon de texte info-bulle lorsqu’un des identificateurs est rencontré. Dans cet exemple, les identificateurs et leurs descriptions sont simplement ajoutées dans le constructeur de la source.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Pour implémenter la source info Express  
  
1.  Ajoutez un fichier de classe et nommez-le `TestQuickInfoSource`.  
  
2.  Ajoutez une référence à Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Ajoutez les importations ci-après.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4.  Déclarez une classe qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>et nommez-le `TestQuickInfoSource`.  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5.  Ajouter des champs pour le fournisseur de code source info Express, la mémoire tampon de texte et un ensemble de noms de méthode et les signatures de méthode. Dans cet exemple, les noms de méthode et les signatures sont initialisés dans le `TestQuickInfoSource` constructeur.  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6.  Ajoutez un constructeur qui définit le fournisseur de code source info Express et la mémoire tampon de texte et remplit l’ensemble des noms de méthode et les signatures de méthode et les descriptions.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7.  Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. Dans cet exemple, la méthode recherche le mot actuel ou le mot précédent si le curseur se trouve à la fin d’une ligne ou une mémoire tampon de texte. Si le mot est un des noms de méthode, la description de ce nom de méthode est ajoutée au contenu Info Express.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8.  Vous devez également implémenter une méthode Dispose(), étant donné que <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implémente <xref:System.IDisposable>:  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implémentation d’un fournisseur de Source de l’info Express  
 Le fournisseur de la source Info express sert principalement à exporter lui-même en tant que composant MEF et instancier la source info Express. S’agissant d’un composant MEF, qu’il puisse importer d’autres composants MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Pour implémenter un fournisseur de code source info Express  
  
1.  Déclarer un fournisseur de code source Info express nommé `TestQuickInfoSourceProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>et exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « Info-bulle Info express Source », un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> d’avant = « default » et un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « texte ».  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2.  Importer les deux services de l’éditeur, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> et <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, en tant que propriétés de `TestQuickInfoSourceProvider`.  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3.  Implémentez <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> pour retourner une nouvelle `TestQuickInfoSource`.  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implémentation d’un contrôleur info Express  
 Info express contrôleurs déterminent quand Info express doit être affichée. Dans cet exemple, Info Express s’affiche lorsque le pointeur est sur un mot qui correspond à un des noms de méthode. Le contrôleur Info express implémente un gestionnaire d’événements de pointage de souris qui déclenche une session info Express.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Pour implémenter un contrôleur info Express  
  
1.  Déclarez une classe qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>et nommez-le `TestQuickInfoController`.  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2.  Ajouter des champs privés pour l’affichage de texte, les mémoires tampons de texte représentés dans l’affichage de texte, la session info Express et le fournisseur de contrôleur info Express.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3.  Ajoutez un constructeur qui définit les champs et ajoute le Gestionnaire d’événements de pointage avec la souris.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4.  Ajoutez le Gestionnaire d’événements de pointage de souris qui déclenche la session info Express.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> méthode afin qu’elle supprime le Gestionnaire d’événements de pointage avec la souris lorsque le contrôleur est détaché de l’affichage de texte.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6.  Implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> (méthode) et le <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> méthode en tant que méthodes vides pour cet exemple.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implémentation d’un fournisseur Info express contrôleur  
 Le fournisseur du contrôleur Info express sert principalement à exporter lui-même en tant que composant MEF et instancier le contrôleur info Express. S’agissant d’un composant MEF, qu’il puisse importer d’autres composants MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Pour implémenter le fournisseur de contrôleur info Express  
  
1.  Déclarez une classe nommée `TestQuickInfoControllerProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>et exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « Info-bulle Info express Controller » et un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « texte » :  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2.  Importer le <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> en tant que propriété.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> méthode en instanciant le contrôleur info Express.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
 Pour tester ce code, générez la solution QuickInfoTest et exécutez-le dans l’instance expérimentale.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Pour générer et tester la solution QuickInfoTest  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3.  Créez un fichier texte et type du texte qui inclut les mots « Ajouter » et « soustraire ».  
  
4.  Déplacez le pointeur sur une des occurrences de « Ajouter ». La signature et la description de la `add` méthode doit être affichée.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

