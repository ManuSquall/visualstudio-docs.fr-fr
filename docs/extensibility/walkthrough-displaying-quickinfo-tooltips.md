---
title: "Procédure pas à pas : Affichage des info-bulles Info express | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 27
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
ms.openlocfilehash: b533e77a2310194b2bccc225f9902e5a8d502da5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Procédure pas à pas : Affichage des info-bulles Info express
Info Express est une fonctionnalité IntelliSense qui affiche les signatures de méthode et des descriptions lorsqu’un utilisateur déplace le pointeur sur un nom de méthode. Vous pouvez implémenter des fonctionnalités reposant sur le langage comme info Express en définissant les identificateurs pour lequel vous souhaitez fournir une description info Express et création d’une info-bulle dans lequel afficher le contenu. Vous pouvez définir des informations dans le contexte d’un service de langage, ou vous pouvez définir votre propre type de contenu et d’extension de nom fichier et afficher les informations de ce type, ou vous pouvez afficher des informations pour un type de contenu existant (par exemple, « texte »). Cette procédure pas à pas montre comment afficher des informations pour le type de contenu « texte ».  
  
 L’exemple info Express dans cette procédure pas à pas affiche les info-bulles lorsque l’utilisateur déplace le pointeur sur un nom de méthode. Cette conception, vous devez implémenter ces quatre interfaces :  
  
-   interface de source  
  
-   interface du fournisseur de source  
  
-   interface de contrôleur  
  
-   interface du fournisseur de contrôleur  
  
 Les fournisseurs de source et le contrôleur sont des composants de Managed Extensibility Framework (MEF) et sont chargés pour exporter les classes source et le contrôleur et l’importation des services et sert d’intermédiaire tel que le <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, qui crée la mémoire tampon de texte info-bulle et le <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, ce qui déclenche la session info Express.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> </xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>  
  
 Dans cet exemple, la source d’info Express utilise une liste codée en dur des noms de méthode et des descriptions, mais dans les implémentations complètes, le service de langage et de la documentation de langage doivent fournir ce contenu.  
  
## <a name="prerequisites"></a>Conditions préalables  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d’informations, consultez [l’installation du Kit de développement logiciel Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Création d’un projet MEF  
  
#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF  
  
1.  Créez un projet VSIX c#. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual C# / extensibilité**, puis **projet VSIX**.) Nommez la solution `QuickInfoTest`.  
  
