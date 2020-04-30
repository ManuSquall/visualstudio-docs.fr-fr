---
title: Test des applications SharePoint 2010 avec des tests codés de l’interface utilisateur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0ec4c0a9594202b6755500d683c426238264aec3
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586972"
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Test des applications SharePoint 2010 avec des tests codés de l'interface utilisateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'ajout de tests codés de l'interface utilisateur dans une application SharePoint vous permet de vérifier si l'application entière, y compris ses contrôles d'interface utilisateur, fonctionne correctement. Les tests codés de l'interface utilisateur peuvent aussi valider les valeurs et la logique de l'interface utilisateur.

 **Configuration requise**

- Visual Studio Enterprise

## <a name="what-else-should-i-know-about-coded-ui-tests"></a>Que dois-je savoir d'autre sur les tests codés de l'interface utilisateur ?
 Pour en savoir plus sur les avantages de l’utilisation de tests codés de l’interface utilisateur, consultez [Utiliser UI Automation pour tester votre code](../test/use-ui-automation-to-test-your-code.md) et [Testing for Continuous Delivery with Visual Studio 2012 – Chapter 5 Automating System Tests (Test de la livraison continue avec Visual Studio 2012 - Chapitre 5 Automatisation des tests système)](https://msdn.microsoft.com/library/jj159335.aspx).

 **Remarques**

- ![Prérequis](../test/media/prereq.png "PREREQ") Les tests codés de l’interface utilisateur pour les applications SharePoint sont pris en charge uniquement avec SharePoint 2010.

- ![Prérequis](../test/media/prereq.png "PREREQ") La prise en charge des contrôles Visio et PowerPoint 2010 dans votre application SharePoint n’est pas prise en charge.

## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>Créer un test d'interface utilisateur codé pour votre application SharePoint
 La[création de tests codés de l'interface utilisateur](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) pour vos applications SharePoint 2010 est identique à la création de tests pour d'autres types d'applications. L'enregistrement et la lecture sont pris en charge pour tous les contrôles sur l'interface de modification Web. L'interface de sélection des catégories et des composants WebPart est constituée de contrôles Web standard.

 ![Composants WebPart SharePoint](../test/media/cuit-sharepoint.png "CUIT_SharePoint")

> [!NOTE]
> Si vous enregistrez une action, validez les actions avant de générer le code. Étant donné que plusieurs comportements sont associés aux pointages de la souris, celle-ci est activée par défaut. Veillez à supprimer les pointages redondants de vos tests codés de l'interface utilisateur. Pour ce faire, modifiez le code du test ou utilisez l' [Éditeur de test codé de l'interface utilisateur](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>Inclusion du test des contrôles Office 2010 dans votre application SharePoint
 Pour activer l'automatisation de certains composants WebPart Office 2010 dans votre application SharePoint, vous devez apporter des modifications de code mineures.

> [!WARNING]
> Les contrôles pour Visio et PowerPoint 2010 ne sont pas pris en charge.

### <a name="excel-2010-cell-controls"></a>Contrôles des cellules Excel 2010
 Pour inclure les contrôles de cellules Excel, vous devez apporter des modifications dans le code du test codé de l'interface utilisateur.

> [!WARNING]
> La saisie de texte dans une cellule Excel, suivie d'une pression sur une touche de direction, ne fonctionne pas correctement. Utilisez la souris pour sélectionner des cellules.

 Si vous enregistrez des actions dans une cellule vide, vous devez modifier le code en double cliquant sur la cellule puis en effectuant une opération de définition de texte. Cela est nécessaire car un clic sur la cellule, suivi d'une action du clavier, active `textarea` dans la cellule. L'enregistrement simple de `setvalue` dans la cellule vide recherche `editbox` qui n'est pas présent jusqu'à ce qu'un clic soit effectué sur la cellule. Par exemple :

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

 Si vous enregistrez des actions dans une cellule qui n’est pas vide, l’enregistrement est un peu plus compliqué, car le temps que vous ajoutiez du texte dans une cellule, un nouveau contrôle \<div> est ajouté en tant qu’enfant de la cellule. Le nouveau contrôle \<div> contient le texte que vous venez d’entrer. L’enregistreur doit enregistrer les actions sur le nouveau contrôle \<div>, mais il ne le peut pas, car le nouveau contrôle \<div> n’existe pas tant que le test n’est pas activé. Vous devez apporter manuellement les modifications de code suivantes pour résoudre ce problème.

1. Accédez à l'initialisation des cellules et définissez `RowIndex` et `ColumnIndex` comme des propriétés principales :

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. Recherchez l'enfant `HtmlDiv` de la cellule :

    ```csharp
    private UITestControl getControlToDoubleClick(HtmlCell cell)
    {
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;
         HtmlDiv pane = new HtmlDiv(cell);
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;
         // Class is an important property in finding pane
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";
         UITestControlCollection panes = pane.FindMatchingControls();
         return panes[0];
    }

    ```

3. Ajoutez du code pour une action de double-clic de la souris sur `HtmlDiv`:

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. Ajoutez du code pour définir le texte sur `TextArea`:

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ```

## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>Activation du test codé de l'interface utilisateur des composants WebPart Silverlight dans votre application SharePoint 2010
 Les tests Silverlight ne sont pas pris en charge dans Visual Studio 2012 et versions ultérieures. Mais, si vous voulez tester les composants WebPart Silverlight dans votre application SharePoint 2010, vous pouvez installer un plug-in Silverlight distinct à partir de la galerie Visual Studio.

#### <a name="setting-up-your-machine"></a>Configuration de votre ordinateur

1. Assurez-vous de disposer de Visual Studio 2012.1 ou version ultérieure.

2. Installez [Microsoft Visual Studio UI Test Plugin for Silverlight](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudioUITestPluginforSilverlight).

3. Installez [Fiddler](http://www.fiddler2.com/fiddler2/). Il s'agit simplement d'un outil qui capture et enregistre le trafic HTTP.

4. Téléchargez le [projet fiddlerXap](https://40jajy3iyl373v772m19fybm-wpengine.netdna-ssl.com/wp-content/uploads/sites/6/2019/02/FiddlerXapProxy.zip). Décompressez-le, générez-le, puis exécutez le script "CopySLHelper.bat" pour installer la DLL du programme d'assistance qui est requise pour analyser les composants WebPart Silverlight lorsque vous utilisez l'outil Fiddler.

   Après avoir configuré votre ordinateur, vous pouvez démarrer le test de votre application SharePoint 2010 avec des composants WebPart Silverlight en procédant comme suit :

#### <a name="testing-silverlight-web-parts"></a>Test des composants WebPart Silverlight

1. Démarrez Fiddler.

2. Effacez le cache du navigateur. Cela est nécessaire car le fichier XAP, qui contient la DLL du programme d'assistance d'UI Automation de Silverlight, est généralement mis en cache. Nous devons nous assurer que le fichier XAP modifié est utilisé. Pour cela, nous désactivons le cache du navigateur.

3. Ouvrez la page Web.

4. Démarrez l'enregistreur et générez le code comme vous le feriez pour un test normal de l'application Web.

5. Vous devez confirmer que le code généré fait référence au fichier Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll.

     Pour plus d’informations, consultez [UI Testing SharePoint 2010 with Visual Studio 2012](https://devblogs.microsoft.com/devops/ui-testing-sharepoint-2010-with-visual-studio-2012/)

## <a name="external-resources"></a>Ressources externes

### <a name="blogs"></a>Blogs
 [UI Testing SharePoint 2010 with Visual Studio 2012](https://devblogs.microsoft.com/devops/ui-testing-sharepoint-2010-with-visual-studio-2012/)

 [Understanding the Search logic for Silverlight controls in Coded UI Test](https://tapas-techsnips.blogspot.com/)

 [Fetching Property of a Silverlight control](https://tapas-techsnips.blogspot.com/)

 [Content Index for Coded UI Test](https://blogs.msdn.microsoft.com/mathew_aniyan/2013/02/18/content-index-for-coded-ui-test/)

### <a name="guidance"></a>Assistance
 [Test de la livraison continue avec Visual Studio 2012 – chapitre 5 automatisation des tests système](https://msdn.microsoft.com/library/jj159335.aspx)

### <a name="forum"></a>Forum
 [Blog Visual Studio ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)

## <a name="see-also"></a> Voir aussi
 [Utiliser UI Automation pour tester votre code](../test/use-ui-automation-to-test-your-code.md) [performances Web et test de charge des applications sharepoint 2010 et 2013](https://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54) [créer des solutions SharePoint](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631) [vérification et débogage de code SharePoint](https://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c) [création et débogage de solutions SharePoint](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) [profilage des performances des applications SharePoint](https://msdn.microsoft.com/library/61ae02e7-3f37-4230-bae1-54a498c2fae8)
