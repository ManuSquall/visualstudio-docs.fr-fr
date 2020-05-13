---
title: 'Procédure pas à pas : Affichage de QuickInfo Tooltips (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 47a14ca0692ad0338b56fd1d372307fb0e2ccc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697439"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Procédure pas à pas: Afficher des outils QuickInfo
QuickInfo est une fonctionnalité IntelliSense qui affiche les signatures et les descriptions de la méthode lorsqu’un utilisateur déplace le pointeur sur un nom de méthode. Vous pouvez implémenter des fonctionnalités basées sur la langue telles que QuickInfo en définissant les identifiants pour lesquels vous souhaitez fournir des descriptions QuickInfo, puis en créant un outil pour afficher le contenu. Vous pouvez définir QuickInfo dans le contexte d’un service linguistique, ou vous pouvez définir votre propre extension de nom de fichier et le type de contenu et afficher le QuickInfo pour ce type, ou vous pouvez afficher QuickInfo pour un type de contenu existant (comme "texte"). Ce pas-là montre comment afficher QuickInfo pour le type de contenu "texte".

 L’exemple QuickInfo dans cette procédure pas à pas affiche les outils lorsqu’un utilisateur déplace le pointeur sur un nom de méthode. Cette conception vous oblige à implémenter ces quatre interfaces :

- interface source

- interface fournisseur source

- interface de contrôleur

- interface fournisseur de contrôleur

  Les fournisseurs de sources et de contrôleurs sont des composants du Cadre d’exténuabilité gérée (MEF) <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>et sont responsables de l’exportation <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>des classes de source et de contrôleur et des services d’importation et des courtiers tels que le , qui crée le tampon texte tooltip, et le , qui déclenche la session QuickInfo.

  Dans cet exemple, la source QuickInfo utilise une liste codée de noms et de descriptions de méthodes, mais dans des implémentations complètes, le service linguistique et la documentation linguistique sont responsables de fournir ce contenu.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’avez pas besoin d’installer le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Créer un projet MEF

### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF

1. Créez un projet VSIX CMD. (Dans le dialogue du **nouveau projet,** sélectionnez **Visual C / Extensibility**, puis **VSIX Project**.) Nommez `QuickInfoTest`la solution .

2. Ajoutez un modèle d’élément Classificateur d’éditeur au projet. Pour plus d’informations, voir [Créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

## <a name="implement-the-quickinfo-source"></a>Implémenter la source QuickInfo
 La source QuickInfo est responsable de la collecte de l’ensemble des identifiants et de leurs descriptions et de l’ajout du contenu au tampon de texte de l’outil lorsque l’un des identificateurs est rencontré. Dans cet exemple, les identificateurs et leurs descriptions sont juste ajoutés dans le constructeur source.

#### <a name="to-implement-the-quickinfo-source"></a>Pour implémenter la source QuickInfo

1. Ajoutez un fichier de classe et nommez-le `TestQuickInfoSource`.

2. Ajouter une référence à *Microsoft.VisualStudio.Language.IntelliSense*.

3. Ajoutez les importations suivantes.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Déclarez une classe <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>qui met `TestQuickInfoSource`en œuvre, et nommez-le .

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Ajoutez des champs pour le fournisseur de source QuickInfo, le tampon de texte et un ensemble de noms de méthode et de signatures de méthode. Dans cet exemple, les noms et signatures `TestQuickInfoSource` de la méthode sont parasécés dans le constructeur.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Ajoutez un constructeur qui définit le fournisseur de source QuickInfo et le tampon de texte, et peuple l’ensemble des noms de méthode, et les signatures et descriptions de la méthode.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. Dans cet exemple, la méthode trouve le mot actuel, ou le mot précédent si le curseur est à la fin d’une ligne ou d’un tampon de texte. Si le mot est l’un des noms de méthode, la description de ce nom de méthode est ajoutée au contenu QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. Vous devez également mettre en œuvre une méthode Dispose() puisque <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> les impléments <xref:System.IDisposable>:

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Implémenter un fournisseur de source QuickInfo
 Le fournisseur de la source QuickInfo sert principalement à s’exporter comme une partie de composant MEF et à instantanéifier la source QuickInfo. Parce qu’il s’agit d’une partie composante MEF, il peut importer d’autres composants MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Pour implémenter un fournisseur de source QuickInfo

1. Déclarez un fournisseur `TestQuickInfoSourceProvider` de source <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>QuickInfo nommé <xref:Microsoft.VisualStudio.Utilities.NameAttribute> qui implémente, et <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "ToolTip QuickInfo Source", un de Avant "par défaut", et un de "texte".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Importer deux services <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>d’éditeur, `TestQuickInfoSourceProvider`et , comme propriétés de .

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Mise <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> en œuvre pour retourner un nouveau `TestQuickInfoSource`.

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Implémenter un contrôleur QuickInfo
 Les contrôleurs QuickInfo déterminent quand QuickInfo est affiché. Dans cet exemple, QuickInfo apparaît lorsque le pointeur est au-dessus d’un mot qui correspond à l’un des noms de méthode. Le contrôleur QuickInfo implémente un gestionnaire d’événements de vol stationnaire de souris qui déclenche une session QuickInfo.

### <a name="to-implement-a-quickinfo-controller"></a>Pour implémenter un contrôleur QuickInfo

1. Déclarez une classe <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>qui met `TestQuickInfoController`en œuvre, et nommez-le .

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Ajoutez des champs privés pour la vue textuelle, les tampons de texte représentés dans la vue de texte, la session QuickInfo et le fournisseur de contrôleur QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Ajoutez un constructeur qui définit les champs et ajoute le gestionnaire d’événements de vol stationnaire de souris.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Ajoutez le gestionnaire d’événements de vol stationnaire de souris qui déclenche la session QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> méthode de sorte qu’elle supprime le gestionnaire d’événements de vol stationnaire de souris lorsque le contrôleur est détaché de la vue de texte.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Implémenter <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> la méthode et la méthode comme méthodes vides pour cet exemple.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Mise en œuvre du fournisseur de contrôleurs QuickInfo
 Le fournisseur du contrôleur QuickInfo sert principalement à s’exporter comme une partie de composant MEF et à instantanéiser le contrôleur QuickInfo. Parce qu’il s’agit d’une partie composante MEF, il peut importer d’autres composants MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Pour implémenter le fournisseur de contrôleurs QuickInfo

1. Déclarez une `TestQuickInfoControllerProvider` classe <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>nommée qui implémente, et exportez-la avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> «ToolTip QuickInfo Controller» et un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de «texte»:

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Importez le <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> en tant que propriété.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Implémenter la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> méthode en instantanéisant le contrôleur QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Construire et tester le Code
 Pour tester ce code, créez la solution QuickInfoTest et exécutez-la dans l’instance expérimentale.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Pour construire et tester la solution QuickInfoTest

1. Générez la solution.

2. Lorsque vous exécutez ce projet dans le débbugger, une deuxième instance de Visual Studio est lancée.

3. Créez un fichier texte et tapez un texte qui inclut les mots « ajouter » et « soustraire ».

4. Déplacez le pointeur sur l’un des événements de "ajouter". La signature et la `add` description de la méthode doivent être affichées.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : liez un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
