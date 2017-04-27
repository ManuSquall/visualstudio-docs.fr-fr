---
title: "Exécuter des tests unitaires avec l’Explorateur de tests | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.unittesting.testexplorer.overview
ms.assetid: 91b167a3-280a-498b-8fc2-f67859a2c64e
caps.latest.revision: 27
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: bcfa2bb3a1841f2d960580506b638edcf650ca9e
ms.lasthandoff: 04/04/2017

---
# <a name="run-unit-tests-with-test-explorer"></a>Exécuter des tests unitaires avec l'Explorateur de tests
Utilisez l'Explorateur de tests pour exécuter des tests unitaires à partir de Visual Studio ou de projets de tests unitaires tiers, regrouper des tests en catégories, filtrer la liste de tests et créer, enregistrer et exécuter des sélections de tests. Vous pouvez également déboguer des tests et analyser les performances des tests et la couverture du code.  
  
##  <a name="BKMK_Contents"></a> Sommaire  
 [Frameworks de tests unitaires et projets de test](#BKMK_Unit_test_frameworks_and_test_projects)  
  
 [Exécuter des tests dans l’Explorateur de tests](#BKMK_Run_tests_in_Test_Explorer)  
  
 [Afficher les résultats des tests](#BKMK_View_test_results)  
  
 [Regrouper et filtrer la liste de tests](#BKMK_Group_and_filter_the_test_list)  
  
 [Créer des sélections personnalisées](#BKMK_Create_custom_playlists)  
  
 [Déboguer et analyser des tests unitaires](#BKMK_Debug_and_analyze_unit_tests)  
  
 [Ressources externes](#BKMK_External_resources)  
  
##  <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Frameworks de tests unitaires et projets de test  
 Visual Studio inclut les frameworks de tests unitaires Microsoft pour le code managé comme pour le code natif. Toutefois, l'Explorateur de tests peut également exécuter tout framework de tests unitaires qui a implémenté un adaptateur pour l'Explorateur de tests. Pour plus d’informations sur l’installation des frameworks de tests unitaires tiers, consultez [Installer des frameworks de tests unitaires tiers](../test/install-third-party-unit-test-frameworks.md).  
  
 L'Explorateur de tests peut exécuter des tests à partir de plusieurs projets de test dans une solution et à partir de classes de test qui font partie des projets de code de production. Les projets de test peuvent utiliser différents frameworks de tests unitaires. Quand le code testé est écrit pour le .NET Framework, le projet de test peut être écrit dans n'importe quel langage qui cible également le .NET Framework, quel que soit le langage du code cible. Les projets de code C/C++ natifs doivent être testés à l'aide d'un framework de tests unitaires C++.  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Run_tests_in_Test_Explorer"></a> Exécuter des tests dans l’Explorateur de tests  
 [Exécuter des tests](#BKMK_Run_tests) **&#124;** [Exécuter des tests après chaque génération](#BKMK_Run_tests_after_every_build)  
  
 Quand vous générez le projet de test, les tests s’affichent dans l’explorateur de tests. Si l’explorateur de tests n’est pas visible, sélectionnez **Test** dans le menu Visual Studio et choisissez **Fenêtres**, puis **Explorateur de tests**.  
  
 ![Explorateur de tests unitaires](../ide/media/ute_failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")  
  
 Tandis que vous exécutez, écrivez et réexécutez vos tests, l'Explorateur de tests affiche les résultats dans les groupes par défaut **Échecs de tests**, **Tests réussis**, **Tests ignorés** et **Tests non exécutés**. Vous pouvez modifier la façon dont l'Explorateur de tests regroupe vos tests.  
  
 Vous pouvez effectuer la majeure partie du travail de recherche, d'organisation et d'exécution des tests à partir de la barre d'outils de l'Explorateur de tests.  
  
 ![Exécuter des tests à partir de la barre d’outils de l’explorateur de tests](../test/media/ute_toolbar.png "UTE_ToolBar")  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
###  <a name="BKMK_Run_tests"></a> Exécuter les tests  
 Vous pouvez exécuter tous les tests dans la solution, tous les tests dans un groupe, ou un ensemble de tests que vous sélectionnez. Effectuez l’une des opérations suivantes :  
  
-   Pour exécuter tous les tests dans une solution, choisissez **Exécuter tout**.  
  
-   Pour exécuter tous les tests dans un groupe par défaut, choisissez **Exécuter...** , puis le groupe dans le menu.  
  
-   Sélectionnez les différents tests à exécuter, ouvrez le menu contextuel pour un test sélectionné, puis choisissez **Exécuter les tests sélectionnés**.  
  
-   Si les tests individuels n’ont aucune dépendance qui les empêche d’être exécutés dans n’importe quel ordre, activez l’exécution parallèle des tests avec le bouton bascule ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png "UTE_parallelicon-small") dans la barre d’outils. Cela peut réduire sensiblement le temps nécessaire pour exécuter tous les tests.  
  
 La barre Réussite/Échec en haut de la fenêtre Explorateur de tests est animée pendant l'exécution des tests. À la fin de la série de tests, la barre Réussite/Échec devient verte si tous les tests ont réussi ou rouge si un test a échoué.  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
###  <a name="BKMK_Run_tests_after_every_build"></a> Exécuter des tests après chaque génération  
  
> [!WARNING]
>  L'exécution de tests unitaires après chaque génération est prise en charge dans Visual Studio Enterprise.  
  
|||  
|-|-|  
|![Exécuter après génération](../test/media/ute_runafterbuild_btn.png "UTE_RunAfterBuild_btn")|Pour exécuter vos tests unitaires après chaque génération locale, choisissez **Test** dans le menu standard, puis **Exécuter les tests après la génération** dans la barre d'outils de l'Explorateur de tests.|  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_View_test_results"></a> Afficher les résultats des tests  
 [Afficher les détails du test](#BKMK_View_test_details) **&#124;** [Afficher le code source d’une méthode de test](#BKMK_View_the_source_code_of_a_test_method)  
  
 Tandis que vous exécutez, écrivez et réexécutez vos tests, l'Explorateur de tests affiche les résultats dans les groupes **Échecs de tests**, **Tests réussis**, **Tests ignorés** et **Tests non exécutés**. Le volet d'informations en bas de l'Explorateur de tests affiche un résumé de la série de tests.  
  
###  <a name="BKMK_View_test_details"></a> Afficher les détails du test  
 Pour afficher les détails d'un test individuel, sélectionnez le test.  
  
 ![Détails de l’exécution de tests](../test/media/ute_testdetails.png "UTE_TestDetails")  
  
 Le volet d'informations de test affiche les informations suivantes :  
  
-   Nom du fichier source et numéro de ligne de la méthode de test.  
  
-   Statut du test.  
  
-   Temps d'exécution de la méthode.  
  
 Si le test échoue, le volet d'informations affiche également :  
  
-   Le message retourné par le framework de tests unitaires pour le test.  
  
-   La trace de la pile au moment de l'échec du test.  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
###  <a name="BKMK_View_the_source_code_of_a_test_method"></a> Afficher le code source d’une méthode de test  
 Pour afficher le code source d'une méthode de test dans l'éditeur Visual Studio, sélectionnez le test, puis choisissez **Ouvrir un test** dans le menu contextuel (clavier : F12).  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Group_and_filter_the_test_list"></a> Regrouper et filtrer la liste de tests  
 [Regroupement de la liste de tests](#BKMK_Grouping_the_test_list) **&#124;** [Regrouper par caractéristiques](#BKMK_Group_by_traits) **&#124;** [Rechercher et filtrer la liste de tests](#BKMK_Search_and_filter_the_test_list)  
  
 L'Explorateur de tests vous permet de regrouper vos tests en catégories prédéfinies. La plupart des frameworks de tests unitaires qui s'exécutent dans l'Explorateur de tests vous permettent de définir vos propres catégories et paires catégorie/valeur pour regrouper vos tests. Vous pouvez également filtrer la liste de tests en mettant en correspondance les chaînes avec les propriétés de test.  
  
###  <a name="BKMK_Grouping_the_test_list"></a> Regroupement de la liste de tests  
 Pour modifier le mode d’organisation des tests, cliquez sur la flèche vers le bas à côté du bouton **Grouper par** ![Bouton Grouper de l’Explorateur de tests](../test/media/ute_groupby_btn.png "UTE_GroupBy_btn") et sélectionnez un nouveau critère de regroupement.  
  
 ![Grouper les tests par catégorie dans l’Explorateur de tests](../test/media/ute_groupbycategory.png "UTE_GroupByCategory")  
  
### <a name="test-explorer-groups"></a>Groupes de l'explorateur de tests  
  
|Regrouper|Description|  
|-----------|-----------------|  
|**Durée**|Regroupe les tests selon la durée d'exécution : **Rapide**, **Moyenne**et **Lente**.|  
|**Résultat**|Regroupe les tests selon les résultats de l'exécution : **Échecs de tests**, **Tests ignorés**, **Tests réussis**.|  
|**Caractéristiques**|Regroupe les tests selon les paires catégorie/valeur que vous définissez. La syntaxe permettant de spécifier les catégories et les valeurs des caractéristiques est définie par le framework de tests unitaires.|  
|**Project**|Regroupe les tests selon le nom des projets.|  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
###  <a name="BKMK_Group_by_traits"></a> Regrouper par caractéristiques  
 Une caractéristique est habituellement une paire nom/valeur de catégorie, mais elle peut également être une catégorie unique. Des caractéristiques peuvent être assignées aux méthodes identifiées comme une méthode de test par le framework de tests unitaires. Un framework de tests unitaires peut définir des catégories de caractéristiques. Vous pouvez ajouter des valeurs aux catégories de caractéristiques pour définir vos propres paires nom/valeur de catégorie. La syntaxe permettant de spécifier les catégories et les valeurs des caractéristiques est définie par le framework de tests unitaires.  
  
 **Caractéristiques dans le framework de tests unitaires Microsoft pour le code managé**  
  
 Dans le framework de tests unitaires Microsoft pour les applications managées, vous définissez une paire nom/valeur de caractéristique dans un attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>. Le framework de tests contient également les caractéristiques prédéfinies suivantes :  
  
|Caractéristique|Description|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|La catégorie Owner est définie par le framework de tests unitaires et vous demande de fournir une valeur de chaîne du propriétaire.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|La catégorie Priority est définie par le framework de tests unitaires et vous demande de fournir une valeur entière de la priorité.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|L'attribut TestCategory vous permet de fournir une catégorie sans valeur. Une catégorie définie par l'attribut TestCategory peut également être la catégorie d'un attribut TestProperty.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|L'attribut TestProperty vous permet de définir la paire catégorie/valeur de caractéristique.|  
  
 **Caractéristiques dans le framework de tests unitaires Microsoft pour C++**  
  
 Pour définir une caractéristique, utilisez la macro `TEST_METHOD_ATTRIBUTE` . Par exemple, pour définir une caractéristique nommée `TEST_MY_TRAIT`:  
  
```cpp  
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)  
```  
  
 Pour utiliser la caractéristique définie dans vos tests unitaires :  
  
```  
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)  
    TEST_OWNER(L"OwnerName")  
    TEST_PRIORITY(1)  
    TEST_MY_TRAIT(L"thisTraitValue")  
END_TEST_METHOD_ATTRIBUTE()  
  
TEST_METHOD(Method1)  
{     
    Logger::WriteMessage("In Method1");  
    Assert::AreEqual(0, 0);  
}  
```  
  
### <a name="c-trait-attribute-macros"></a>Macros d'attribut de fonctionnalités C++  
  
|Macro|Description|  
|-----------|-----------------|  
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Utilisez la macro TEST_METHOD_ATTRIBUTE pour définir une caractéristique.|  
|`TEST_OWNER(ownerAlias)`|Utilisez la caractéristique Owner prédéfinie pour spécifier un propriétaire de la méthode de test.|  
|`TEST_PRIORITY(priority)`|Utilisez la caractéristique Priority prédéfinie pour assigner des priorités relatives à vos méthodes de test.|  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
###  <a name="BKMK_Search_and_filter_the_test_list"></a> Rechercher et filtrer la liste de tests  
 Vous pouvez utiliser des filtres de l'Explorateur de tests pour limiter les méthodes de test dans les projets que vous affichez et exécutez.  
  
 Quand vous tapez une chaîne dans la zone de recherche de l'Explorateur de tests et appuyez sur Entrée, la liste de tests est filtrée pour afficher uniquement les tests dont les noms qualifiés complets contiennent la chaîne.  
  
 Pour filtrer selon un autre critère :  
  
1.  Ouvrez la liste déroulante à droite de la zone de recherche.  
  
2.  Choisissez un nouveau critère.  
  
3.  Entrez la valeur de filtre entre guillemets.  
  
 ![Filtrer les tests dans l’Explorateur de tests](../test/media/ute_filtertestlist.png "UTE_FilterTestList")  
  
> [!NOTE]
>  Les recherches ne respectent pas la casse et associent la chaîne spécifiée à une partie de la valeur de critère.  
  
|Qualificateur|Description|  
|---------------|-----------------|  
|**Caractéristique**|Recherche la catégorie et la valeur de caractéristique pour les correspondances. La syntaxe permettant de spécifier les catégories et les valeurs des caractéristiques est définie par le framework de tests unitaires.|  
|**Project**|Recherche les noms de projet de test pour les correspondances.|  
|**Message d’erreur**|Recherche les messages d'erreur définis par l'utilisateur retournés par des assertions ayant échoué pour les correspondances.|  
|**Chemin du fichier**|Recherche le nom de fichier qualifié complet des fichiers sources de test pour les correspondances.|  
|**Nom qualifié complet**|Recherche le nom de fichier qualifié complet des espaces de noms, des classes et des méthodes de test pour les correspondances.|  
|**Sortie**|Recherche les messages d'erreur définis par l'utilisateur qui sont écrits dans la sortie standard (stdout) ou une erreur standard (stderr). La syntaxe permettant de spécifier les messages de sortie est définie par le framework de tests unitaires.|  
|**Résultat**|Recherche les noms de catégorie de l'Explorateur de tests pour les correspondances : **Échecs de tests**, **Tests ignorés**, **Tests réussis**.|  
  
 Pour exclure un sous-ensemble des résultats d'un filtre, utilisez la syntaxe suivante :  
  
```  
FilterName:"Criteria" -FilterName:"SubsetCriteria"  
```  
  
 Par exemple :  
  
```  
FullName:"MyClass" - FullName:"PerfTest"  
```  
  
 retourne tous les tests qui incluent « MyClass » dans leur nom sauf ceux qui incluent également « PerfTest » dans leur nom.  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Create_custom_playlists"></a> Créer des sélections personnalisées  
 Vous pouvez créer et enregistrer une liste de tests que vous souhaitez exécuter ou visualiser en tant que groupe. Quand vous sélectionnez une sélection, les tests de la liste sont affichés dans l'Explorateur de tests. Vous pouvez ajouter un test à plusieurs sélections, et tous les tests de votre projet sont disponibles quand vous choisissez la sélection par défaut **Tous les tests** .  
  
 ![Choisissez une sélection](../test/media/ute_playlist.png "UTE_Playlist")  
  
 **Pour créer une sélection**, sélectionnez un ou plusieurs tests dans l'Explorateur de tests. Dans le menu contextuel, sélectionnez **Ajouter à la sélection**, **NewPlaylist**. Enregistrez le fichier sous le nom et à l'emplacement que vous spécifiez dans la boîte de dialogue **Créer une sélection** .  
  
 **Pour ajouter des tests à une sélection**, sélectionnez un ou plusieurs tests dans l'Explorateur de tests. Dans le menu contextuel, choisissez **Ajouter à la sélection**, puis la sélection à laquelle vous souhaitez ajouter des tests.  
  
 **Pour ouvrir une sélection**, choisissez Test, Sélection dans le menu Visual Studio, puis choisissez une sélection dans la liste de sélections récemment utilisées ou choisissez Ouvrir la sélection pour spécifier le nom et l'emplacement de la sélection.  
  
 Si les tests individuels n’ont aucune dépendance qui les empêche d’être exécutés dans n’importe quel ordre, activez l’exécution parallèle des tests avec le bouton bascule ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png "UTE_parallelicon-small") dans la barre d’outils. Cela peut réduire sensiblement le temps nécessaire pour exécuter tous les tests.  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Debug_and_analyze_unit_tests"></a> Déboguer et analyser des tests unitaires  
 [Déboguer les tests unitaires](#BKMK_Debug_unit_tests) **&#124;** [Diagnostiquer les problèmes de performances de méthode de test](#BKMK_Diagnose_test_method_performance_issues) **&#124;** [Analyser la couverture de code de test unitaire](#BKMK_Analyzeunit_test_code_coverage)  
  
###  <a name="BKMK_Debug_unit_tests"></a> Déboguer les tests unitaires  
 Vous pouvez utiliser l'Explorateur de tests pour démarrer une session de débogage de vos tests. L'exécution pas à pas de votre code avec le débogueur Visual Studio vous conduit de manière transparente à des allers et retours entre les tests unitaires et le projet testé. Pour démarrer le débogage :  
  
1.  Dans l’éditeur Visual Studio, définissez un point d’arrêt dans une ou plusieurs méthodes de test que vous souhaitez déboguer.  
  
    > [!NOTE]
    >  Comme les méthodes de test peuvent s'exécuter dans n'importe quel ordre, définissez les points d'arrêt dans toutes les méthodes de test que vous souhaitez déboguer.  
  
2.  Dans l'Explorateur de tests, sélectionnez les méthodes de test, puis choisissez **Déboguer les tests sélectionnés** dans le menu contextuel.  
  
 Pour plus d’informations sur le débogueur, consultez [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md).  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
###  <a name="BKMK_Diagnose_test_method_performance_issues"></a> Diagnostiquer les problèmes de performances de méthode de test  
 Pour diagnostiquer la raison pour laquelle une méthode de test est beaucoup trop longue, sélectionnez la méthode dans l'Explorateur de tests, puis choisissez Profil dans le menu contextuel. Consultez [Explorateur de performances](../profiling/performance-explorer.md).  
  
###  <a name="BKMK_Analyzeunit_test_code_coverage"></a> Analyser la couverture du code de test unitaire  
  
> [!NOTE]
>  La couverture du code de test unitaire est uniquement disponible dans Visual Studio Enterprise.  
  
 Vous pouvez déterminer la quantité de code de votre produit qui est réellement testée par vos tests unitaires à l'aide de l'outil de couverture de code Visual Studio. Vous pouvez exécuter la couverture de code sur les tests sélectionnés ou sur tous les tests d'une solution.  
  
 Pour exécuter la couverture du code pour les méthodes de test dans une solution :  
  
1.  Choisissez **Tests** dans le menu Visual Studio, puis **Analyser la couverture du code**.  
  
2.  Sélectionnez l'une des commandes suivantes dans le sous-menu :  
  
    -   **Tests sélectionnés** exécute les méthodes de test que vous avez sélectionnées dans l'Explorateur de tests.  
  
    -   **Tous les tests** exécute toutes les méthodes de test de la solution.  
  
 La fenêtre Résultats de la couverture du code affiche le pourcentage des blocs du code du produit qui ont été testés par ligne, fonction, classe, espace de noms et module.  
  
 Pour plus d’informations, consultez [Utilisation de la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_External_resources"></a> Ressources externes  
  
###  <a name="BKMK_Guidance"></a> Conseils  
 [Test de la livraison continue avec Visual Studio 2012 - Chapitre 2 : Tests unitaires : tester l’intérieur](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Voir aussi  
 [Tests unitaires sur votre code](../test/unit-test-your-code.md)   
 [Exécuter un test unitaire comme processus 64 bits](../test/run-a-unit-test-as-a-64-bit-process.md)

