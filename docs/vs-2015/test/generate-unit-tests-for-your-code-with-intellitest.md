---
title: Générer des tests unitaires pour votre code avec IntelliTest | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.assetid: cd9ff940-e948-4d28-a72c-b291ef5c1e90
caps.latest.revision: 35
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 304b26f8724413dceef8126434861bd7128d588c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60085010"
---
# <a name="generate-unit-tests-for-your-code-with-intellitest"></a>Générer des tests unitaires pour votre code avec IntelliTest
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliTest explore votre code .NET pour générer des données de test et une suite de tests unitaires. Pour chaque instruction dans le code, une entrée de test est générée pour exécuter cette instruction. Une analyse de cas est effectuée pour chaque branche conditionnelle dans le code. Par exemple, les instructions if, les assertions et toutes les opérations susceptibles de lever des exceptions sont analysées. Cette analyse vous permet de générer des données de test pour établir un test unitaire paramétré pour chacune de vos méthodes et de bénéficier d'une couverture de code élevée.  
  
 Lorsque vous exécutez IntelliTest, vous pouvez facilement détecter les tests qui échouent et ajouter le code nécessaire pour les corriger. Vous pouvez sélectionner les tests générés à enregistrer dans un projet de test pour fournir une suite de régression. À mesure que vous modifiez votre code, relancez IntelliTest pour synchroniser les tests générés avec les changements de code.  
  
 IntelliTest est disponible pour C# uniquement et ne prend pas en charge la configuration x64.  
  
## <a name="get-started-with-intellitest"></a>Mise en route d’IntelliTest  
 Vous avez besoin de Visual Studio Enterprise.  
  