2.  Ajouter un modèle d’élément éditeur classifieur au projet. Pour plus d’informations, consultez [avec un éditeur de modèle d’élément pour créer une Extension](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
## <a name="implementing-the-quickinfo-source"></a>L’implémentation de la Source d’info Express  
 La source d’informations est responsable de la collecte de l’ensemble des identificateurs et leurs descriptions et ajouter le contenu de la mémoire tampon de texte info-bulle lorsqu’un des identificateurs est rencontré. Dans cet exemple, les identificateurs et leurs descriptions sont simplement ajoutées dans le constructeur de la source.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Pour implémenter la source info Express  
  
1.  Ajoutez un fichier de classe et nommez-le `TestQuickInfoSource`.  
  
2.  Ajoutez une référence à Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Ajoutez les importations ci-après.  
  
     [!code-vb[N °&1; de VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n °&1;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  Déclarez une classe qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>et nommez-le `TestQuickInfoSource`.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
     [!code-vb[VSSDKQuickInfoTest n °&2;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n °&2;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  Ajouter des champs pour le fournisseur de source info Express, la mémoire tampon de texte et un ensemble de noms de méthode et les signatures de méthode. Dans cet exemple, les noms de méthode et les signatures sont initialisés dans le `TestQuickInfoSource` constructeur.  
  
     [!code-vb[VSSDKQuickInfoTest n °&3;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n°&3;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  Ajoutez un constructeur qui définit le fournisseur de source info Express et la mémoire tampon de texte et remplit l’ensemble des noms de méthode et les signatures de méthode et les descriptions.  
  
     [!code-vb[VSSDKQuickInfoTest n °&4;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n °&4;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>méthode.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> Dans cet exemple, la méthode recherche le mot en cours ou le mot précédent si le curseur se trouve à la fin d’une ligne ou une mémoire tampon de texte. Si le mot est un des noms de méthode, la description de ce nom de méthode est ajoutée au contenu Info Express.  
  
     [!code-vb[VSSDKQuickInfoTest&5;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n °&5;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  Vous devez également implémenter une méthode Dispose(), depuis <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>implémente <xref:System.IDisposable>:</xref:System.IDisposable> </xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
     [!code-vb[VSSDKQuickInfoTest n °&6;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n °&6;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implémentation d’un fournisseur Info express Source  
 Le fournisseur de la source d’Info express sert principalement à exporter en tant que composant MEF et instancier la source info Express. S’agissant d’un composant MEF, il peut importer des autres composants MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Pour implémenter un fournisseur de source info Express  
  
1.  Déclarer un fournisseur de source Info express nommé `TestQuickInfoSourceProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>et exportez-le avec une <xref:Microsoft.VisualStudio.Utilities.NameAttribute>d’info-bulle Info express « Source », un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>d’avant = « par défaut » et un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>de « texte ».</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.OrderAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
     [!code-vb[VSSDKQuickInfoTest&#7;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#7;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  Importer les deux services d’éditeur, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>et <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, en tant que propriétés de `TestQuickInfoSourceProvider`.</xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
     [!code-vb[VSSDKQuickInfoTest&#8;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#8;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  Implémentez <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>pour retourner une nouvelle `TestQuickInfoSource`.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&#9;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&9;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implementing-a-quickinfo-controller"></a>L’implémentation d’un contrôleur info Express  
 Info express contrôleurs déterminent quand Info express doit être affichée. Dans cet exemple, Info Express s’affiche lorsque le pointeur se trouve sur un mot qui correspond à un des noms de méthode. Le contrôleur Info express implémente un gestionnaire d’événements de pointage de souris qui déclenche une session info Express.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Pour implémenter un contrôleur info Express  
  
1.  Déclarez une classe qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>et nommez-le `TestQuickInfoController`.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>  
  
     [!code-vb[VSSDKQuickInfoTest&#10;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#10;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  Ajoutez des champs privés pour l’affichage de texte, les mémoires tampons de texte représentés dans l’affichage de texte, la session info Express et le fournisseur de contrôleur info Express.  
  
     [!code-vb[VSSDKQuickInfoTest&#11;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#11;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  Ajoutez un constructeur qui définit les champs et ajoute le Gestionnaire d’événements de pointage de la souris.  
  
     [!code-vb[VSSDKQuickInfoTest&#12;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#12;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  Ajoutez le Gestionnaire d’événements de pointage de souris qui déclenche la session info Express.  
  
     [!code-vb[VSSDKQuickInfoTest&#13;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#13;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>méthode afin qu’elle supprime le Gestionnaire d’événements de pointage de la souris lorsque le contrôleur est détaché de la vue de texte.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>  
  
     [!code-vb[VSSDKQuickInfoTest n °&14;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#14;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  Implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>(méthode) et le <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A>méthode en tant que méthodes vides pour cet exemple.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&#15;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#15;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implémentation d’un fournisseur Info express contrôleur  
 Le fournisseur du contrôleur Info express sert principalement à exporter en tant que composant MEF et instancier le contrôleur info Express. S’agissant d’un composant MEF, il peut importer des autres composants MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Pour implémenter le fournisseur de contrôleur info Express  
  
1.  Déclarez une classe nommée `TestQuickInfoControllerProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>et exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>de « Info-bulle Info express contrôleur » et un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>de « texte » :</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>  
  
     [!code-vb[VSSDKQuickInfoTest&#16;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb) ] 
     [!code-cs [VSSDKQuickInfoTest n°&16;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  Importation du <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>en tant que propriété.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>  
  
     [!code-vb[VSSDKQuickInfoTest n °&17;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#17;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>méthode en instanciant le contrôleur info Express.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&#18;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#18;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
 Pour tester ce code, générez la solution QuickInfoTest et exécutez-le dans l’instance expérimentale.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Pour générer et tester la solution QuickInfoTest  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3.  Créez un fichier texte et type du texte contenant les mots « Ajouter » et « soustraire ».  
  
4.  Déplacez le pointeur sur l’une des occurrences de « Ajouter ». La signature et la description de la `add` méthode doit s’afficher.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Liaison d’un Type de contenu à une Extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
