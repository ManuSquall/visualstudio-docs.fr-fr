---
title: Live Unit Testing
description: En savoir plus sur les Live Unit Testing lors du développement d’applications, notamment sur les frameworks pris en charge et sur la configuration de Live Unit Testing.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: b9b78771c36dce26744ba74af63922cf1efa48e2
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798620"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Comment configurer et utiliser Live Unit Testing

Lorsque vous développez une application, Live Unit Testing exécute automatiquement tous les tests unitaires impactés en arrière-plan et présente les résultats et la couverture du code en temps réel. Lorsque vous modifiez votre code, Live Unit Testing fournit des commentaires sur l’impact de vos modifications sur les tests existants et vous indique si le code que vous avez ajouté est couvert par un ou plusieurs tests existants. Cela vous rappelle doucement d’écrire des tests unitaires au fur et à mesure que vous apportez des correctifs de bogues ou que vous ajoutez de nouvelles fonctionnalités.

> [!NOTE]
> Live Unit Testing est disponible pour les projets C# et Visual Basic qui ciblent .NET Core ou .NET Framework dans l’édition Enterprise de Visual Studio.

Lorsque vous utilisez Live Unit Testing pour vos tests, il conserve les données sur l’état de vos tests. L’utilisation de données persistantes permet à Live Unit Testing d’offrir des performances supérieures lors de l’exécution dynamique de vos tests en réponse aux modifications du code.

## <a name="supported-test-frameworks"></a>Frameworks de test pris en charge

Live Unit Testing fonctionne avec les trois frameworks de tests unitaires populaires listés dans le tableau suivant. La version minimale prise en charge de leurs adaptateurs et infrastructures est également indiquée. Les frameworks de tests unitaires sont tous disponibles dans NuGet.org.

|Framework de test  |Version minimale de l’adaptateur Visual Studio  |Version minimale du framework  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio version 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter version 3.5.1 |NUnit version 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Si vous avez des projets de test basés sur MSTest plus anciens qui référencent Microsoft. VisualStudio. QualityTools. UnitTestFramework et que vous ne souhaitez pas passer aux packages NuGet NuGet plus récents, effectuez une mise à niveau vers Visual Studio 2019 ou Visual Studio 2017.

Dans certains cas, vous devrez peut-être restaurer explicitement les packages NuGet référencés par un projet pour que les Live Unit Testing fonctionnent. Pour ce faire, vous pouvez effectuer une build explicite de la solution (sélectionnez **générer** la  >  **solution** dans le menu Visual Studio de niveau supérieur) ou restaurer des packages dans la solution (cliquez avec le bouton droit sur la solution et sélectionnez **restaurer les packages NuGet**).

## <a name="configure"></a>Configurer

Configurez Live Unit testing en sélectionnant **Outils**  >  **options** dans la barre de menus de niveau supérieur de Visual Studio, puis en sélectionnant **Live Unit testing** dans le volet gauche de la boîte de dialogue **options** .

