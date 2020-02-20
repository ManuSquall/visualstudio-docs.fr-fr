---
title: 'Procédure pas à pas : affichage des info-bulles Info-bulle | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 3e75188c359a88bfe40a820546d7b042ecaacdac
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476950"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Procédure pas à pas : afficher les info-bulles Info Express
Info Express est une fonctionnalité IntelliSense qui affiche des signatures et des descriptions de méthode lorsqu’un utilisateur déplace le pointeur sur un nom de méthode. Vous pouvez implémenter des fonctionnalités basées sur le langage, telles que Info Express, en définissant les identificateurs pour lesquels vous souhaitez fournir des descriptions Info Express, puis en créant une info-bulle dans laquelle afficher le contenu. Vous pouvez définir Info Express dans le contexte d’un service de langage, ou vous pouvez définir votre propre extension de nom de fichier et type de contenu et afficher l’info-automatique pour ce type, ou vous pouvez afficher info Express pour un type de contenu existant (tel que « texte »). Cette procédure pas à pas montre comment afficher info Express pour le type de contenu « texte ».

 L’exemple info-bulle de cette procédure pas à pas affiche les info-bulles lorsqu’un utilisateur déplace le pointeur sur un nom de méthode. Cette conception vous oblige à implémenter ces quatre interfaces :

- interface source

- interface du fournisseur source

- interface du contrôleur

- interface du fournisseur de contrôleur

  Les fournisseurs de sources et de contrôleurs sont des composants de Managed Extensibility Framework (MEF), et sont responsables de l’exportation des classes source et contrôleur et de l’importation des services et des courtiers, tels que le <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, qui crée la mémoire tampon de texte info-bulle et la <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, qui déclenche la session Info Express.

  Dans cet exemple, la source Info Express utilise une liste codée en dur des noms et des descriptions des méthodes, mais dans les implémentations complètes, le service de langage et la documentation du langage sont responsables de la fourniture de ce contenu.

## <a name="prerequisites"></a>Conditions préalables requises
 À compter de Visual Studio 2015, vous n’avez pas besoin d’installer le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Créer un projet MEF

### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF

1. Créez un C# projet VSIX. (Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C# /extensibilité**, puis **projet VSIX**.) Nommez la solution `QuickInfoTest`.

2. Ajoutez un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

## <a name="implement-the-quickinfo-source"></a>Implémenter la source Info Express
 La source Info Express est chargée de collecter le jeu d’identificateurs et leurs descriptions, et d’ajouter le contenu à la mémoire tampon de texte info-bulle lorsque l’un des identificateurs est rencontré. Dans cet exemple, les identificateurs et leurs descriptions sont simplement ajoutés dans le constructeur source.

#### <a name="to-implement-the-quickinfo-source"></a>Pour implémenter la source Info Express

1. Ajoutez un fichier de classe et nommez-le `TestQuickInfoSource`.

2. Ajoutez une référence à *Microsoft. VisualStudio. Language. IntelliSense*.

3. Ajoutez les importations suivantes.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Déclarez une classe qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>et nommez-la `TestQuickInfoSource`.

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Ajoutez des champs pour le fournisseur de source Info Express, la mémoire tampon de texte et un ensemble de noms de méthode et de signatures de méthode. Dans cet exemple, les noms et les signatures des méthodes sont initialisés dans le constructeur `TestQuickInfoSource`.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Ajoutez un constructeur qui définit le fournisseur de source Info Express et la mémoire tampon de texte, et remplit l’ensemble de noms de méthodes, ainsi que les signatures et les descriptions de méthode.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. Dans cet exemple, la méthode recherche le mot actuel ou le mot précédent si le curseur se trouve à la fin d’une ligne ou d’une mémoire tampon de texte. Si le mot est l’un des noms de méthode, la description de ce nom de méthode est ajoutée au contenu Info Express.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. Vous devez également implémenter une méthode Dispose (), car <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implémente <xref:System.IDisposable>:

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Implémenter un fournisseur de source Info Express
 Le fournisseur de la source Info-Express sert principalement à s’exporter en tant que composant MEF et à instancier la source Info-Express. Étant donné qu’il s’agit d’une partie du composant MEF, il peut importer d’autres composants MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Pour implémenter un fournisseur de source Info Express

1. Déclarez un fournisseur de source info-bulle nommé `TestQuickInfoSourceProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>, puis exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « ToolTip source info-bulle », une <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de Before = « default » et un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « Text ».

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Importez deux services de l’éditeur, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> et <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, en tant que propriétés de `TestQuickInfoSourceProvider`.

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Implémentez <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> pour retourner un nouveau `TestQuickInfoSource`.

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Implémenter un contrôleur Info Express
 Les contrôleurs d’info-Express déterminent le moment où Info Express est affiché. Dans cet exemple, info Express s’affiche lorsque le pointeur se trouve sur un mot qui correspond à l’un des noms de méthode. Le contrôleur Info-Express implémente un gestionnaire d’événements de pointage de la souris qui déclenche une session Info Express.

### <a name="to-implement-a-quickinfo-controller"></a>Pour implémenter un contrôleur Info Express

1. Déclarez une classe qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>et nommez-la `TestQuickInfoController`.

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Ajoutez des champs privés pour l’affichage de texte, les mémoires tampons de texte représentées dans l’affichage de texte, la session Info Express et le fournisseur de contrôleur Info Express.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Ajoutez un constructeur qui définit les champs et ajoute le gestionnaire d’événements de pointage de la souris.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Ajoutez le gestionnaire d’événements de pointage de la souris qui déclenche la session Info Express.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> pour supprimer le gestionnaire d’événements de pointage de la souris lorsque le contrôleur est détaché de la vue de texte.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> et la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> en tant que méthodes vides pour cet exemple.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Implémentation du fournisseur de contrôleur Info Express
 Le fournisseur du contrôleur Info-Express sert principalement à s’exporter en tant que composant MEF et à instancier le contrôleur Info Express. Étant donné qu’il s’agit d’une partie du composant MEF, il peut importer d’autres composants MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Pour implémenter le fournisseur de contrôle d’info-Express

1. Déclarez une classe nommée `TestQuickInfoControllerProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>et exportez-la avec une <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de « ToolTip info Controller » et une <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> « Text » :

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Importez le <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> en tant que propriété.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> en instanciant le contrôleur Info Express.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Générer et tester le code
 Pour tester ce code, générez la solution QuickInfoTest et exécutez-la dans l’instance expérimentale.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Pour générer et tester la solution QuickInfoTest

1. Générez la solution.

2. Quand vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.

3. Créez un fichier texte et tapez du texte qui comprend les mots « ajouter » et « soustraire ».

4. Déplacez le pointeur sur l’une des occurrences de « Add ». La signature et la description de la méthode `add` doivent être affichées.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
