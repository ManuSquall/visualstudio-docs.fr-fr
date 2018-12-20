---
title: Tester des applications SharePoint avec des tests codés de l’interface utilisateur
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 91d17857f1d20508041ad6c5daa90a962d6d30e6
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895442"
---
# <a name="test-sharepoint-applications-with-coded-ui-tests"></a>Tester des applications SharePoint avec des tests codés de l’interface utilisateur

L'ajout de tests codés de l'interface utilisateur dans une application SharePoint vous permet de vérifier si l'application entière, y compris ses contrôles d'interface utilisateur, fonctionne correctement. Les tests codés de l'interface utilisateur peuvent aussi valider les valeurs et la logique de l'interface utilisateur.

Pour plus d’informations sur avantages de l’utilisation de tests codés de l’interface utilisateur, consultez [Utiliser l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Spécifications**

- Visual Studio Enterprise

## <a name="create-a-coded-ui-test-for-a-sharepoint-app"></a>Créer un test codé de l’interface utilisateur pour une application SharePoint

La [création de tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md) pour vos applications SharePoint est identique à la création de tests pour d’autres types d’applications. L’enregistrement et la lecture sont pris en charge pour tous les contrôles sur l’interface de **modification web**. L'interface de sélection des catégories et des composants WebPart est constituée de contrôles Web standard.

![SharePoint, composants WebPart](../test/media/cuit_sharepoint.png)

> [!NOTE]
> Si vous enregistrez une action, validez les actions avant de générer le code. Étant donné que plusieurs comportements sont associés aux pointages de la souris, celle-ci est activée par défaut. Veillez à supprimer les pointages redondants de vos tests codés de l'interface utilisateur. Pour ce faire, modifiez le code du test ou utilisez l' [Éditeur de test codé de l'interface utilisateur](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="test-office-controls-within-a-sharepoint-app"></a>Tester des contrôles Office dans une application SharePoint

Pour activer l’automatisation de certains composants WebPart Office dans votre application SharePoint, vous devez apporter quelques modifications mineures au code.

> [!NOTE]
> Le test de contrôles Visio et PowerPoint dans une application SharePoint ne sont pas pris en charge.

### <a name="excel-cell-controls"></a>Contrôles de cellules Excel

Pour inclure les contrôles de cellules Excel, vous devez apporter des modifications dans le code du test codé de l’interface utilisateur.

> [!WARNING]
> La saisie de texte dans une cellule Excel, suivie d'une pression sur une touche de direction, ne fonctionne pas correctement. Utilisez la souris pour sélectionner des cellules.

Si vous enregistrez des actions dans une cellule vide, vous devez modifier le code en double cliquant sur la cellule puis en effectuant une opération de définition de texte. C’est nécessaire car un clic sur la cellule suivi d’une action quelconque du clavier active `textarea` dans la cellule. L'enregistrement simple de `setvalue` dans la cellule vide recherche `editbox` qui n'est pas présent jusqu'à ce qu'un clic soit effectué sur la cellule. Exemple :

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
    ``

## See also

- [Use UI automation to test your code](../test/use-ui-automation-to-test-your-code.md)
- [Create SharePoint solutions](../sharepoint/create-sharepoint-solutions.md)
- [Verify and debug SharePoint code](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Profile the performance of SharePoint applications](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)