> [!TIP]
> Une fois que Live Unit testing est activé (voir la section suivante, [Démarrer, suspendre et arrêter Live Unit testing](#start-pause-and-stop)), vous pouvez également ouvrir la boîte de dialogue **options** en sélectionnant **Tester**  >  **Live Unit testing**  >  **options**.

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

Pour activer Live Unit testing, sélectionnez **test**  >  **Live Unit testing**  >  **Démarrer** dans le menu Visual Studio de niveau supérieur. Lorsque Live Unit Testing est activé, les options disponibles dans le menu **Live Unit testing** sont modifiées à partir d’un seul élément, **Démarrer**, **suspendre** et **arrêter**:

- L' **interruption** interrompt temporairement Live Unit testing.

  Lorsque Live Unit Testing est suspendue, la visualisation de couverture n’apparaît pas dans l’éditeur, mais toutes les données collectées sont conservées. Pour réactiver Live Unit Testing, sélectionnez **Continuer** dans le menu Live Unit Testing. Live Unit Testing effectue le travail nécessaire pour rattraper toutes les modifications apportées pendant qu’il a été suspendu et met à jour les glyphes de manière appropriée.

- **Arrêter** arrête complètement Live Unit testing. Live Unit Testing abandonne toutes les données qu’il a collectées.

> [!NOTE]
> Si vous démarrez Live Unit Testing dans une solution qui n’inclut pas de projet de test unitaire, les options **suspendre** et **arrêter** s’affichent dans le menu **Live Unit testing** , mais Live Unit testing ne démarre pas. La fenêtre **sortie** affiche un message qui commence par « aucun adaptateur de test pris en charge n’est référencé par cette solution... ».

À tout moment, vous pouvez interrompre temporairement ou arrêter complètement Live Unit Testing. Vous pouvez effectuer cette opération, par exemple, si vous êtes au milieu d’une refactorisation et si vous savez que vos tests seront rompus pendant un certain temps.

## <a name="view-coverage-visualization"></a>Afficher la visualisation de la couverture

Une fois l’option activée, Live Unit Testing met à jour chaque ligne de code dans l’éditeur Visual Studio pour vous indiquer si le code que vous écrivez est couvert par les tests unitaires et si les tests qui le couvrent réussissent. L’image suivante montre des lignes de code avec les tests en réussite et en échec, ainsi que des lignes de code qui ne sont pas couvertes par les tests. Les lignes avec un symbole « ✓ » vert sont couvertes seulement par des tests ayant réussi, les lignes assorties d’un symbole « x » rouge sont couvertes par un ou plusieurs tests ayant échoué, et les lignes avec un symbole « ➖ » bleu ne sont couvertes par aucun test.

![Couverture du code dans Visual Studio](./media/lut-codewindow.png)

Live Unit Testing la visualisation de la couverture est mise à jour immédiatement lorsque vous modifiez le code dans l’éditeur de code. Lors du traitement des modifications, la visualisation change pour indiquer que les données ne sont pas à jour en ajoutant une image de minuteur ronde sous les symboles de réussite, d’échec et non couverts, comme le montre l’image suivante.

![Couverture du code dans Visual Studio avec l’icône de minuterie](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Obtenir des informations sur l’état des tests

En passant la souris sur le symbole de réussite ou d’échec dans la fenêtre de code, vous pouvez voir combien de tests ont atteint cette ligne. Pour afficher l’état des tests individuels, sélectionnez le symbole :

![État des tests pour un symbole dans Visual Studio](./media/lut-failedinfo.png)

En plus de fournir les noms et les résultats des tests, l’info-bulle vous permet de réexécuter ou de déboguer l’ensemble de tests. Si vous sélectionnez un ou plusieurs des tests dans l’infobulle, vous pouvez également exécuter ou déboguer uniquement ces tests. Cela vous permet de déboguer vos tests sans quitter la fenêtre de code. Lors du débogage, en plus d’observer les points d’arrêt que vous pouvez avoir déjà définis, l’exécution du programme s’interrompt lorsque le débogueur exécute une méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> qui retourne un résultat inattendu.

Lorsque vous passez la souris sur un test ayant échoué dans l’infobulle, celle-ci se développe pour fournir des informations supplémentaires sur l’échec, comme illustré dans l’image suivante. Pour accéder directement à un test ayant échoué, double-cliquez dessus dans l’info-bulle.

![Info des info-bulles de test ayant échoué dans Visual Studio](./media/lut-failedmsg.png)

Lorsque vous accédez au test qui a échoué, Live Unit Testing indique visuellement dans la signature de la méthode les tests qui ont :

- passé (indiqué par un becher demi-complet avec un « ✓ » vert)
- échec (un becher demi-complet avec un «» rouge 🞩 )
- ne sont pas impliquées dans le Live Unit Testing (un bécher à demi-totalité avec un « ➖ » bleu)

Les méthodes sans test n’affichent aucun un symbole. L’image suivante illustre les quatre types de méthodes.

![Méthodes de test dans Visual Studio avec le symbole de réussite ou d’échec](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnostiquer et corriger les échecs des tests

À partir du test qui a échoué, vous pouvez facilement déboguer le code du produit, apporter des modifications et continuer à développer votre application. Étant donné que Live Unit Testing s’exécute en arrière-plan, il n’est pas nécessaire d’arrêter et de redémarrer Live Unit Testing pendant le cycle de débogage, de modification et de reprise.

Par exemple, l’échec du test affiché dans l’image précédente était dû à une hypothèse incorrecte dans la méthode de test que les caractères non alphabétiques retournent lorsqu’ils sont `true` passés à la <xref:System.Char.IsLower%2A?displayProperty=fullName> méthode. Une fois que vous avez corrigé la méthode de test, tous les tests doivent réussir. Vous n’avez pas besoin de suspendre ou d’arrêter Live Unit Testing.

::: moniker range="vs-2017"
## <a name="test-explorer"></a>Explorateur de tests

L' **Explorateur de tests** fournit une interface qui vous permet d’exécuter et de déboguer des tests et d’analyser les résultats des tests. Live Unit Testing s’intègre à **l’Explorateur de tests**. Quand Live Unit Testing n’est pas activé ou quand il est arrêté, **l’Explorateur de tests** affiche l’état des tests unitaires lors de la dernière exécution d’un test. Des modifications apportées au code source nécessitent que vous réexécutiez les tests. En revanche, lorsque Live Unit Testing est activé, l’état des tests unitaires dans **l’Explorateur de tests** est mis à jour immédiatement. Vous n’avez pas besoin d’exécuter explicitement les tests unitaires.

> [!TIP]
> Ouvrez **Live Unit testing** en sélectionnant **tester**  >    >  l'**Explorateur de tests** Windows dans le menu Visual Studio de niveau supérieur.

Vous remarquerez peut-être dans la fenêtre de l' **Explorateur de tests** que certains tests sont dépassés. Par exemple, lorsque vous activez Live Unit Testing après l’ouverture d’un projet précédemment enregistré, la fenêtre de l' **Explorateur de tests** avait sorti tout sauf le test ayant échoué, comme le montre l’image suivante. Dans ce cas, Live Unit Testing a réexécuté le test qui a échoué, mais il n’a pas réexécuté les tests réussis. Cela est dû au fait que les données persistantes de Live Unit Testing indiquent qu’aucune modification n’a été apportée depuis la dernière exécution réussie des tests.

![Échec du test dans l’Explorateur de tests](media/lut-test-explorer.png)

Vous pouvez réexécuter tous les tests qui apparaissent estompés en sélectionnant les options **exécuter tout** ou **exécuter** dans le menu de l' **Explorateur de tests** . Ou sélectionnez un ou plusieurs tests dans le menu de l'  **Explorateur de tests** , cliquez avec le bouton droit, puis sélectionnez **exécuter les tests sélectionnés** ou **déboguer les tests sélectionnés** dans le menu contextuel. À mesure que les tests sont exécutés, ils sont déplacent vers le haut de la liste.

Il existe certaines différences entre l’exécution automatique des tests et la mise à jour des résultats de test de Live Unit Testing et l’exécution explicite des tests à partir de **l’Explorateur de tests**. Ces différences incluent :

- L’exécution ou le débogage des tests depuis la fenêtre de l’Explorateur de tests exécute des fichiers binaires standards tandis que Live Unit Testing exécute des fichiers binaires instrumentés.
- Live Unit Testing ne crée pas de domaine d’application pour exécuter des tests, mais exécute des tests à partir du domaine par défaut. Les tests exécutés depuis la fenêtre de **l’Explorateur de tests** créent un domaine d’application.
- Live Unit Testing exécute des tests dans chaque assembly de test de manière séquentielle. Dans la fenêtre **Explorateur de tests** , vous pouvez choisir d’exécuter plusieurs tests en parallèle.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Fenêtre Live Unit Testing

**Live Unit testing**, semblable à l' **Explorateur de tests**, fournit une interface qui vous permet d’exécuter et de déboguer des tests et d’analyser les résultats des tests. Lorsque Live Unit Testing est activé, l’état des tests unitaires dans l' **Explorateur de tests** est mis à jour immédiatement. Vous n’avez pas besoin d’exécuter explicitement les tests unitaires. Lorsque Live Unit Testing n’est pas activé ou est arrêté, **Live Unit testing** affiche l’état des tests unitaires lors de la dernière exécution d’un test. Une fois que vous avez redémarré Live Unit Testing, une modification du code source est nécessaire pour réexécuter les tests.

> [!TIP]
> Démarrez Live Unit testing en sélectionnant **test**  >  **Live Unit testing**  >  **Démarrer** dans le menu Visual Studio de niveau supérieur. Vous pouvez également ouvrir la fenêtre de **Live Unit testing** à l’aide de la fenêtre **Afficher** les  >  **autres**  >  **Live Unit testing** Windows.

Vous pouvez remarquer dans la fenêtre de **Live Unit testing** que certains tests sont sortis. Par exemple, lorsque vous arrêtez et redémarrez Live Unit Testing, la fenêtre de **Live Unit testing** grise tous les tests, comme le montre l’image suivante. Les résultats de tests dépassés indiquent que le test ne fait pas partie de la dernière série de tests unitaires en direct. Les tests ne s’exécutent que lorsqu’une modification apportée au test ou aux dépendances du test est détectée. Si aucune modification n’est apportée, l’exécution du test n’est pas obligatoire. Dans ce cas, le résultat du test grisé est toujours « à jour », bien qu’il ne fasse pas partie de la dernière exécution.

![Tests atténués dans l’Explorateur de tests](media/vs-2019/lut-test-explorer.png)

Vous pouvez réexécuter tous les tests qui apparaissent en fondu en modifiant le code.

Il existe certaines différences entre l’exécution automatique des tests et la mise à jour des résultats de test de Live Unit Testing et l’exécution explicite des tests à partir de **l’Explorateur de tests**. Ces différences incluent :

- L’exécution ou le débogage des tests depuis la fenêtre de l’Explorateur de tests exécute des fichiers binaires standards tandis que Live Unit Testing exécute des fichiers binaires instrumentés.
- Live Unit Testing ne crée pas de domaine d’application pour exécuter des tests, mais exécute des tests à partir du domaine par défaut. Les tests exécutés depuis la fenêtre de **l’Explorateur de tests** créent un domaine d’application.
- Live Unit Testing exécute des tests dans chaque assembly de test de manière séquentielle. Dans la fenêtre **Explorateur de tests** , vous pouvez choisir d’exécuter plusieurs tests en parallèle.
::: moniker-end

## <a name="large-solutions"></a>Solutions de grande taille

Si votre solution contient au moins 10 projets, Visual Studio affiche la boîte de dialogue suivante lorsque vous :

- Démarrer Live Unit Testing et il n’y a pas de données persistantes
- Sélectionnez **Outils**  >  **options**  >  **Live Unit testing**  >  **Supprimer les données persistantes**

![Boîte de dialogue Live Unit Testing pour les gros projets](media/lut-large-project.png)

La boîte de dialogue vous avertit que l’exécution dynamique d’un grand nombre de tests dans des projets volumineux peut avoir un impact considérable sur les performances. Si vous sélectionnez **OK**, Live Unit Testing exécute tous les tests de la solution. Si vous sélectionnez **Annuler**, vous pouvez sélectionner les tests à exécuter. La section suivante explique comment procéder.

## <a name="include-and-exclude-test-projects-and-test-methods&quot;></a>Inclure et exclure des projets de test et des méthodes de test

Pour les solutions comportant de nombreux projets de test, vous pouvez contrôler les projets et les méthodes individuelles d’un projet qui participent à Live Unit Testing. Par exemple, si vous disposez d’une solution avec des centaines de projets de test, vous pouvez sélectionner un ensemble ciblé de projets de test à inclure dans Live Unit Testing. Il existe plusieurs façons de procéder, selon que vous souhaitez exclure tous les tests du projet ou de la solution, inclure ou exclure la plupart des tests ou exclure des tests individuels. Live Unit Testing enregistre l’état d’inclusion/d’exclusion en tant que paramètre utilisateur et le conserve quand une solution est fermée puis ouverte à nouveau.

### <a name=&quot;exclude-all-tests-in-a-project-or-solution&quot;></a>Exclure tous les tests d’un projet ou d’une solution

Pour sélectionner les projets individuels dans les tests unitaires, procédez comme suit une fois Live Unit Testing démarré :

1. Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** et choisissez **Live Unit testing**  >  **exclure** pour exclure toute la solution.
1. Cliquez avec le bouton droit sur chaque projet de test que vous souhaitez inclure dans les tests, puis choisissez **Live Unit testing**  >  **inclure**.

### <a name=&quot;exclude-individual-tests-from-the-code-editor-window&quot;></a>Exclure des tests individuels de la fenêtre de l’éditeur de code

Vous pouvez utiliser la fenêtre de l’éditeur de code pour inclure ou exclure des méthodes de test. Cliquez avec le bouton droit sur la signature de la méthode de test dans la fenêtre de l’éditeur de code, puis sélectionnez l’une des options suivantes :

- **Live Unit testing**  >  **Inclure \<selected method>**
- **Live Unit testing**  >  **Exclure \<selected method>**
- **Live Unit testing**  >  **Exclure tout sauf \<selected method>**

### <a name=&quot;exclude-tests-programmatically&quot;></a>Exclure des tests par programmation

Vous pouvez appliquer l’attribut <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> pour exclure par programme des méthodes, des classes ou des structures de la génération de couverture dans Live Unit Testing.

Utilisez les attributs suivants pour exclure des méthodes individuelles de Live Unit Testing :

- Pour xUnit : `[Trait(&quot;Category&quot;, &quot;SkipWhenLiveUnitTesting")]`
- Pour NUnit : `[Category("SkipWhenLiveUnitTesting")]`
- Pour MSTest : `[TestCategory("SkipWhenLiveUnitTesting")]`

Utilisez les attributs suivants pour exclure l’intégralité d’un assembly de tests de Live Unit Testing :

- Pour xUnit : `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Pour NUnit : `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Pour MSTest : `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Voir aussi

- [Outils de test de code](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blog Live Unit Testing](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [FAQ Live Unit Testing](live-unit-testing-faq.yml)
- [Vidéo Channel 9 : Live Unit Testing dans Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
