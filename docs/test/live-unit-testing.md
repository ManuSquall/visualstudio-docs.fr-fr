---
title: Live Unit Testing
ms.date: 03/07/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: jillre
ms.author: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b5974819e9dca064655cf04eec3dd371f09ee15c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653003"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Comment configurer et utiliser Live Unit Testing

Lorsque vous développez une application, Live Unit Testing exécute automatiquement tous les tests unitaires impactés en arrière-plan et présente les résultats et la couverture du code en temps réel. Lorsque vous modifiez votre code, Live Unit Testing fournit des commentaires sur l’impact de vos modifications sur les tests existants et vous indique si le code que vous avez ajouté est couvert par un ou plusieurs tests existants. Cela vous rappelle doucement d’écrire des tests unitaires au fur et à mesure que vous apportez des correctifs de bogues ou que vous ajoutez de nouvelles fonctionnalités.

> [!NOTE]
> Live Unit Testing est disponible pour C# les projets et Visual Basic qui ciblent .net Core ou .NET Framework dans l’édition Enterprise de Visual Studio.

Lorsque vous utilisez Live Unit Testing pour vos tests, il conserve les données sur l’état de vos tests. L’utilisation de données persistantes permet à Live Unit Testing d’offrir des performances supérieures lors de l’exécution dynamique de vos tests en réponse aux modifications du code.

## <a name="supported-test-frameworks"></a>Frameworks de test pris en charge

Live Unit Testing fonctionne avec les trois frameworks de tests unitaires populaires listés dans le tableau suivant. La version minimale prise en charge de leurs adaptateurs et infrastructures est également indiquée. Les frameworks de tests unitaires sont tous disponibles dans NuGet.org.

|Infrastructure de test  |Version minimale de l’adaptateur Visual Studio  |Version minimale du framework  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio version 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter version 3.5.1 |NUnit version 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Si vous avez des projets de test basés sur MSTest plus anciens qui référencent Microsoft. VisualStudio. QualityTools. UnitTestFramework et que vous ne souhaitez pas passer aux packages NuGet NuGet plus récents, effectuez une mise à niveau vers Visual Studio 2019 ou Visual Studio 2017.

Dans certains cas, vous devrez peut-être restaurer explicitement les packages NuGet référencés par un projet pour que les Live Unit Testing fonctionnent. Pour ce faire, vous pouvez effectuer une génération explicite de la solution (sélectionnez **générer**  > **régénérer la solution** dans le menu Visual Studio de niveau supérieur) ou restaurer les packages dans la solution (cliquez avec le bouton droit sur la solution et sélectionnez **restaurer NuGet Packages**).

## <a name="configure"></a>Configurer

Configurez Live Unit Testing en sélectionnant **outils**  > **options** dans la barre de menus de Visual Studio de niveau supérieur, puis en sélectionnant **Live Unit testing** dans le volet gauche de la boîte de dialogue **options** .

