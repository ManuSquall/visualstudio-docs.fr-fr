---
title: Live Unit Testing
ms.date: 03/07/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: 1e1a0ec1fd6f2fbdf4f016b1d22db5a6929b5e24
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75851442"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Comment configurer et utiliser live Unit Testing

Au fur et à mesure que vous développez une application, Live Unit Testing exécute automatiquement tous les tests unitaires impactés en arrière-plan et présente les résultats et la couverture du code en temps réel. Lorsque vous modifiez votre code, Live Unit Testing fournit des commentaires sur l’impact de vos modifications sur les tests existants et vous indique si le code que vous avez ajouté est couvert par un ou plusieurs tests existants. Cela vous rappelle doucement d’écrire des tests unitaires que vous faites des correctifs bug ou l’ajout de nouvelles fonctionnalités.

> [!NOTE]
> Live Unit Testing est disponible pour les projets C et Visual Basic qui ciblent .NET Core ou .NET Framework dans l’édition Enterprise de Visual Studio.

Lorsque vous utilisez Live Unit Testing pour vos tests, il persiste des données sur l’état de vos tests. L’utilisation de données persistantes permet aux tests d’unité en direct d’offrir des performances supérieures tout en exécutant vos tests de manière dynamique en réponse aux modifications de code.

## <a name="supported-test-frameworks"></a>Frameworks de test pris en charge

Live Unit Testing fonctionne avec les trois frameworks de tests unitaires populaires listés dans le tableau suivant. La version minimale prise en charge de leurs adaptateurs et cadres est également affichée. Les frameworks de tests unitaires sont tous disponibles dans NuGet.org.

|Framework de test  |Version minimale de l’adaptateur Visual Studio  |Version minimale du framework  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio version 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter version 3.5.1 |NUnit version 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Si vous avez d’anciens projets de test basés sur MSTest qui font référence à Microsoft.VisualStudio.QualityTools.UnitTestFramework, et que vous ne souhaitez pas passer aux nouveaux forfaits MSTest NuGet, passez à Visual Studio 2019 ou Visual Studio 2017.

Dans certains cas, vous devrez peut-être restaurer explicitement les paquets NuGet référencés par un projet afin que les tests d’unité en direct fonctionnent. Vous pouvez le faire soit en faisant une version explicite de la solution (sélectionnez **Build** > **Rebuild Solution** à partir du menu Visual Studio de haut niveau) ou en rétablissant des paquets dans la solution (cliquez à droite sur la solution et sélectionnez Restaurer les **paquets NuGet**).

## <a name="configure"></a>Configurer

Configurez live Unit Testing en sélectionnant des**options** **d’outils** > à partir de la barre de menu Visual Studio de haut niveau, puis en sélectionnant **les tests d’unité en direct** dans le volet gauche du dialogue **Options.**

