---
title: Test des applications SharePoint 2010 avec des tests codés de l’interface utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: 32
ms.author: gewarren
manager: douge
ms.openlocfilehash: 346362a6812882bd795b6180ac735e51f13e3530
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303756"
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Test des applications SharePoint 2010 avec des tests codés de l'interface utilisateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'ajout de tests codés de l'interface utilisateur dans une application SharePoint vous permet de vérifier si l'application entière, y compris ses contrôles d'interface utilisateur, fonctionne correctement. Les tests codés de l'interface utilisateur peuvent aussi valider les valeurs et la logique de l'interface utilisateur.  
  
 **Spécifications**  
  
-   Visual Studio Enterprise  
  
## <a name="what-else-should-i-know-about-coded-ui-tests"></a>Que dois-je savoir d'autre sur les tests codés de l'interface utilisateur ?  
 Pour en savoir plus sur les avantages de l’utilisation de tests codés de l’interface utilisateur, consultez [Utiliser UI Automation pour tester votre code](../test/use-ui-automation-to-test-your-code.md) et [Testing for Continuous Delivery with Visual Studio 2012 – Chapter 5 Automating System Tests (Test de la livraison continue avec Visual Studio 2012 - Chapitre 5 Automatisation des tests système)](http://go.microsoft.com/fwlink/?LinkID=255196).  
  
 **Notes**  
  
-   ![Prérequis](../test/media/prereq.png "Prereq") Les tests codés de l’interface utilisateur pour les applications SharePoint ne sont pris en charge qu’avec SharePoint 2010.  
  
-   ![Prérequis](../test/media/prereq.png "Prereq") Les contrôles pour Visio et PowerPoint 2010 ne sont pas pris en charge dans votre application SharePoint.  
  
## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>Créer un test d'interface utilisateur codé pour votre application SharePoint  
 La[création de tests codés de l'interface utilisateur](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) pour vos applications SharePoint 2010 est identique à la création de tests pour d'autres types d'applications. L'enregistrement et la lecture sont pris en charge pour tous les contrôles sur l'interface de modification Web. L'interface de sélection des catégories et des composants WebPart est constituée de contrôles Web standard.  
  
 ![Composants WebPart SharePoint](../test/media/cuit-sharepoint.png "CUIT_SharePoint")  
  
> [!NOTE]
>  Si vous enregistrez une action, validez les actions avant de générer le code. Étant donné que plusieurs comportements sont associés aux pointages de la souris, celle-ci est activée par défaut. Veillez à supprimer les pointages redondants de vos tests codés de l'interface utilisateur. Pour ce faire, modifiez le code du test ou utilisez l' [Éditeur de test codé de l'interface utilisateur](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>Inclusion du test des contrôles Office 2010 dans votre application SharePoint  
 Pour activer l'automatisation de certains composants WebPart Office 2010 dans votre application SharePoint, vous devez apporter des modifications de code mineures.  
  
> [!WARNING]
>  Les contrôles pour Visio et PowerPoint 2010 ne sont pas pris en charge.  
  
### <a name="excel-2010-cell-controls"></a>Contrôles des cellules Excel 2010  
 Pour inclure les contrôles de cellules Excel, vous devez apporter des modifications dans le code du test codé de l'interface utilisateur.  
  
> [!WARNING]
>  La saisie de texte dans une cellule Excel, suivie d'une pression sur une touche de direction, ne fonctionne pas correctement. Utilisez la souris pour sélectionner des cellules.  
  
 Si vous enregistrez des actions dans une cellule vide, vous devez modifier le code en double cliquant sur la cellule puis en effectuant une opération de définition de texte. Cela est nécessaire car un clic sur la cellule, suivi d'une action du clavier, active `textarea` dans la cellule. L'enregistrement simple de `setvalue` dans la cellule vide recherche `editbox` qui n'est pas présent jusqu'à ce qu'un clic soit effectué sur la cellule. Exemple :  
  
```csharp  
Mouse.DoubliClick(uiItemCell,new Point(31,14));  
uiGridKeyboardInputEdit.Text=value;  
```  
  
 Si vous enregistrez des actions dans une cellule qui n’est pas vide, l’enregistrement est un peu plus compliqué, car le temps que vous ajoutiez du texte dans une cellule, un nouveau contrôle \<div> est ajouté en tant qu’enfant de la cellule. Le nouveau contrôle \<div> contient le texte que vous venez d’entrer. L’enregistreur doit enregistrer les actions sur le nouveau contrôle \<div>, mais il ne le peut pas, car le nouveau contrôle \<div> n’existe pas tant que le test n’est pas activé. Vous devez apporter manuellement les modifications de code suivantes pour résoudre ce problème.  
  
1.  Accédez à l'initialisation des cellules et définissez `RowIndex` et `ColumnIndex` comme des propriétés principales :  
  
    ```csharp  
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";   
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";  
    ```  
  
2.  Recherchez l'enfant `HtmlDiv` de la cellule :  
  
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
  
3.  Ajoutez du code pour une action de double-clic de la souris sur `HtmlDiv`:  
  
    ```csharp  
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )  
    ```  
  
4.  Ajoutez du code pour définir le texte sur `TextArea`:  
  
    ```csharp  
    uIGridKeyboardInputEdit.Text = value; }  
    ```  
  
## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>Activation du test codé de l'interface utilisateur des composants WebPart Silverlight dans votre application SharePoint 2010  
 Les tests Silverlight ne sont pas pris en charge dans Visual Studio 2012 et versions ultérieures. Mais, si vous voulez tester les composants WebPart Silverlight dans votre application SharePoint 2010, vous pouvez installer un plug-in Silverlight distinct à partir de la galerie Visual Studio.  
  
#### <a name="setting-up-your-machine"></a>Configuration de votre ordinateur  
  
1.  Assurez-vous de disposer de Visual Studio 2012.1 ou version ultérieure.  
  
2.  Installez [Microsoft Visual Studio UI Test Plugin for Silverlight](http://visualstudiogallery.msdn.microsoft.com/28312a61-9451-451a-990c-c9929b751eb4).  
  
3.  Installez [Fiddler](http://www.fiddler2.com/fiddler2/). Il s'agit simplement d'un outil qui capture et enregistre le trafic HTTP.  
  
4.  Téléchargez le [projet fiddlerXap](http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-components-postattachments/00-10-36-48-70/FiddlerXapProxy.zip). Décompressez-le, générez-le, puis exécutez le script "CopySLHelper.bat" pour installer la DLL du programme d'assistance qui est requise pour analyser les composants WebPart Silverlight lorsque vous utilisez l'outil Fiddler.  
  
 Après avoir configuré votre ordinateur, vous pouvez démarrer le test de votre application SharePoint 2010 avec des composants WebPart Silverlight en procédant comme suit :  
  
#### <a name="testing-silverlight-web-parts"></a>Test des composants WebPart Silverlight  
  
1.  Démarrez Fiddler.  
  
2.  Effacez le cache du navigateur. Cela est nécessaire car le fichier XAP, qui contient la DLL du programme d'assistance d'UI Automation de Silverlight, est généralement mis en cache. Nous devons nous assurer que le fichier XAP modifié est utilisé. Pour cela, nous désactivons le cache du navigateur.  
  
3.  Ouvrez la page Web.  
  
4.  Démarrez l'enregistreur et générez le code comme vous le feriez pour un test normal de l'application Web.  
  
5.  Vous devez confirmer que le code généré fait référence au fichier Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll.  
  
     Pour plus d’informations, consultez [UI Testing SharePoint 2010 with Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
## <a name="external-resources"></a>Ressources externes  
  
### <a name="blogs"></a>Blogs  
 [UI Testing SharePoint 2010 with Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
 [Understanding the Search logic for Silverlight controls in Coded UI Test](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/understanding-the-search-logic-for-silverlight-controls-in-coded-ui-test.aspx)  
  
 [Fetching Property of a Silverlight control](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/fetching-property-of-a-silverlight-control.aspx)  
  
 [Content Index for Coded UI Test](http://blogs.msdn.com/b/mathew_aniyan/archive/2010/02/11/content-index-for-coded-ui-test.aspx)  
  
### <a name="guidance"></a>Conseils  
 [test de la livraison continue avec Visual Studio 2012 – Chapitre 5 Automating System Tests](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="forum"></a>Forum  
 [Blog Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=254496)  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser UI Automation pour tester votre code](../test/use-ui-automation-to-test-your-code.md)   
 [Test de performances web et tests de charge des applications SharePoint 2010 et 2013](http://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54)   
 [Créer des solutions SharePoint](http://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631)   
 [Vérification et débogage du code SharePoint](http://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c)   
 [Génération et débogage de solutions SharePoint](http://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae)   
 [Profilage des performances des applications SharePoint](http://msdn.microsoft.com/library/61ae02e7-3f37-4230-bae1-54a498c2fae8)



