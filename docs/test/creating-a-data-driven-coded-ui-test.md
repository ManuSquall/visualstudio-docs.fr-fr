---
title: Tutoriel de test codé de l’interface utilisateur piloté par les données
description: Découvrez comment utiliser des tests codés de l’interface utilisateur pilotés par les données pour tester différentes conditions en exécutant plusieurs fois vos tests avec des valeurs de paramètre différentes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, data-driven
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9c4deb02bea8bf6e3dc3615ba9c5f0eddc6c877
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442675"
---
# <a name="create-a-data-driven-coded-ui-test"></a>Créer un test codé de l'interface utilisateur piloté par les données

Pour tester différentes conditions, vous pouvez exécuter vos tests à plusieurs reprises avec différentes valeurs de paramètre. Les tests codés de l'interface utilisateur pilotés par les données sont un moyen pratique pour cela. Vous définissez des valeurs de paramètre dans une source de données et chaque ligne de la source de données est une itération du test codé de l'interface utilisateur. Le résultat global du test repose sur le résultat de toutes les itérations. Par exemple, si une itération de test échoue, le résultat global du test est un échec.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Configuration requise**

- Visual Studio Enterprise
- Composant Test codé de l’interface utilisateur

## <a name="create-a-test-project"></a>Créer un projet de test

Cet exemple crée un test codé de l'interface utilisateur qui s'exécute sur l'application Calculatrice de Windows. Il additionne deux nombres et utilise une assertion pour valider que la somme est correcte. Ensuite, l'assertion et les valeurs de paramètre des deux nombres sont codées pour devenir pilotées par les données et stockées dans un fichier de valeurs séparées par des virgules (.*csv*).

### <a name="step-1---create-a-coded-ui-test"></a>Étape 1 : Créer un test codé de l'interface utilisateur