> [!TIP]
> Après que le test d’unité en direct est activé (voir la section suivante, [Démarrer, faire une pause et arrêter les tests d’unité en direct),](#start-pause-and-stop)vous pouvez également ouvrir le dialogue **Options** **en** > sélectionnant les > **options**de**test d’unité en direct**.

L’image suivante montre les options de configuration de test d’unité en direct disponibles dans le dialogue :

![Options de configuration de test d’unité en direct](./media/lut-options.png)

Les options configurables sont les suivantes :

- Interruption de Live Unit Testing quand une solution est générée et déboguée.

- L’interruption de Live Unit Testing lorsque la batterie d’un système passe en dessous d’un seuil défini.

- L’exécution automatique de Live Unit Testing lorsqu’une solution est ouverte.

- Activation de la génération de commentaires de documentation XML et de symboles de débogage.

- Répertoire où stocker les données persistantes.

- Possibilité de supprimer toutes les données persistantes. Ceci est utile lorsque Live Unit Testing se comporte d’une manière imprévisible ou inattendue, ce qui suggère que les données persistantes sont devenues corrompues.

- L’intervalle après lequel un cas de test s’évanouit. La valeur par défaut est de 30 secondes.

- Le nombre maximal de processus de test que Live Unit Testing crée.

- La quantité maximale de mémoire que les processus Live Unit Testing peuvent consommer.

- Le niveau des informations écrites dans la fenêtre **Sortie** de Live Unit Testing.

   Les options incluent : aucune journalisation (**Aucune**), messages d’erreur uniquement (**Erreur**), erreur et messages d’information (**Info**, la valeur par défaut) ou tous les détails (**Commentaires**).

   Vous pouvez également afficher une sortie détaillée dans la fenêtre **Sortie** de Live Unit Testing en affectant la valeur « 1 » à une variable d’environnement utilisateur nommée `VS_UTE_DIAGNOSTICS`, puis en redémarrant Visual Studio.

   Pour capturer dans un fichier les messages détaillés du journal MSBuild à partir de Live Unit Testing, définissez la variable d’environnement utilisateur `LiveUnitTesting_BuildLog` en fonction du nom du fichier qui doit contenir le journal.

## <a name="start-pause-and-stop"></a>Commencez, faites une pause et arrêtez-vous

Pour activer les tests d’unités en direct, sélectionnez **Test** > **Live Unit Testing** > **Start à** partir du menu Visual Studio de haut niveau. Lorsque les tests d’unité en direct sont activés, les options disponibles sur le menu **De test d’unité en direct** changent d’un seul élément, **Démarrer,** **faire une pause** et **arrêter**:

- **Pause** suspend temporairement les tests d’unité en direct.

  Lorsque le test d’unité en direct est interrompu, la visualisation de la couverture n’apparaît pas dans l’éditeur, mais toutes les données recueillies sont conservées. Pour réactiver Live Unit Testing, sélectionnez **Continuer** dans le menu Live Unit Testing. Live Unit Testing fait le travail nécessaire pour rattraper toutes les modifications qui ont été apportées pendant qu’il était en pause et met à jour les glyphes de manière appropriée.

- **Stop** arrête complètement les tests d’unité en direct. Live Unit Testing abandonne toutes les données qu’il a collectées.

> [!NOTE]
> Si vous commencez à tester en direct dans une solution qui n’inclut pas un projet de test unitaire, les options **Pause** et **Stop** apparaissent sur le menu **de test d’unité en direct,** mais les tests d’unité en direct ne démarrent pas. La fenêtre **Output** affiche un message qui commence : « Aucun adaptateur de test pris en charge n’est référencé par cette solution...

À tout moment, vous pouvez interrompre temporairement ou arrêter complètement Live Unit Testing. Vous voudrez peut-être le faire, par exemple, si vous êtes au milieu d’une refactoration et sachez que vos tests seront interrompus pendant un certain temps.

## <a name="view-coverage-visualization"></a>Afficher la visualisation de la couverture

Une fois qu’il est activé, Live Unit Testing met à jour chaque ligne de code de l’éditeur Visual Studio pour vous montrer si le code que vous écrivez est couvert par des tests unitaires et si les tests qui le couvrent sont en cours de passage. L’image suivante montre des lignes de code avec des tests de passage et d’échec, ainsi que des lignes de code qui ne sont pas couvertes par des tests. Les lignes avec un symbole « ✓ » vert sont couvertes seulement par des tests ayant réussi, les lignes assorties d’un symbole « x » rouge sont couvertes par un ou plusieurs tests ayant échoué, et les lignes avec un symbole « ➖ » bleu ne sont couvertes par aucun test.

![Couverture du code dans Visual Studio](./media/lut-codewindow.png)

La visualisation de la couverture de test unitaire en direct est mise à jour immédiatement lorsque vous modifiez le code dans l’éditeur de code. Pendant le traitement des modifications, la visualisation change pour indiquer que les données ne sont pas à jour en ajoutant une image de minuterie ronde en dessous des symboles de passage, d’échec et non couverts, comme le montre l’image suivante.

![Couverture de code dans Visual Studio avec icône de minuterie](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Obtenir des informations sur l’état du test

En passant la souris sur le symbole de réussite ou d’échec dans la fenêtre de code, vous pouvez voir combien de tests ont atteint cette ligne. Pour voir l’état des tests individuels, sélectionnez le symbole :

![Statut de test pour un symbole dans Visual Studio](./media/lut-failedinfo.png)

En plus de fournir les noms et le résultat des tests, l’outil vous permet de rediffuser ou de déboquer l’ensemble des tests. Si vous sélectionnez un ou plusieurs des tests dans l’infobulle, vous pouvez également exécuter ou déboguer uniquement ces tests. Cela vous permet de déboguer vos tests sans quitter la fenêtre de code. Lors du débogage, en plus d’observer les points d’arrêt que vous pouvez avoir déjà définis, l’exécution du programme s’interrompt lorsque le débogueur exécute une méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> qui retourne un résultat inattendu.

Lorsque vous passez la souris sur un test ayant échoué dans l’infobulle, celle-ci se développe pour fournir des informations supplémentaires sur l’échec, comme illustré dans l’image suivante. Pour naviguer directement vers un test raté, cliquez deux fois sur lui dans l’outiltip.

![Informations sur l’outil de test échoué dans Visual Studio](./media/lut-failedmsg.png)

Lorsque vous naviguez vers le test échoué, Live Unit Testing indique visuellement dans la signature de la méthode les tests qui ont:

- passé (indiqué par un bécher à moitié plein avec un vert "")
- échoué (un bécher demi-plein avec🞩un rouge " ")
- ne sont pas impliqués dans les tests d’unité en direct (un bécher à moitié plein avec un bleu "➖")

Les méthodes sans test n’affichent aucun un symbole. L’image suivante illustre les quatre types de méthodes.

![Méthodes d’essai dans Visual Studio avec symbole de passage ou d’échec](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnostiquer et corriger les échecs des tests

À partir du test échoué, vous pouvez facilement déboiffer le code produit, faire des modifications et continuer à développer votre application. Étant donné que le test d’unité en direct s’exécute en arrière-plan, vous n’avez pas à vous arrêter et redémarrer les tests d’unité en direct pendant le débogé, modifier et continuer le cycle.

Par exemple, l’échec du test indiqué dans l’image précédente a été causé `true` par une <xref:System.Char.IsLower%2A?displayProperty=fullName> hypothèse incorrecte dans la méthode de test que les caractères non alphabétique reviennent lorsqu’ils sont transmis à la méthode. Après avoir corrigé la méthode de test, tous les tests doivent passer. Vous n’avez pas à faire une pause ou arrêter les tests d’unité en direct.

## <a name="test-explorer"></a>Explorateur de tests

**Test Explorer** fournit une interface qui vous permet d’exécuter et de déboguer des tests et d’analyser les résultats des tests. Live Unit Testing s’intègre à **l’Explorateur de tests**. Quand Live Unit Testing n’est pas activé ou quand il est arrêté, **l’Explorateur de tests** affiche l’état des tests unitaires lors de la dernière exécution d’un test. Des modifications apportées au code source nécessitent que vous réexécutiez les tests. En revanche, lorsque Live Unit Testing est activé, l’état des tests unitaires dans **l’Explorateur de tests** est mis à jour immédiatement. Vous n’avez pas besoin d’exécuter explicitement les tests unitaires.

> [!TIP]
> Ouvrez **Test Explorer** en sélectionnant **Test** > **Windows** > Test**Explorer** à partir du menu Visual Studio de haut niveau.

Vous remarquerez peut-être dans la fenêtre **Test Explorer** que certains tests sont effacés. Par exemple, lorsque vous activez live Unit Testing après l’ouverture d’un projet précédemment enregistré, la fenêtre **Test Explorer** s’était évanouie, sauf le test échoué, comme le montre l’image suivante. Dans ce cas, Live Unit Testing a réexécuté le test échoué, mais il n’a pas réexécuté les tests réussis. C’est parce que les données persistantes de Live Unit Testing indiquent qu’il n’y a eu aucun changement depuis la dernière exécution des tests.

![Test échoué dans Test Explorer](media/lut-test-explorer.png)

Vous pouvez réexécuter tous les tests qui semblent fanés en sélectionnant les options **Run All** or **Run** dans le menu **Test Explorer.** Ou, sélectionnez un ou plusieurs tests dans le menu **Test Explorer,** cliquez à droite, puis sélectionnez **Des tests sélectionnés ou** des tests **sélectionnés Debug** dans le menu popup. À mesure que les tests sont exécutés, ils sont déplacent vers le haut de la liste.

Il existe certaines différences entre l’exécution automatique des tests et la mise à jour des résultats de test de Live Unit Testing et l’exécution explicite des tests à partir de **l’Explorateur de tests**. Ces différences incluent :

- L’exécution ou le débogage des tests depuis la fenêtre de l’Explorateur de tests exécute des fichiers binaires standards tandis que Live Unit Testing exécute des fichiers binaires instrumentés.
- Live Unit Testing ne crée pas de domaine d’application pour exécuter des tests, mais exécute des tests à partir du domaine par défaut. Les tests exécutés depuis la fenêtre de **l’Explorateur de tests** créent un domaine d’application.
- Live Unit Testing exécute des tests dans chaque assembly de test de manière séquentielle. Dans la fenêtre **Test Explorer,** vous pouvez choisir d’exécuter plusieurs tests en parallèle.

## <a name="large-solutions"></a>Grandes solutions

Si votre solution a 10 projets ou plus, Visual Studio affiche le dialogue suivant lorsque vous :

- commencer les tests d’unité en direct et il n’y a pas de données persistantes
- sélectionner **les options d’outils** > **Options** > **Live Unit Testing** > **Supprimer les données persistées**

![Boîte de dialogue Live Unit Testing pour les gros projets](media/lut-large-project.png)

Le dialogue vous avertit que l’exécution dynamique d’un grand nombre de tests dans de grands projets peut avoir un impact sévère sur les performances. Si vous sélectionnez **OK**, Live Unit Testing exécute tous les tests de la solution. Si vous sélectionnez **Annuler**, vous pouvez sélectionner les tests à exécuter. La section suivante explique comment le faire.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Inclure et exclure des projets de test et des méthodes de test

Pour trouver des solutions avec de nombreux projets d’essai, vous pouvez contrôler quels projets et méthodes individuelles d’un projet participent à des tests d’unités en direct. Par exemple, si vous disposez d’une solution avec des centaines de projets de test, vous pouvez sélectionner un ensemble ciblé de projets de test à inclure dans Live Unit Testing. Il existe un certain nombre de façons de le faire, selon que vous souhaitez exclure tous les tests du projet ou de la solution, inclure ou exclure la plupart des tests, ou exclure les tests individuels. Live Unit Testing enregistre l’état d’inclusion/d’exclusion en tant que paramètre utilisateur et le conserve quand une solution est fermée puis ouverte à nouveau.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Exclure tous les tests d’un projet ou d’une solution

Pour sélectionner les projets individuels dans les tests unitaires, procédez comme suit une fois Live Unit Testing démarré :

1. Cliquez avec le bouton droit sur la solution dans **l’Explorateur de solutions** et choisissez **Live Tests** > **Exclure** pour exclure toute la solution.
1. Cliquez à droite sur chaque projet de test que vous souhaitez inclure dans les tests et choisissez **des tests** > en direct**Inclure**.

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Exclure les tests individuels de la fenêtre de l’éditeur de code

Vous pouvez utiliser la fenêtre de l’éditeur de code pour inclure ou exclure des méthodes de test. Cliquez à droite sur la signature de la méthode de test dans la fenêtre de l’éditeur de code, puis sélectionnez l’une des options suivantes :

- **Les tests** > en direct**comprennent \<une méthode sélectionnée>**
- **Tests en direct** > **Excluent \<la méthode sélectionnée>**
- **Les tests** > en direct**excluent toutes les méthodes mais \<sélectionnées>**

### <a name="exclude-tests-programmatically"></a>Exclure les tests programmatiquement

Vous pouvez appliquer l’attribut <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> pour exclure par programme des méthodes, des classes ou des structures de la génération de couverture dans Live Unit Testing.

Utilisez les attributs suivants pour exclure les méthodes individuelles des tests d’unité en direct :

- Pour xUnit : `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Pour NUnit : `[Category("SkipWhenLiveUnitTesting")]`
- Pour MSTest : `[TestCategory("SkipWhenLiveUnitTesting")]`

Utilisez les attributs suivants pour exclure un ensemble entier de tests de tests d’unité en direct :

- Pour xUnit : `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Pour NUnit : `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Pour MSTest : `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Voir aussi

- [Outils de test de code](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Live Unit Testing blog](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [FaQ de test d’unité en direct](live-unit-testing-faq.md)
- [Channel 9 vidéo: Live Unit Testing in Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