### <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Exploration : Utiliser IntelliTest pour explorer votre code et générer des tests unitaires  
 Pour générer des tests unitaires, vos types doivent être publics. Sinon, [créez d’abord des tests unitaires](#NoRun) avant de les générer.  
  
1. Ouvrez votre solution dans Visual Studio. Ouvrez ensuite le fichier de classe comprenant les méthodes à tester.  
  
2. Cliquez avec le bouton droit sur une méthode dans votre code et choisissez **Exécuter IntelliTest** pour générer des tests unitaires pour le code de votre méthode.  
  
     ![Cliquer avec le bouton droit dans votre méthode pour générer des tests unitaires](../test/media/runpex.png "RunPEX")  
  
     IntelliTest exécute votre code plusieurs fois de suite avec des entrées différentes. Chaque série est représentée dans un tableau qui répertorie les données des tests d'entrée et la sortie ou exception résultante.  
  
     ![Fenêtre Résultats de l’exploration affichée avec des tests](../test/media/pexexplorationresults.png "PEXExplorationResults")  
  
     Pour générer des tests unitaires pour toutes les méthodes publiques d'une classe, cliquez avec le bouton droit sur la classe, et non sur une méthode spécifique. Sélectionnez **Exécuter IntelliTest**. Utilisez la liste déroulante dans la fenêtre Résultats de l'exploration pour afficher les tests unitaires et les données d'entrée pour chaque méthode dans la classe.  
  
     ![Sélectionner les résultats des tests à afficher dans la liste](../test/media/selectpextest.png "SelectPEXTest")  
  
     Pour les tests réussis, vérifiez que les résultats indiqués dans la colonne des résultats correspondent bien à vos attentes. Pour les tests qui échouent, corrigez votre code comme il convient. Réexécutez IntelliTest pour valider les corrections.  
  
### <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Persistance : Enregistrer les tests unitaires comme une suite de régression  
  
1. Sélectionnez les lignes de données que vous souhaitez enregistrer avec le test unitaire paramétrable dans un projet de test.  
  
     ![Sélectionner des tests, puis cliquer avec le bouton droit et choisir Enregistrer](../test/media/savepextests.png "SavePEXTests")  
  
     Vous pouvez afficher le projet de test et le test unitaire paramétré qui a été créé. Les tests unitaires individuels correspondant à chacune des lignes sont enregistrés dans le fichier .g.cs dans le projet de test, et un test unitaire paramétré est enregistré dans son fichier .cs correspondant. Vous pouvez exécuter les tests unitaires et afficher les résultats dans l'Explorateur de tests au même titre qu'un autre test unitaire que vous avez créé manuellement.  
  
     ![Ouvrir le fichier de classe dans la méthode de test pour afficher le test unitaire](../test/media/testmethodpex.png "TestMethodPEX")  
  
     Toutes les références nécessaires sont également ajoutées au projet de test.  
  
     Si le code de la méthode change, relancez IntelliTest pour synchroniser les tests unitaires avec les changements.  
  
### <a name="assist-use-intellitest-to-focus-code-exploration"></a>Assistance : Utiliser IntelliTest pour vous concentrer sur l’exploration du code  
  
1. Si vous avez du code plus complexe, IntelliTest vous aide à vous concentrer sur l'exploration de votre code. Par exemple, si vous avez une méthode avec une interface comme paramètre et que plusieurs classes implémentent cette interface, IntelliTest découvre ces classes et génère un avertissement.  
  
     Passez en revue les avertissements et décidez de la marche à suivre.  
  
     ![Afficher les avertissements](../test/media/pexviewwarning.png "PEXViewWarning")  
  
2. Après avoir étudié le code et identifié les parties à tester, vous pouvez traiter l'avertissement et choisir les classes à utiliser pour tester l'interface.  
  
     ![Cliquer avec le bouton droit sur l’avertissement et choisir Corriger](../test/media/pexfixwarning.png "PEXFixWarning")  
  
     Ce choix est ajouté au fichier PexAssemblyInfo.cs.  
  
     `[assembly: PexUseType(typeof(Camera))]`  
  
3. Vous pouvez à présent relancer IntelliTest pour générer un test unitaire paramétrable et des données de test en utilisant simplement la classe que vous avez corrigée.  
  
     ![Réexécuter IntelliTest pour générer les données de test](../test/media/pexwarningsfixed.png "PEXWarningsFixed")  
  
### <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Spécification : Utiliser IntelliTest pour valider les propriétés de correction que vous spécifiez dans le code  
 Spécifiez la relation générale entre les entrées et les sorties que les tests unitaires générés doivent valider. Cette spécification est encapsulée dans une méthode qui ressemble à une méthode de test, mais qui est quantifiée de façon universelle. Il s'agit de la méthode de test unitaire paramétré, et les assertions que vous faites doivent contenir toutes les valeurs d'entrée possibles qu'IntelliTest peut générer.  
  
## <a name="QandALink"></a> Q et R  
  
### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>Q : Pouvez-vous utiliser IntelliTest pour du code non managé ?  
 **R :** Non, IntelliTest fonctionne uniquement avec du code managé.  
  
### <a name="q-when-does-a-generated-test-pass-or-fail"></a>Q : Qu’est-ce qui détermine la réussite ou l’échec d’un test généré ?  
 **R :** Comme tout autre test unitaire, il réussit si aucune exception ne se produit. Il échoue en cas d'échec d'une assertion ou si le code testé lève une exception non gérée.  
  
 Si vous avez un test qui peut réussir en dépit de certaines exceptions, vous pouvez définir l'un des attributs suivants en fonction de vos besoins au niveau de la méthode de test, de la classe de test ou de l'assembly :  
  
- **PexAllowedExceptionAttribute**  
  
- **PexAllowedExceptionFromTypeAttribute**  
  
- **PexAllowedExceptionFromTypeUnderTestAttribute**  
  
- **PexAllowedExceptionFromAssemblyAttribute**  
  
### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>Q : puis-je ajouter des hypothèses au test unitaire paramétrable ?  
 **R :** Oui, utilisez des hypothèses afin de spécifier les données de test non nécessaires pour le test unitaire d’une méthode spécifique. Utilisez la classe <xref:Microsoft.Pex.Framework.PexAssume> pour ajouter des hypothèses. Par exemple, vous pouvez ajouter une hypothèse selon laquelle la variable lengths n'a pas la valeur NULL.  
  
 `PexAssume.IsNotNull(lengths);`  
  
 Si vous ajoutez une hypothèse et que vous relancez IntelliTest, les données de test qui ne sont plus adéquates sont supprimées.  
  
### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>Q : puis-je ajouter des assertions au test unitaire paramétrable ?  
 **R :** Oui. IntelliTest vérifie que les assertions dans votre instruction sont correctes quand il exécute les tests unitaires. Utilisez la classe <xref:Microsoft.Pex.Framework.PexAssert> ou l'API d'assertion qui est fournie avec l'infrastructure de test pour ajouter des assertions. Par exemple, vous pouvez ajouter une assertion selon laquelle deux variables sont égales.  
  
 `PexAssert.AreEqual(a, b);`  
  
 Si vous ajoutez une assertion et que vous relancez IntelliTest, ce dernier vérifie que votre assertion est valide et le test échoue si elle ne l’est pas.  
  
### <a name="NoRun"></a> Q : Puis-je générer des tests unitaires paramétrables sans exécuter auparavant IntelliTest ?  
 **R :** Oui, cliquez avec le bouton droit sur la classe ou la méthode, puis choisissez **Créer IntelliTest**.  
  
 ![Cliquer avec le bouton droit sur l’éditeur, choisir Créer IntelliTest](../test/media/pexcreateintellitest.png "PEXCreateIntelliTest")  
  
 Acceptez le format par défaut pour générer vos tests ou modifiez la façon dont votre projet et les tests sont nommés. Vous pouvez créer un nouveau projet de test ou enregistrer vos tests dans un projet existant.  
  
 ![Créer IntelliTest avec MSTest par défaut](../test/media/pexcreateintellitestmstest.png "PEXCreateIntelliTestMSTest")  
  
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>Q : Puis-je utiliser d’autres frameworks de tests unitaires avec IntelliTest ?  
 **R :** Oui, suivez ces étapes pour [rechercher et installer d’autres frameworks](../test/install-third-party-unit-test-frameworks.md). Après avoir redémarré Visual Studio et rouvert votre solution, cliquez avec le bouton droit sur la classe ou la méthode, puis choisissez **Créer IntelliTest**. Sélectionnez le framework installé ici :  
  
 ![Sélectionner un autre framework de test unitaire pour IntelliTest](../test/media/pexcreateintellitestextensions.png "PEXCreateIntelliTestExtensions")  
  
 Exécutez ensuite IntelliTest pour générer des tests unitaires individuels dans leurs fichiers g.cs correspondants.  
  
### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>Q : Puis-je en savoir plus sur la façon dont les tests sont générés ?  
 **R :** Oui, pour obtenir une vue d’ensemble générale, lisez ce [billet de blog](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/05/intellitest-one-test-to-rule-them-all.aspx).