> [!TIP]
> Une fois que Live Unit Testing est activé (voir la section suivante, [Démarrer, suspendre et arrêter Live Unit testing](#start-pause-and-stop)), vous pouvez également ouvrir la boîte de dialogue **options** en sélectionnant **tester**  > **Live Unit testing** **options**de  > .

L’illustration suivante montre les options de configuration Live Unit Testing disponibles dans la boîte de dialogue :

![Options de configuration Live Unit Testing](./media/lut-options.png)

Les options configurables sont les suivantes :

- Interruption de Live Unit Testing quand une solution est générée et déboguée.

- L’interruption de Live Unit Testing lorsque la batterie d’un système passe en dessous d’un seuil défini.

- L’exécution automatique de Live Unit Testing lorsqu’une solution est ouverte.

- Activation de la génération de commentaires de documentation XML et de symboles de débogage.

- Répertoire où stocker les données persistantes.

- Possibilité de supprimer toutes les données persistantes. Cela est utile lorsque Live Unit Testing se comporte de manière imprévisible ou inattendue, ce qui suggère que les données persistantes sont endommagées.

- Intervalle après lequel un cas de test expire. La valeur par défaut est de 30 secondes.

- Le nombre maximal de processus de test que Live Unit Testing crée.

- La quantité maximale de mémoire que les processus Live Unit Testing peuvent consommer.

- Le niveau des informations écrites dans la fenêtre **Sortie** de Live Unit Testing.

   Les options incluent : aucune journalisation (**Aucune**), messages d’erreur uniquement (**Erreur**), erreur et messages d’information (**Info**, la valeur par défaut) ou tous les détails (**Commentaires**).

   Vous pouvez également afficher une sortie détaillée dans la fenêtre **Sortie** de Live Unit Testing en affectant la valeur « 1 » à une variable d’environnement utilisateur nommée `VS_UTE_DIAGNOSTICS`, puis en redémarrant Visual Studio.

   Pour capturer dans un fichier les messages détaillés du journal MSBuild à partir de Live Unit Testing, définissez la variable d’environnement utilisateur `LiveUnitTesting_BuildLog` en fonction du nom du fichier qui doit contenir le journal.

## <a name="start-pause-and-stop"></a>Démarrer, suspendre et arrêter

Pour activer Live Unit Testing, sélectionnez **Test**  > **Live Unit testing**  > **Démarrer** dans le menu Visual Studio de niveau supérieur. Lorsque Live Unit Testing est activé, les options disponibles dans le menu **Live Unit testing** sont modifiées à partir d’un seul élément, **Démarrer**, **suspendre**, **arrêter**et **Réinitialiser le nettoyage**:

- L' **interruption** interrompt temporairement Live Unit testing.

  Lorsque Live Unit Testing est suspendue, la visualisation de couverture n’apparaît pas dans l’éditeur, mais toutes les données collectées sont conservées. Pour réactiver Live Unit Testing, sélectionnez **Continuer** dans le menu Live Unit Testing. Live Unit Testing effectue le travail nécessaire pour rattraper toutes les modifications apportées pendant qu’il a été suspendu et met à jour les glyphes de manière appropriée.

- **Arrêter** arrête complètement Live Unit testing. Live Unit Testing abandonne toutes les données qu’il a collectées.

- La **réinitialisation** des arrêts en mode minimal Live Unit testing, supprime les données persistantes, puis redémarre Live Unit testing.

> [!NOTE]
> Si vous démarrez Live Unit Testing dans une solution qui n’inclut pas un projet de test unitaire, les options **Pause**, **Arrêter**, et **Réinitialiser** apparaissent dans le menu de **Live Unit Testing**, mais Live Unit Testing ne démarre pas. La fenêtre **sortie** affiche un message qui commence par « aucun adaptateur de test pris en charge n’est référencé par cette solution... ».

À tout moment, vous pouvez interrompre temporairement ou arrêter complètement Live Unit Testing. Vous pouvez effectuer cette opération, par exemple, si vous êtes au milieu d’une refactorisation et si vous savez que vos tests seront rompus pendant un certain temps.

## <a name="view-coverage-visualization"></a>Afficher la visualisation de la couverture

Une fois l’option activée, Live Unit Testing met à jour chaque ligne de code dans l’éditeur Visual Studio pour vous indiquer si le code que vous écrivez est couvert par les tests unitaires et si les tests qui le couvrent réussissent. L’image suivante montre des lignes de code avec les tests en réussite et en échec, ainsi que des lignes de code qui ne sont pas couvertes par les tests. Les lignes avec un symbole « ✓ » vert sont couvertes seulement par des tests ayant réussi, les lignes assorties d’un symbole « x » rouge sont couvertes par un ou plusieurs tests ayant échoué, et les lignes avec un symbole « ➖ » bleu ne sont couvertes par aucun test.

![Couverture du code dans Visual Studio](./media/lut-codewindow.png)

Live Unit Testing la visualisation de la couverture est mise à jour immédiatement lorsque vous modifiez le code dans l’éditeur de code. Lors du traitement des modifications, la visualisation change pour indiquer que les données ne sont pas à jour en ajoutant une image de minuteur ronde sous les symboles de réussite, d’échec et non couverts, comme le montre l’image suivante.

![Couverture du code dans Visual Studio avec l’icône de minuterie](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Obtenir des informations sur l’état des tests

En passant la souris sur le symbole de réussite ou d’échec dans la fenêtre de code, vous pouvez voir combien de tests ont atteint cette ligne. Pour afficher l’état des tests individuels, sélectionnez le symbole :

![État des tests pour un symbole dans Visual Studio](./media/lut-failedinfo.png)

En plus de fournir les noms et les résultats des tests, l’info-bulle vous permet de réexécuter ou de déboguer l’ensemble de tests. Si vous sélectionnez un ou plusieurs des tests dans l’infobulle, vous pouvez également exécuter ou déboguer uniquement ces tests. Cela vous permet de déboguer vos tests sans quitter la fenêtre de code. Lors du débogage, en plus d’observer tous les points d’arrêt que vous avez déjà définis, l’exécution du programme s’interrompt quand le débogueur exécute une méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> qui retourne un résultat inattendu.

Lorsque vous passez la souris sur un test ayant échoué dans l’infobulle, celle-ci se développe pour fournir des informations supplémentaires sur l’échec, comme illustré dans l’image suivante. Pour accéder directement à un test ayant échoué, double-cliquez dessus dans l’info-bulle.

![Info des info-bulles de test ayant échoué dans Visual Studio](./media/lut-failedmsg.png)

Lorsque vous accédez au test qui a échoué, Live Unit Testing indique visuellement dans la signature de la méthode les tests qui ont :

- passé (indiqué par un becher demi-complet avec un « ✓ » vert)
- échec (un becher demi-complet avec un « 🞩 » rouge)
- ne sont pas impliquées dans le Live Unit Testing (un bécher à demi-totalité avec un « ➖ » bleu)

Les méthodes sans test n’affichent aucun un symbole. L’image suivante illustre les quatre types de méthodes.

![Méthodes de test dans Visual Studio avec le symbole de réussite ou d’échec](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnostiquer et corriger les échecs des tests

À partir du test qui a échoué, vous pouvez facilement déboguer le code du produit, apporter des modifications et continuer à développer votre application. Étant donné que Live Unit Testing s’exécute en arrière-plan, il n’est pas nécessaire d’arrêter et de redémarrer Live Unit Testing pendant le cycle de débogage, de modification et de reprise.

Par exemple, l’échec du test affiché dans l’image précédente était dû à une hypothèse incorrecte dans la méthode de test que les caractères non alphabétiques retournent `true` lorsqu’ils sont passés à la méthode <xref:System.Char.IsLower%2A?displayProperty=fullName>. Une fois que vous avez corrigé la méthode de test, tous les tests doivent réussir. Vous n’avez pas besoin de suspendre ou d’arrêter Live Unit Testing.

## <a name="test-explorer"></a>Explorateur de tests

L' **Explorateur de tests** fournit une interface qui vous permet d’exécuter et de déboguer des tests et d’analyser les résultats des tests. Live Unit Testing s’intègre à **l’Explorateur de tests**. Quand Live Unit Testing n’est pas activé ou quand il est arrêté, **l’Explorateur de tests** affiche l’état des tests unitaires lors de la dernière exécution d’un test. Des modifications apportées au code source nécessitent que vous réexécutiez les tests. En revanche, lorsque Live Unit Testing est activé, l’état des tests unitaires dans **l’Explorateur de tests** est mis à jour immédiatement. Vous n’avez pas besoin d’exécuter explicitement les tests unitaires.

> [!TIP]
> Ouvrez l' **Explorateur de tests** en sélectionnant **tester**  > **Windows**  >  l'**Explorateur de tests** dans le menu Visual Studio de niveau supérieur.

Vous remarquerez peut-être dans la fenêtre de l' **Explorateur de tests** que certains tests sont dépassés. Par exemple, lorsque vous activez Live Unit Testing après l’ouverture d’un projet précédemment enregistré, la fenêtre de l' **Explorateur de tests** avait sorti tout sauf le test ayant échoué, comme le montre l’image suivante. Dans ce cas, Live Unit Testing a réexécuté le test qui a échoué, mais il n’a pas réexécuté les tests réussis. Cela est dû au fait que les données persistantes de Live Unit Testing indiquent qu’aucune modification n’a été apportée depuis la dernière exécution réussie des tests.

![Échec du test dans l’Explorateur de tests](media/lut-test-explorer.png)

Vous pouvez réexécuter tous les tests qui apparaissent estompés en sélectionnant les options **exécuter tout** ou **exécuter** dans le menu de l' **Explorateur de tests** . Ou sélectionnez un ou plusieurs tests dans le menu de l' **Explorateur de tests** , cliquez avec le bouton droit, puis sélectionnez **exécuter les tests sélectionnés** ou **déboguer les tests sélectionnés** dans le menu contextuel. À mesure que les tests sont exécutés, ils sont déplacent vers le haut de la liste.

Il existe certaines différences entre l’exécution automatique des tests et la mise à jour des résultats de test de Live Unit Testing et l’exécution explicite des tests à partir de **l’Explorateur de tests**. Ces différences incluent :

- L’exécution ou le débogage des tests depuis la fenêtre de l’Explorateur de tests exécute des fichiers binaires standards tandis que Live Unit Testing exécute des fichiers binaires instrumentés.
- Live Unit Testing ne crée pas de domaine d’application pour exécuter des tests, mais exécute des tests à partir du domaine par défaut. Les tests exécutés depuis la fenêtre de **l’Explorateur de tests** créent un domaine d’application.
- Live Unit Testing exécute des tests dans chaque assembly de test de manière séquentielle. Dans la fenêtre **Explorateur de tests** , vous pouvez choisir d’exécuter plusieurs tests en parallèle.

## <a name="large-solutions"></a>Solutions de grande taille

Si votre solution contient au moins 10 projets, Visual Studio affiche la boîte de dialogue suivante lorsque vous :

- Démarrer Live Unit Testing et il n’y a pas de données persistantes
- sélectionner le  >  de **Test** **Live Unit testing**  > **Réinitialiser le nettoyage**

![Boîte de dialogue Live Unit Testing pour les gros projets](media/lut-large-project.png)

La boîte de dialogue vous avertit que l’exécution dynamique d’un grand nombre de tests dans des projets volumineux peut avoir un impact considérable sur les performances. Si vous sélectionnez **OK**, Live Unit Testing exécute tous les tests de la solution. Si vous sélectionnez **Annuler**, vous pouvez sélectionner les tests à exécuter. La section suivante explique comment procéder.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Inclure et exclure des projets de test et des méthodes de test

Pour les solutions comportant de nombreux projets de test, vous pouvez contrôler les projets et les méthodes individuelles d’un projet qui participent à Live Unit Testing. Par exemple, si vous disposez d’une solution avec des centaines de projets de test, vous pouvez sélectionner un ensemble ciblé de projets de test à inclure dans Live Unit Testing. Il existe plusieurs façons de procéder, selon que vous souhaitez exclure tous les tests du projet ou de la solution, inclure ou exclure la plupart des tests ou exclure des tests individuels. Live Unit Testing enregistre l’état d’inclusion/d’exclusion en tant que paramètre utilisateur et le conserve quand une solution est fermée puis ouverte à nouveau.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Exclure tous les tests d’un projet ou d’une solution

Pour sélectionner les projets individuels dans les tests unitaires, procédez comme suit une fois Live Unit Testing démarré :

1. Cliquez avec le bouton droit sur la solution dans **l’Explorateur de solutions** et choisissez **Live Tests** > **Exclure** pour exclure toute la solution.
1. Cliquez avec le bouton droit sur chaque projet de test à inclure dans les tests et choisissez **Live Tests** > **Inclure**.

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Exclure des tests individuels de la fenêtre de l’éditeur de code

Vous pouvez utiliser la fenêtre de l’éditeur de code pour inclure ou exclure des méthodes de test. Cliquez avec le bouton droit sur la signature de la méthode de test dans la fenêtre de l’éditeur de code, puis sélectionnez l’une des options suivantes :

- Les **tests en direct**  >  incluent la**méthode \<selected >**
- **Tests en direct**  > **méthode d’exclusion \<selected >**
- Les **tests en direct**  > **excluent tout sauf \<selected méthode >**

### <a name="exclude-tests-programmatically"></a>Exclure des tests par programmation

Vous pouvez appliquer l’attribut <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> pour exclure par programme des méthodes, des classes ou des structures de la génération de couverture dans Live Unit Testing.

Utilisez les attributs suivants pour exclure des méthodes individuelles de Live Unit Testing :

- Pour xUnit : `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Pour NUnit : `[Category("SkipWhenLiveUnitTesting")]`
- Pour MSTest : `[TestCategory("SkipWhenLiveUnitTesting")]`

Utilisez les attributs suivants pour exclure l’intégralité d’un assembly de tests de Live Unit Testing :

- Pour xUnit : `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Pour NUnit : `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Pour MSTest : `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Voir aussi

- [Outils de test de code](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blog sur Live Unit Testing](https://go.microsoft.com/fwlink/?linkid=842514)
- [FAQ Live Unit Testing](live-unit-testing-faq.md)
- [Vidéo Channel 9 : Live Unit Testing dans Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
