---
title: Tests unitaires sur votre code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1e6f0dd19c9d5d3ea1ee28a267aa969aad638948
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695220"
---
# <a name="unit-test-your-code"></a>Tests unitaires sur votre code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les tests unitaires offrent aux développeurs et aux testeurs une méthode rapide pour rechercher des erreurs de logique dans les méthodes des classes des projets [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] et [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)].  
  
 Les outils de test unitaire incluent :  
  
1. **Explorateur de tests.** L'Explorateur de tests vous permet d'exécuter des tests unitaires et d'afficher leurs résultats. L'Explorateur de tests peut utiliser tout framework de tests unitaires, notamment un framework tiers, qui a un adaptateur pour l'Explorateur de solutions.  
  
2. **Framework de tests unitaires Microsoft pour le code managé.** Le framework de tests unitaires Microsoft pour le code managé est installée avec Visual Studio et fournit un framework pour tester le code .NET.  
  
3. **Frameworks de tests unitaires Microsoft pour C++.** Le framework de tests unitaires Microsoft pour C++ est installée avec Visual Studio et fournit un framework pour tester le code natif.  
  
4. **Outils de couverture du code.** Vous pouvez déterminer la quantité de code du produit que vos tests unitaires passent en revue en utilisant une seule commande dans l'Explorateur de tests.  
  
5. **Framework d’isolement Microsoft Fakes.** Le framework d'isolement Microsoft Fakes peut créer des classes et des méthodes de remplacement pour le code de production et le code du système qui créent des dépendances du code testé. En implémentant les délégués substituts d'une fonction, vous contrôlez le comportement et la sortie de l'objet de dépendance.  
  
   Vous pouvez également utiliser [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) pour explorer votre code .NET et générer des données de test et une suite de tests unitaires. Pour chaque instruction dans le code, une entrée de test est générée pour exécuter cette instruction. Une analyse de cas est effectuée pour chaque branche conditionnelle dans le code.  
  
## <a name="key-tasks"></a>Tâches clés  
 Utilisez les rubriques suivantes pour mieux comprendre et créer les tests unitaires :  
  
|Tâches|Rubriques associées|  
|-----------|-----------------------|  
|**Démarrages rapides et procédures pas à pas :** consultez les rubriques suivantes pour apprendre à effectuer des tests unitaires dans Visual Studio avec des exemples de code.|-   [Procédure pas à pas : Création et exécution de tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Démarrage rapide : Développement piloté par les tests avec l’Explorateur de tests](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Ajout de tests unitaires à des applications C++ existantes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [Tests unitaires de code natif avec l’Explorateur de tests](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
|**Tests unitaires avec l’Explorateur de tests :** découvrez comment l’Explorateur de tests vous permet de créer des tests unitaires plus productifs et plus efficaces.|-   [Concepts de base des tests unitaires](../test/unit-test-basics.md)<br />-   [Créer un projet de test unitaire](../test/create-a-unit-test-project.md)<br />-   [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)<br />-   [Installer des frameworks de tests unitaires tiers](../test/install-third-party-unit-test-frameworks.md)<br />-   [Mise à niveau des tests unitaires dans Visual Studio 2010](https://msdn.microsoft.com/9bb75856-f68a-4de2-a084-b08a947a1172)|  
|**Effectuer des tests unitaires sur du code managé :**|-   [Écriture de tests unitaires pour le .NET Framework à l’aide du framework de tests unitaires Microsoft pour le code managé](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|  
|**Effectuer des tests unitaires sur du code C++**|-   [Écriture de tests unitaires pour C/C++ à l’aide du framework de tests unitaires Microsoft pour C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|  
|**Isolation des tests unitaires**|-   [Isolation du code testé avec Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|  
|**Utiliser de la couverture du code pour identifier quelle proportion du code de votre projet est testée à l’aide de tests unitaires :** En savoir plus sur la fonctionnalité de couverture du code de [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] outils de test.|-   [Utilisation de la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|  
|**Effectuer l’analyse des performances et de contrainte à l’aide de tests de charge pour vos tests unitaires :** vous pouvez créer un test de charge et lui ajouter vos tests unitaires pour isoler les problèmes de contraintes et de performances de votre application. **Remarque :**  La création et l’utilisation de tests de charge nécessitent Visual Studio Enterprise.|-   [Création et modification de tests de charge](https://msdn.microsoft.com/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [Guide pratique pour Ajouter des Tests de performances Web et Tests unitaires à un scénario de Test de charge](https://msdn.microsoft.com/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [Guide pratique pour Supprimer des Tests Web et Tests unitaires à partir d’un scénario de Test de charge](https://msdn.microsoft.com/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|  
|**Définir et appliquer des critères de qualité :** Vous pouvez créer des niveaux de qualité pour que les tests soient exécutés avant que le code est archivé pour aider à garantir la qualité du code.|-   [Définir et appliquer des niveaux de qualité](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Étendez l’unité de type de test :** Vous pouvez ajouter des fonctionnalités à vos tests qui ne peuvent pas être dans l’infrastructure de Test unitaire. Par exemple, vous pouvez ajouter une propriété de test qui spécifie si un test doit s'exécuter comme utilisateur normal ou pas. Vous pouvez également étendre le framework pour ajouter des attributs de ligne à une méthode et utiliser les données de cette ligne dans le test.|Pour obtenir un exemple de code permettant d’étendre le framework de tests unitaires, consultez le [site web Microsoft](http://go.microsoft.com/fwlink/?LinkId=185591) suivant.|  
|**Définir les options de test :** par exemple, vous pouvez spécifier l’emplacement de stockage des résultats des tests.|[Configurer des tests unitaires à l’aide d’un fichier .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## <a name="related-tasks"></a>Tâches connexes  
 [Examen des résultats des tests dans Microsoft Test Manager](https://msdn.microsoft.com/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)  
  
 Décrit les résultats des tests et la façon de les utiliser, notamment comment les afficher, les enregistrer et les supprimer.  
  
 [Exécution de tests du système à l’aide de Microsoft Visual Studio](https://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130)  
  
 Fournit des liens vers des informations sur l'utilisation de Visual Studio plutôt que [!INCLUDE[TCMext](../includes/tcmext-md.md)] pour exécuter des tests automatisés.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 Décrit l’espace de noms UnitTesting qui fournit des attributs, des exceptions, des assertions et d’autres classes qui prennent en charge le test unitaire.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 Décrit l'espace de noms UnitTesting.Web qui étend l'espace de noms UnitTesting en fournissant la prise en charge pour les tests unitaires [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] et de service Web.  
  
## <a name="external-resources"></a>Ressources externes  
  
### <a name="videos"></a>Vidéos  
 [Channel 9 : Vos applications Windows Store en XAML de tests unitaires](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Forums  
 [Tests unitaires Visual Studio](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="guidance"></a>Conseils  
 [Test de livraison continue avec Visual Studio 2012 – chapitre 2 : Tests unitaires : Tester l’intérieur](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="reference"></a>Référence  
 [Index de contenu des tests unitaires](http://go.microsoft.com/fwlink/?LinkID=254719)  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorer la qualité du code](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)   
 [Test de l’application](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)
