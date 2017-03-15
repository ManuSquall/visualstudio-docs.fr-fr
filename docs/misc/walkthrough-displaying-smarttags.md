---
title: "Proc&#233;dure pas &#224; pas&#160;: affichage de balises actives | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs [Kit SDK Visual Studio], nouveau - balises actives"
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# Proc&#233;dure pas &#224; pas&#160;: affichage de balises actives
Les balises actives sont déconseillées au profit des ampoules. Consultez [Procédure pas à pas : Affichage des Suggestions d'ampoule](../Topic/Walkthrough:%20Displaying%20Light%20Bulb%20Suggestions.md).  
  
 Les balises actives sont des balises sur du texte qui se développent pour afficher un ensemble d’actions. Par exemple, dans un projet Visual Basic ou Visual C\#, une ligne rouge apparaît sous un mot quand vous renommez un identificateur tel qu’un nom de variable. Lorsque vous déplacez le pointeur sur le trait de soulignement, un bouton est affiché près du pointeur. Si vous cliquez sur le bouton, une action suggérée est affichée, par exemple **Renommer IsRead en IsReady**. Si vous cliquez sur l’action, toutes les références à **IsRead** dans le projet sont renommées **IsReady**.  
  
 Même si les balises actives font partie de l’implémentation d’IntelliSense dans l’éditeur, vous pouvez implémenter des balises actives en sous\-classant <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>, puis en implémentant les interfaces <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> et <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>.  
  
> [!NOTE]
>  Vous pouvez implémenter d’autres types de balises de manière similaire.  
  
 La procédure suivante montre comment créer une balise active qui apparaît sur le mot actuel et suggère deux actions : **Convert to upper case** et **Convert to lower case**.  
  
## Composants requis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel \(SDK\) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Création d’un projet Managed Extensibility Framework \(MEF\)  
  
#### Pour créer un projet MEF  
  
1.  Créez un projet Classifieur d’éditeur. Nommez la solution `SmartTagTest`.  
  
2.  Ouvrez le fichier source.extension.vsixmanifest dans l’éditeur de manifeste VSIX.  
  
3.  Vérifiez que la section **Assets** contient un type `Microsoft.VisualStudio.MefComponent`, que la **Source** est `A project in current solution` et que **Project** a la valeur SmartTagTest.dll.  
  
4.  Enregistrez et fermez source.extension.vsixmanifest.  
  
5.  Ajoutez la référence suivante au projet et affectez la valeur `false` à **CopyLocal** :  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6.  Supprimez les fichiers de classe existants.  
  
## Implémentation d’un baliseur pour les balises actives  
  
#### Pour implémenter un baliseur pour les balises actives  
  
1.  Ajoutez un fichier de classe et nommez\-le `TestSmartTag`.  
  
2.  Ajoutez les importations suivantes :  
  
     [!code-cs[VSSDKSmartTagTest#1](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_1.cs)]
     [!code-vb[VSSDKSmartTagTest#1](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_1.vb)]  
  
3.  Ajoutez une classe nommée `TestSmartTag` qui hérite de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-cs[VSSDKSmartTagTest#2](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_2.cs)]
     [!code-vb[VSSDKSmartTagTest#2](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_2.vb)]  
  
4.  Ajoutez un constructeur pour cette classe qui appelle le constructeur de base avec un <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> égal à <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, ce qui provoquera l’affichage d’une ligne bleue sous le premier caractère d’un mot. \(Si vous utilisez <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, une ligne rouge apparaîtra sous le dernier caractère du mot.\)  
  
     [!code-cs[VSSDKSmartTagTest#3](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_3.cs)]
     [!code-vb[VSSDKSmartTagTest#3](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_3.vb)]  
  
5.  Ajoutez une classe nommée `TestSmartTagger` qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de type `TestSmartTag` et implémente <xref:System.IDisposable>.  
  
     [!code-cs[VSSDKSmartTagTest#4](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_4.cs)]
     [!code-vb[VSSDKSmartTagTest#4](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_4.vb)]  
  
6.  Ajoutez les champs privés suivants à la classe du baliseur.  
  
     [!code-cs[VSSDKSmartTagTest#5](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_5.cs)]
     [!code-vb[VSSDKSmartTagTest#5](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_5.vb)]  
  
7.  Ajoutez un constructeur qui définit les champs privés et s’abonne à l’événement <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-cs[VSSDKSmartTagTest#6](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_6.cs)]
     [!code-vb[VSSDKSmartTagTest#6](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_6.vb)]  
  
8.  Implémentez <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> pour que la balise soit créée pour le mot actuel. \(Cette méthode appelle également une méthode privée `GetSmartTagActions` qui est expliquée plus loin.\)  
  
     [!code-cs[VSSDKSmartTagTest#7](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_7.cs)]
     [!code-vb[VSSDKSmartTagTest#7](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_7.vb)]  
  
9. Ajoutez une méthode `GetSmartTagActions` pour définir les actions de la balise active. Les actions proprement dites seront implémentées lors d’étapes ultérieures.  
  
     [!code-cs[VSSDKSmartTagTest#8](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_8.cs)]
     [!code-vb[VSSDKSmartTagTest#8](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_8.vb)]  
  
10. Déclarez l’événement `SmartTagsChanged`.  
  
     [!code-cs[VSSDKSmartTagTest#9](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_9.cs)]
     [!code-vb[VSSDKSmartTagTest#9](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_9.vb)]  
  
11. Implémentez le gestionnaire d’événements `OnLayoutChanged` pour déclencher l’événement `TagsChanged`, ce qui provoque l’appel à <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>.  
  
     [!code-cs[VSSDKSmartTagTest#10](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_10.cs)]
     [!code-vb[VSSDKSmartTagTest#10](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_10.vb)]  
  
12. Implémentez la méthode <xref:System.IDisposable.Dispose%2A> pour qu’elle annule son abonnement à l’événement <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-cs[VSSDKSmartTagTest#11](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_11.cs)]
     [!code-vb[VSSDKSmartTagTest#11](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_11.vb)]  
  
## Implémentation du fournisseur de baliseur de balise active  
  
#### Pour implémenter le fournisseur de baliseur de balise active  
  
1.  Ajoutez une classe nommée `TestSmartTagTaggerProvider` qui hérite de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Exportez\-la avec un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> égal à "text", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> égal à Before\="default" et un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> égal à <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-cs[VSSDKSmartTagTest#12](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_12.cs)]
     [!code-vb[VSSDKSmartTagTest#12](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_12.vb)]  
  
2.  Importez le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> en tant que propriété.  
  
     [!code-cs[VSSDKSmartTagTest#13](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_13.cs)]
     [!code-vb[VSSDKSmartTagTest#13](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_13.vb)]  
  
3.  Implémentez la méthode <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>.  
  
     [!code-cs[VSSDKSmartTagTest#14](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_14.cs)]
     [!code-vb[VSSDKSmartTagTest#14](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_14.vb)]  
  
## Implémentation des actions de balise active  
  
#### Pour implémenter des actions de balise active  
  
1.  Créez deux classes, la première nommée `UpperCaseSmartTagAction` et la seconde nommée `LowerCaseSmartTagAction`. Ces deux classes implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction>.  
  
     [!code-cs[VSSDKSmartTagTest#15](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_15.cs)]
     [!code-vb[VSSDKSmartTagTest#15](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_15.vb)]  
  
     [!code-cs[VSSDKSmartTagTest#16](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_16.cs)]
     [!code-vb[VSSDKSmartTagTest#16](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_16.vb)]  
  
 Elles sont identiques, sauf que l’une appelle <xref:System.String.ToUpper%2A> et l’autre appelle <xref:System.String.ToLower%2A>. Les étapes suivantes traitent uniquement de la classe d’action de mise en majuscules, mais vous devez implémenter les deux classes. Appliquez les étapes d’implémentation de l’action de mise en majuscules comme modèle pour l’implémentation de l’action de mise en minuscules.  
  
1.  Déclarez un ensemble de champs privés.  
  
     [!code-cs[VSSDKSmartTagTest#17](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_17.cs)]
     [!code-vb[VSSDKSmartTagTest#17](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_17.vb)]  
  
2.  Ajoutez un constructeur qui définit les champs.  
  
     [!code-cs[VSSDKSmartTagTest#18](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_18.cs)]
     [!code-vb[VSSDKSmartTagTest#18](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_18.vb)]  
  
3.  Implémentez les propriétés comme suit.  
  
     [!code-cs[VSSDKSmartTagTest#19](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_19.cs)]
     [!code-vb[VSSDKSmartTagTest#19](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_19.vb)]  
  
4.  Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> en remplaçant le texte dans l’étendue par son équivalent en majuscules.  
  
     [!code-cs[VSSDKSmartTagTest#20](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_20.cs)]
     [!code-vb[VSSDKSmartTagTest#20](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_20.vb)]  
  
## Création et test du code  
 Pour tester ce code, générez la solution SmartTagTest et exécutez\-la dans l’instance expérimentale.  
  
#### Pour générer et tester la solution SmartTagTest  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3.  Créez un fichier texte et tapez du texte.  
  
     Une ligne bleue doit s’afficher sous la première lettre du premier mot du texte.  
  
4.  Déplacez le pointeur sur la ligne bleue.  
  
     Un bouton doit s’afficher à côté du pointeur.  
  
5.  Quand vous cliquez sur le bouton, deux suggestions d’action doivent s’afficher : **Convert to upper case** et **Convert to lower case**. Si vous cliquez sur la première action, tout le texte du mot actuel doit être converti en majuscules. Si vous cliquez sur la deuxième action, tout le texte doit être converti en minuscules.  
  
## Voir aussi  
 [Procédure pas à pas : Liaison d'un Type de contenu à une Extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)