---
title: "Comment&#160;: cr&#233;er un test unitaire pilot&#233; par des donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.test.testresults.unittest.datadriven"
  - "vs.test.testresults.unittest.datadriven.failure"
helpviewer_keywords: 
  - "tests unitaires, exécuter"
  - "tests unitaires, pilotés par des données"
  - "tests unitaires pilotés par des données"
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 33
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 33
---
# Comment&#160;: cr&#233;er un test unitaire pilot&#233; par des donn&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

À l'aide de l'infrastructure de test unitaire Microsoft pour le code managé, vous pouvez installer une méthode de test unitaire pour récupérer des valeurs utilisées dans la méthode de test d'une source de données.  La méthode est exécutée successivement pour chaque ligne de la source de données, qui facilite de tester diverses entrées à l'aide d'une méthode unique.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [La méthode testée](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
-   [Création d'une source de données](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
-   [TestContext ajouter un à la classe de test](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
-   [Écrire la méthode de test](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
    -   [Spécifier le DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
    -   [Utilisation TestContext.DataRow pour accéder aux données](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
-   [Exécuter les résultats des tests et d'affichage](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
 Créer un test unitaire piloté par des données implique les étapes suivantes :  
  
1.  Créez une source de données qui contient les valeurs que vous utilisez dans la méthode de test.  La source de données peut être tout type qui est stocké sur l'ordinateur qui exécute le test.  
  
2.  Ajoutez un champ privé d' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> et une propriété publique d' `TestContext` à la classe de test.  
  
3.  Créez une méthode de test unitaire et ajoutez un attribut d' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> lui.  
  
4.  Utilisez la propriété d'indexeur d' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> pour récupérer les valeurs que vous utilisez dans un test.  
  
##  <a name="BKMK_The_method_under_test"></a> La méthode testée  
 Par exemple, laissez nous supposent que nous avons créé :  
  
1.  Une solution appelée `MyBank` qui reçoit et traite des transactions pour différents types de comptes.  
  
2.  Un projet dans `MyBank` a appelé `BankDb` qui gère les transactions pour les comptes.  
  
3.  Une classe appelée `Maths` dans le projet d' `DbBank` qui exécute les fonctions mathématiques pour garantir qu'une transaction est avantageuse à bank.  
  
4.  Un projet de test unitaire a appelé `BankDbTests` pour tester le comportement du composant d' `BankDb`.  
  
5.  Une classe de test unitaire a appelé `MathsTests` pour vérifier le comportement de la classe d' `Maths`.  
  
 Nous testerons une méthode dans `Maths` qui ajoute deux entiers à l'aide d'une boucle :  
  
```  
public int AddIntegers(int first, int second)  
{  
    int sum = first;  
    for( int i = 0; i < second; i++)  
    {  
        sum += 1;  
    }  
    return sum;  
}  
```  
  
##  <a name="BKMK_Creating_a_data_source"></a> Création d'une source de données  
 Pour tester la méthode d' `AddIntegers`, nous créons une source de données qui spécifie une plage de valeurs pour les paramètres et la somme que vous vous attendez à ce que la valeur soit retournée.  Dans notre exemple, nous créons un contrat `MathsData` nommé par base de données SQL et une table nommée `AddIntegersData` qui contient les noms de colonne et valeurs suivants  
  
|FirstNumber|SecondNumber|Sum|  
|-----------------|------------------|---------|  
|0|1|1|  
|1|1|2|  
|2|\-3|\-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> TestContext ajouter un à la classe de test  
 L'infrastructure de test unitaire crée un objet d' `TestContext` pour stocker les informations de source de données pour un test piloté par des données.  L'infrastructure définit ensuite cet objet comme valeur de la propriété d' `TestContext` que nous créons les.  
  
```  
  
private TestContext testContextInstance;  
public TestContext TestContext  
{  
    get { return testContextInstance; }  
    set { testContextInstance = value; }  
}  
  
```  
  
 Dans votre méthode de test, vous accédez aux données via la propriété d'indexeur d' `DataRow` d' `TestContext`.  
  
##  <a name="BKMK_Writing_the_test_method"></a> Écrire la méthode de test  
 La méthode de test pour `AddIntegers` est assez simple.  Pour chaque ligne de la source de données, nous appelons `AddIntegers` avec les valeurs de la colonne de **FirstNumber** et de **SecondNumber** comme paramètres, et il vérifions la valeur de retour à la valeur de la colonne de **Somme** :  
  
```  
  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]  
[TestMethod()]  
public void AddIntegers_FromDataSourceTest()  
{  
    var target = new Maths();  
  
    // Access the data  
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);   
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);  
    int actual = target.IntegerMethod(x, y);  
    Assert.AreEqual(expected, actual,  
        "x:<{0}> y:<{1}>",  
        new object[] {x, y});  
  
}  
  
```  
  
 Notez que la méthode d' `Assert` inclut un message qui affiche les valeurs d' `x` et d' `y` d'une itération.  Par défaut, les valeurs affirmées, `expected` et `actual`, sont déjà incluses dans les détails d'un test.  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> Spécifier le DataSourceAttribute  
 L'attribut d' `DataSource` spécifie la chaîne de connexion pour la source de données et le nom de la table que vous utilisez dans la méthode de test.  Les informations exactes de la chaîne de connexion diffèrent selon le type de source de données que vous utilisez.  Dans cet exemple, nous avons utilisé une base de données SqlServerCe.  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 l'attribut de source de données a trois constructeurs.  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 Un constructeur avec un paramètre utilise les informations de connexion stockées dans le fichier app.config pour la solution.  *dataSourceSettingsName* est le nom de l'élément XML dans le fichier de configuration qui spécifie les informations de connexion.  
  
 L'utilisation d'un fichier app.config présente l'avantage que vous pouvez modifier l'emplacement de la base de données sans apporter de modifications au test unitaire lui\-même.  Pour plus d'informations sur la création et l'utilisation d'un fichier app.config, consultez [Procédure pas à pas : utilisation d'un fichier de configuration pour définir une source de données](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 Le constructeur d' `DataSource` avec deux paramètres spécifie la chaîne de connexion pour la source de données et le nom de la table qui contient les données pour la méthode de test.  
  
 Les chaînes de connexion dépend du type de source de données, mais il doit contenir un élément de fournisseur qui spécifie le nom invariant du fournisseur de données.  
  
```  
[DataSource(  
    dataProvider,   
    connectionString,   
    tableName,  
    dataAccessMethod  
    )]  
```  
  
###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> Utilisation TestContext.DataRow pour accéder aux données  
 Pour accéder aux données dans `AddIntegersData` entrez, utilisez l'indexeur d' `TestContext.DataRow`.  `DataRow` est un objet d' <xref:System.Data.DataRow>, nous extrayons des valeurs de colonne par index ou noms de colonnes.  Étant donné que les valeurs sont retournées sous forme de objets, nous devons les convertir en type approprié :  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a> Exécuter les résultats des tests et d'affichage  
 Lorsque vous avez terminé d'écrire une méthode de test, générez le projet de test.  La méthode de test s'affiche dans la fenêtre explorateur de tests dans le groupe **Pas exécuter des tests**.  Lorsque vous exécutez, entrez, puis réexécutez les tests, affiche dans l'explorateur de tests les résultats aux groupes par défaut **Échec des tests**, **Tests réussis**, **Tests ignorés** et Pas exécuter des tests.  Vous pouvez choisir **Exécuter tout** pour exécuter tous les tests, ou choisissez **Exécuter…** pour sélectionner un sous\-ensemble de tests à exécuter.  
  
 La barre de résultats des tests en haut de l'explorateur est animée comme vos séries de tests.  À la fin de la série de tests, la barre est verte si tous les tests ont réussi, ou rouge l'un des tests a échoué.  Un résumé de la série de tests s'affiche dans le volet d'informations en bas de la fenêtre explorateur de tests.  Sélectionnez un test pour afficher les détails de ce test dans le volet inférieur.  
  
 Si vous avez exécuté la méthode d' `AddIntegers_FromDataSourceTest` dans notre exemple, la barre de résultats active ou désactive le rouge et la méthode de test est déplacée échoue pilotés par des données de test **Échec des tests** A si les méthodes itérées l'une des de la source de données échoue.  Lorsque vous choisissez un test piloté par des données dans la fenêtre explorateur de tests, le volet d'informations affiche les résultats de chaque itération qui est identifiée par l'index de ligne de données.  Dans notre exemple, il s'avère que l'algorithme d' `AddIntegers` ne gère pas les valeurs négatives correctement.  
  
 Lorsque la méthode testée est corrigé et la récupération de test, vert de tours de barre des résultats et la méthode de test est déplacé dans le groupe **Test a réussi**.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>   
 [How to: Create and Run a Unit Test](http://msdn.microsoft.com/fr-fr/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)   
 [Tests unitaires sur votre code](../test/unit-test-your-code.md)   
 [Exécuter des tests unitaires avec l'Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)   
 [Écriture de tests unitaires pour le .NET Framework à l'aide de l'infrastructure de tests unitaires Microsoft pour le code managé](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)