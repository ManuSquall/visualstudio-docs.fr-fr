---
title: 'Procédure pas à pas : Affichage de balises actives | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - smart tags
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
manager: douge
ms.openlocfilehash: 84736e4cb4212b912d87caa7849a37bbc726ffdd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291016"
---
# <a name="walkthrough-displaying-smarttags"></a>Procédure pas à pas : affichage de balises actives
Les balises actives sont déconseillées au profit des ampoules. Consultez [Walkthrough: Displaying Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
 Les balises actives sont des balises sur du texte qui se développent pour afficher un ensemble d’actions. Par exemple, dans un projet Visual Basic ou Visual C#, une ligne rouge apparaît sous un mot quand vous renommez un identificateur tel qu’un nom de variable. Lorsque vous déplacez le pointeur sur le trait de soulignement, un bouton est affiché près du pointeur. Si vous cliquez sur le bouton, une action suggérée est affichée, par exemple **Renommer IsRead en IsReady**. Si vous cliquez sur l’action, toutes les références à **IsRead** dans le projet sont renommées **IsReady**.  
  
 Même si les étiquettes actives font partie de l’implémentation d’IntelliSense dans l’éditeur, vous pouvez implémenter des étiquettes actives en sous-classant <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>, puis en implémentant les interfaces <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> et <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>.  
  
> [!NOTE]
>  Vous pouvez implémenter d’autres types de balises de manière similaire.  
  
 La procédure suivante montre comment créer une balise active qui apparaît sur le mot actuel et suggère deux actions : **Convert to upper case** et **Convert to lower case**.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Création d’un projet Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF  
  
1.  Créez un projet Classifieur d’éditeur. Nommez la solution `SmartTagTest`.  
  
2.  Ouvrez le fichier source.extension.vsixmanifest dans l’éditeur de manifeste VSIX.  
  
3.  Vérifiez que la section **Assets** contient un type `Microsoft.VisualStudio.MefComponent` , que la **Source** est `A project in current solution`et que **Project** a la valeur SmartTagTest.dll.  
  
4.  Enregistrez et fermez source.extension.vsixmanifest.  
  
5.  Ajoutez la référence suivante au projet et affectez la valeur **à** CopyLocal `false`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6.  Supprimez les fichiers de classe existants.  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>Implémentation d’un baliseur pour les balises actives  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>Pour implémenter un baliseur pour les balises actives  
  
1.  Ajoutez un fichier de classe et nommez-le `TestSmartTag`.  
  
2.  Ajoutez les importations suivantes :  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3.  Ajoutez une classe nommée `TestSmartTag` qui hérite de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4.  Ajoutez un constructeur pour cette classe qui appelle le constructeur de base avec un <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> égal à <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, ce qui provoquera l’affichage d’une ligne bleue sous le premier caractère d’un mot. (Si vous utilisez <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, une ligne rouge apparaîtra sous le dernier caractère du mot.)  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5.  Ajoutez une classe nommée `TestSmartTagger` qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de type `TestSmartTag` et implémente <xref:System.IDisposable>.  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6.  Ajoutez les champs privés suivants à la classe du baliseur.  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7.  Ajoutez un constructeur qui définit les champs privés et s’abonne à l’événement <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8.  Implémentez <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> pour que la balise soit créée pour le mot actuel. (Cette méthode appelle également une méthode privée `GetSmartTagActions` qui est expliquée plus loin.)  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. Ajoutez une méthode `GetSmartTagActions` pour définir les actions de la balise active. Les actions proprement dites seront implémentées lors d’étapes ultérieures.  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. Déclarez l’événement `SmartTagsChanged`.  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. Implémentez le gestionnaire d’événements `OnLayoutChanged` pour déclencher l’événement `TagsChanged`, ce qui provoque l’appel à <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>.  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. Implémentez la méthode <xref:System.IDisposable.Dispose%2A> pour qu’elle annule son abonnement à l’événement <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>Implémentation du fournisseur de baliseur de balise active  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>Pour implémenter le fournisseur de baliseur de balise active  
  
1.  Ajoutez une classe nommée `TestSmartTagTaggerProvider` qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Exportez-la avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> égal à "text", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> égal à Before="default" et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> égal à <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2.  Importez le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> en tant que propriété.  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3.  Implémentez la méthode <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>.  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>Implémentation des actions de balise active  
  
#### <a name="to-implement-smart-tag-actions"></a>Pour implémenter des actions de balise active  
  
1.  Créez deux classes, la première nommée `UpperCaseSmartTagAction` et la seconde nommée `LowerCaseSmartTagAction`. Ces deux classes implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction>.  
  
     [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
     [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
     [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
     [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
 Elles sont identiques, sauf que l’une appelle <xref:System.String.ToUpper%2A> et l’autre appelle <xref:System.String.ToLower%2A>. Les étapes suivantes traitent uniquement de la classe d’action de mise en majuscules, mais vous devez implémenter les deux classes. Appliquez les étapes d’implémentation de l’action de mise en majuscules comme modèle pour l’implémentation de l’action de mise en minuscules.  
  
1.  Déclarez un ensemble de champs privés.  
  
     [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
     [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
2.  Ajoutez un constructeur qui définit les champs.  
  
     [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
     [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
3.  Implémentez les propriétés comme suit.  
  
     [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
     [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
4.  Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> en remplaçant le texte dans l’étendue par son équivalent en majuscules.  
  
     [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
     [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
 Pour tester ce code, générez la solution SmartTagTest et exécutez-la dans l’instance expérimentale.  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>Pour générer et tester la solution SmartTagTest  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3.  Créez un fichier texte et tapez du texte.  
  
     Une ligne bleue doit s’afficher sous la première lettre du premier mot du texte.  
  
4.  Déplacez le pointeur sur la ligne bleue.  
  
     Un bouton doit s’afficher à côté du pointeur.  
  
5.  Quand vous cliquez sur le bouton, deux suggestions d’action doivent s’afficher : **Convert to upper case** et **Convert to lower case**. Si vous cliquez sur la première action, tout le texte du mot actuel doit être converti en majuscules. Si vous cliquez sur la deuxième action, tout le texte doit être converti en minuscules.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)