1. Crée un projet.

    ![Créer un projet de test d'interface utilisateur codé](../test/media/cuit_datadriven_.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle de **projet de test codé de l’interface utilisateur** , vous devez [installer le composant de test codé de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

2. Choisissez **d’enregistrer les actions**.

    ![Choisir d'enregistrer les actions](../test/media/cuit_datadriven_generatecodedialog.png)

3. Ouvrez l'application Calculatrice et démarrez l'enregistrement du test.

    ![Enregistrer les actions](../test/media/cuit_datadriven_cuitbuilder.png)

4. Additionnez 1 et 2, interrompez l'enregistreur et générez la méthode de test. Plus tard, nous allons remplacer les valeurs de cette entrée utilisateur par les valeurs d’un fichier de données.

    ![Générer une méthode de test](../test/media/cuit_datadriven_cuitbuildergencode.png)

    Fermez le générateur de test. La méthode est ajoutée au test :

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       // To generate code for this test, select "Generate Code for Coded UI Test"
       // from the shortcut menu and select one of the menu items.
       this.UIMap.AddNumbers();
   }
   ```

5. Utilisez la méthode `AddNumbers()` pour vérifier que le test s'exécute. Placez le curseur dans la méthode de test illustrée ci-dessus, ouvrez le menu contextuel (clic droit) et choisissez **Exécuter les tests**. (Raccourci clavier : **CTRL** + **R**,**T**).

    Le résultat du test qui indique si le test a réussi ou a échoué apparaît dans la fenêtre **Explorateur de tests**. Pour ouvrir la fenêtre Explorateur de tests, dans le menu **Test**, choisissez **Fenêtres**, puis **Explorateur de tests**.

6. Dans la mesure où une source de données peut également être utilisée pour les valeurs de paramètre d’assertion (qui sont utilisées par le test pour vérifier les valeurs attendues), ajoutons une assertion pour confirmer que la somme des deux nombres est correcte. Placez le curseur dans la méthode de test illustrée ci-dessus, ouvrez le menu contextuel (clic droit) et choisissez **Générer le code du test codé de l’interface utilisateur**, puis **Utiliser le générateur de tests codés de l’interface utilisateur**.

    Mappez le contrôle de texte dans la calculatrice qui affiche la somme.

    ![Mapper le contrôle de texte de l'interface utilisateur](../test/media/cuit_datadriven_addassertion.png)

7. Ajoutez une assertion qui vérifie que la valeur de la somme est correcte. Choisissez la propriété **DisplayText** dont la valeur est **3**, puis choisissez **Ajouter une assertion**. Utilisez le comparateur **AreEqual** et vérifiez que la valeur de comparaison est **3**.

    ![Configurer l'assertion](../test/media/cuit_datadriven_builderaddassertion2.png)

8. Après avoir configuré l'assertion, générez à nouveau le code à partir du générateur. Une nouvelle méthode pour la validation est ainsi créée.

    ![Générer la méthode d'assertion](../test/media/cuit_datadriven_assertiongencode.png)

    Étant donné que la méthode `ValidateSum` valide les résultats de la méthode `AddNumbers`, déplacez-la vers le bas du bloc de code.

   ```csharp
   public void CodedUITestMethod1()
   {
       this.UIMap.AddNumbers();
       this.UIMap.ValidateSum();
   }
   ```

9. Vérifiez que le test s'exécute à l'aide de la méthode `ValidateSum()`. Placez le curseur dans la méthode de test illustrée ci-dessus, ouvrez le menu contextuel (clic droit) et choisissez **Exécuter les tests**. (Raccourci clavier : **CTRL** + **R**,**T**).

     À ce stade, toutes les valeurs de paramètre sont définies dans leurs méthodes en tant que constantes. Ensuite, nous allons créer un jeu de données pour créer notre test piloté par les données.

### <a name="step-2---create-a-data-set"></a>Étape 2 : créer un jeu de données

1. Ajoutez un fichier texte au projet dataDrivenSample nommé *data.csv*.

     ![Ajouter un fichier de valeurs séparées par une virgule au projet](../test/media/cuit_datadriven_addcsvfile.png)

2. Renseignez le fichier .*csv* avec les données suivantes :

    |Num1|Num2|Somme|
    |-|-|-|
    |3|4|7|
    |5|6|11|
    |6|8|14|

     Après avoir ajouté les données, le fichier doit ressembler à ce qui suit :

     ![Renseigner le fichier .csv avec des données](../test/media/cuit_datadriven_adddatatocsvfile.png)

3. Il est important d’enregistrer le fichier .*csv* en utilisant le bon encodage. Dans le menu **Fichier**, choisissez **Options d’enregistrement avancées**, puis choisissez l’encodage **Unicode (UTF-8 sans signature) - Page de codes 65001**.

4. Le fichier .*csv* doit être copié dans le répertoire de sortie, sans quoi le test ne peut pas s’exécuter. Utilisez la fenêtre **Propriétés** pour le copier.

     ![Déployer le fichier .csv](../test/media/cuit_datadriven_deploycsvfile.png)

     Maintenant que nous avons créé le jeu de données, nous allons lier les données au test.

### <a name="step-3---add-data-source-binding"></a>Étape 3 : ajouter une liaison de source de données

1. Pour lier la source de données, ajoutez un attribut `DataSource` dans l'attribut `[TestMethod]` existant qui se trouve juste au-dessus de la méthode de test.

    ```csharp
    [DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSum();
    }
    ```

     La source de données est maintenant disponible pour cette méthode de test.

    > [!TIP]
    > Consultez les [exemples d’attributs de source de données](#CreateDataDrivenCUIT_QA_DataSourceAttributes) dans la section des questions et réponses sur l’utilisation d’autres types de source de données tels que XML, SQL Express et Excel.

2. Exécutez le test.

     Notez que le test s'exécute via trois itérations. En effet, la source de données qui a été liée contient trois lignes de données. En revanche, vous pouvez remarquer que le test utilise toujours les valeurs de paramètre constantes et additionne 1 + 2 avec une somme de 3 à chaque fois.

     Ensuite, nous allons configurer le test pour utiliser les valeurs incluses dans le fichier de la source de données.

### <a name="step-4---use-the-data-in-the-coded-ui-test"></a>Étape 4 : utiliser les données dans le test codé de l’interface utilisateur

1. Ajoutez `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` au début du fichier *CodedUITest.cs* :

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text.RegularExpressions;
    using System.Windows.Input;
    using System.Windows.Forms;
    using System.Drawing;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UnitTesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    ```

2. Ajoutez `TestContext.DataRow[]` dans la méthode `CodedUITestMethod1()` qui va appliquer les valeurs de la source de données. Les valeurs de la source de données se substituent aux constantes affectées aux contrôles UIMap en utilisant les contrôles `SearchProperties` :

   ```csharp
   public void CodedUITestMethod1()
   {
       this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();
       this.UIMap.UICalculatorWindow.UIItemWindow2.UIItem2Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num2"].ToString();
       this.UIMap.AddNumbers();
       this.UIMap.ValidateSumExpectedValues.UIItem3TextDisplayText = TestContext.DataRow["Sum"].ToString();
       this.UIMap.ValidateSum();
    }
    ```

     Pour déterminer vers quelles propriétés de recherche coder les données, utilisez l'éditeur de test codé de l'interface utilisateur.

    - Ouvrez le fichier *UIMap.uitest*.

         ![Ouvrir l'éditeur de test d'interface utilisateur codé](../test/media/cuit_datadriven_opentesteditor.png)

    - Choisissez l'action d'interface utilisateur et observez le mappage des contrôles d'interface utilisateur correspondant. Remarquez que le mappage correspond au code, par exemple, `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button`.

         ![Utiliser l'éditeur de test d'interface utilisateur codé pour faciliter le codage](../test/media/cuit_datadriven_testeditor.png)

    - Dans la fenêtre **Propriétés**, ouvrez **Propriétés de recherche**. La valeur **Nom** des propriétés de recherche est celle manipulée dans le code à l’aide de la source de données. Par exemple, `SearchProperties` se voit attribué les valeurs de la première colonne de chaque ligne de données : `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();`. Pour les trois itérations, ce test va remplacer la valeur **Nom** de la propriété de recherche par 3, puis 5 et enfin 6.

         ![Utiliser les propriétés de recherche pour faciliter le codage](../test/media/cuit_datadriven_searchproperties.png)

3. Enregistrez la solution.

### <a name="step-5---run-the-data-driven-test"></a>Étape 5 : exécuter le test piloté par les données

Vérifiez que le test est maintenant piloté par les données en l'exécutant de nouveau.

Vous devez voir le test s'exécuter via trois itérations à l'aide des valeurs incluses dans le fichier .*csv*. La validation doit également fonctionner et le test doit s’afficher comme réussi dans l’Explorateur de tests.

## <a name="q--a"></a>Questions et réponses

### <a name="what-are-the-data-source-attributes-for-other-data-source-types-such-as-sql-express-or-xml"></a><a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a> Quels sont les attributs de la source de données pour d’autres types de source de données, comme SQL Express ou XML ?

**R :** Vous pouvez utiliser les exemples de chaînes de source de données dans le tableau ci-dessous en les copiant dans votre code et en effectuant les personnalisations nécessaires.

**Types de source de données et attributs**

- CSV

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`

- Excel

     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`

- Cas de test dans Team Foundation Server

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`

- XML

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`

- SQL Express

     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Q : Pourquoi ne puis-je pas modifier le code du fichier UIMap.Designer ?

**R :** Toutes les modifications de code que vous apportez dans le fichier *UIMapDesigner.cs* sont remplacées chaque fois que vous générez du code à l’aide du générateur de test codé de l’interface utilisateur UIMap. Dans cet exemple et dans la plupart des cas, les modifications de code nécessaires pour permettre à un test d’utiliser une source de données peuvent être apportées au fichier de code source du test (c’est-à-dire, *CodedUITest1.cs*).

Si vous devez modifier une méthode enregistrée, vous devez la copier dans le fichier *UIMap.cs* et la renommer. Le fichier *UIMap.cs* peut être utilisé pour substituer les méthodes et les propriétés dans le fichier *UIMapDesigner.cs* . Vous devez supprimer la référence à la méthode d’origine dans le fichier Encoded *UITest.cs* et la remplacer par le nom de la méthode renommée.

## <a name="see-also"></a>Voir aussi

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Utiliser UI Automation pour tester votre code](../test/use-ui-automation-to-test-your-code.md)
- [Créer des tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md)
- [Meilleures pratiques pour les tests codés de l’interface utilisateur](../test/best-practices-for-coded-ui-tests.md)
- [Configurations et plateformes prises en charge pour les tests codés de l’interface utilisateur et les enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
