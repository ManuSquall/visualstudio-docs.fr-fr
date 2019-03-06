---
title: Live Unit Testing
ms.date: 03/07/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 4e631c5b4d9b02b38939e6a1aba6337f633f83fa
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55921534"
---
# <a name="live-unit-testing-with-visual-studio-2017"></a>Live Unit Testing avec Visual Studio 2017

Au fil du développement d’une application, Live Unit Testing exécute automatiquement en arrière-plan tous les tests unitaires affectés, et présente en temps réel les résultats et la couverture du code dans l’IDE Visual Studio. Lorsque vous modifiez votre code, Live Unit Testing fournit des commentaires sur l’impact de vos modifications sur les tests existants et vous indique si le code que vous avez ajouté est couvert par un ou plusieurs tests existants. Cela vous rappellera d’écrire des tests unitaires lorsque vous créez des correctifs de bogues ou que vous ajoutez des fonctionnalités.

> [!NOTE]
> Live Unit Testing est disponible pour les projets Visual Basic et C# qui ciblent .NET Core ou le .NET Framework dans l’édition Enterprise de Visual Studio 2017.

Lorsque vous utilisez Live Unit Testing pour vos tests, Live Unit Testing conserve des données sur l’état de vos tests. La capacité de Live Unit Testing à utiliser des données persistantes lui permet d’offrir des performances supérieures lors de l’exécution de vos tests de façon dynamique en réponse à des modifications du code.

## <a name="supported-test-frameworks"></a>Frameworks de test pris en charge
Live Unit Testing fonctionne avec les trois frameworks de tests unitaires populaires listés dans le tableau suivant. La version minimale prise en charge des adaptateurs et des frameworks est également listée dans le tableau. Les frameworks de tests unitaires sont tous disponibles dans NuGet.org.

<table>
<tr>
   <th>Framework de test</th>
   <th>Version minimale de l’adaptateur Visual Studio</th>
   <th>Version minimale du framework</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio version 2.2.0-beta3-build1187</td>
   <td>xunit 1.9.2</td>
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter version 3.5.1</td>
   <td>NUnit version 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

Si vous avez des projets de test basés sur MSTest plus anciens qui référencent `Microsoft.VisualStudio.QualityTools.UnitTestFramework` et que vous ne souhaitez pas passer aux packages NuGet de MSTest plus récents, faites une mise à niveau vers Visual Studio 2017 version 15.4.

Dans certains cas, vous devez peut-être restaurer explicitement les packages NuGet référencés par les projets dans la solution pour que Live Unit Testing fonctionne. Pour ce faire, générez une version explicite de la solution (sélectionnez **Générer** > **Regénérer la solution** dans le menu de niveau supérieur de Visual Studio) ou restaurez les packages dans la solution (cliquez avec le bouton droit sur la solution et sélectionnez **Restaurer des packages NuGet**) avant d’activer Live Unit Testing.

## <a name="configure-live-unit-testing"></a>Configurer Live Unit Testing

Vous pouvez configurer Live Unit Testing en sélectionnant **Outils** > **Options** dans la barre de menus de niveau supérieur de Visual Studio, puis en sélectionnant **Live Unit Testing** dans le volet gauche de la boîte de dialogue **Options**.

> [!TIP]
> Une fois Live Unit Testing activé (consultez la section suivante, [Démarrage, interruption et arrêt de Live Unit Testing](#start-pause-and-stop-live-unit-testing), vous pouvez également ouvrir la boîte de dialogue **Options** en sélectionnant **Test** > **Live Unit Testing** > **Options**).

La figure suivante montre les options de configuration de Live Unit Testing disponibles dans la boîte de dialogue :

  ![Image](./media/lut-options.png)

Les options configurables sont les suivantes :

- Interruption de Live Unit Testing quand une solution est générée et déboguée.

- L’interruption de Live Unit Testing lorsque la batterie d’un système passe en dessous d’un seuil défini.

- L’exécution automatique de Live Unit Testing lorsqu’une solution est ouverte.

- Activation de la génération de commentaires de documentation XML et de symboles de débogage.

- Répertoire où stocker les données persistantes.

- Possibilité de supprimer toutes les données persistantes. Cette opération est utile lorsque Live Unit Testing se comporte de façon imprévisible ou inattendue, signe que des données persistantes ont été endommagées.

- L’intervalle après lequel un cas de test expire ; la valeur par défaut est 30 secondes.

- Le nombre maximal de processus de test que Live Unit Testing crée.

- La quantité maximale de mémoire que les processus Live Unit Testing peuvent consommer.

- Le niveau des informations écrites dans la fenêtre **Sortie** de Live Unit Testing.

   Les options incluent : aucune journalisation (**Aucune**), messages d’erreur uniquement (**Erreur**), erreur et messages d’information (**Info**, la valeur par défaut) ou tous les détails (**Commentaires**).

   Vous pouvez également afficher une sortie détaillée dans la fenêtre **Sortie** de Live Unit Testing en affectant la valeur « 1 » à une variable d’environnement utilisateur nommée `VS_UTE_DIAGNOSTICS`, puis en redémarrant Visual Studio.

   Pour capturer dans un fichier les messages détaillés du journal MSBuild à partir de Live Unit Testing, définissez la variable d’environnement utilisateur `LiveUnitTesting_BuildLog` en fonction du nom du fichier qui doit contenir le journal.

## <a name="start-pause-and-stop-live-unit-testing"></a>Démarrer, interrompre et arrêter Live Unit Testing

Pour activer Live Unit Testing, sélectionnez **Test** > **Live Unit Testing** > **Démarrer** dans le menu Visual Studio de niveau supérieur. Une fois Live Unit Testing activé, les options disponibles dans le menu **Live Unit Testing** changent à partir d’un seul élément, de **Démarrer** à **Pause**, **Arrêter** et **Réinitialiser le nettoyage**.

> [!NOTE]
> Si vous démarrez Live Unit Testing dans une solution qui n’inclut pas un projet de test unitaire, les options **Pause**, **Arrêter**, et **Réinitialiser** apparaissent dans le menu de **Live Unit Testing**, mais Live Unit Testing ne démarre pas. La fenêtre **Sortie** affiche un message qui commence par « Aucun adaptateur de test pris en charge n’est référencé par cette solution... »

À tout moment, vous pouvez interrompre temporairement ou arrêter complètement Live Unit Testing. Vous souhaiterez peut-être le faire si, par exemple, vous êtes en pleine refactorisation et que vous savez que vos tests seront incorrects pendant un certain temps. Les trois options du menu sont :

- **Pause**, qui permet d’interrompre temporairement Live Unit Testing.

    Lorsque Live Unit Testing est interrompu, votre visualisation de couverture n’apparaît pas dans l’éditeur, mais toutes les données collectées sont conservées. Pour réactiver Live Unit Testing, sélectionnez **Continuer** dans le menu Live Unit Testing. Live Unit Testing fait ce qu’il faut pour rattraper toutes les modifications apportées lorsqu’il était interrompu et met à jour les glyphes en conséquence.

- **Arrêter** permet d’arrêter complètement Live Unit Testing. Live Unit Testing abandonne toutes les données qu’il a collectées.

- **Réinitialiser le nettoyage**, qui interrompt Live Unit Testing, supprime les données persistantes et redémarre Live Unit Testing.

- **Options**, qui ouvre la boîte de dialogue **Options** décrite dans la section [Configurer Live Unit Testing](#configure-live-unit-testing).

## <a name="view-coverage-visualization-in-the-editor-as-you-type"></a>Afficher la visualisation de couverture dans l’éditeur à mesure que vous tapez

Une fois activé, Live Unit Testing met à jour chaque ligne de code dans l’éditeur Visual Studio pour vous indiquer si le code que vous écrivez est couvert par les tests unitaires et si les tests qui le couvrent réussissent.  La figure suivante montre les lignes de code avec des résultats positifs et négatifs aux tests, ainsi que les lignes de code qui ne sont pas couvertes par les tests. Les lignes avec un symbole « ✓ » vert sont couvertes seulement par des tests ayant réussi, les lignes assorties d’un symbole « x » rouge sont couvertes par un ou plusieurs tests ayant échoué, et les lignes avec un symbole « ➖ » bleu ne sont couvertes par aucun test.

  ![Image](./media/lut-codewindow.png)

La visualisation de couverture Live Unit Testing est immédiatement mise à jour lorsque vous modifiez le code dans l’éditeur de code. Lors du traitement des modifications, la visualisation change pour indiquer que les données ne sont pas à jour en ajoutant une image de minuteur en dessous des symboles de réussite, d’échec et de non-couverture, comme présenté dans la figure suivante.

  ![Image](./media/lut-codeupdating.png)

## <a name="get-information-on-successful-or-failed-tests"></a>Obtenir des informations sur les réussites et les échecs des tests

En passant la souris sur le symbole de réussite ou d’échec dans la fenêtre de code, vous pouvez voir combien de tests ont atteint cette ligne. Si vous cliquez sur le symbole, vous pouvez voir l’état de chaque test, comme le montre la figure suivante :

  ![Image](./media/lut-failedinfo.png)

En plus de fournir les noms et les résultats des tests, l’infobulle vous permet de réexécuter l’ensemble des tests et d’exécuter cet ensemble des tests à l’aide du débogueur. Si vous sélectionnez un ou plusieurs des tests dans l’infobulle, vous pouvez également exécuter ou déboguer uniquement ces tests. Cela vous permet de déboguer vos tests sans quitter la fenêtre de code. Lors du débogage, en plus d’observer les points d’arrêt que vous pouvez avoir déjà définis, l’exécution du programme s’interrompt lorsque le débogueur exécute une méthode [`Assert`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert) qui retourne un résultat inattendu.

Lorsque vous passez la souris sur un test ayant échoué dans l’infobulle, celle-ci se développe pour fournir des informations supplémentaires sur l’échec, comme illustré dans l’image suivante. Si vous double-cliquez sur le test ayant échoué dans l’infobulle, vous pouvez y accéder directement.

  ![Image](./media/lut-failedmsg.png)

Quand vous accédez au test ayant échoué, Live Unit Testing indique également visuellement dans la signature de la méthode les tests qui ont réussi (signalés par un bécher à moitié plein avec un symbole vert « ✓ »), qui ont échoué (un bécher à moitié plein avec un symbole rouge « 🞩 »), ou ceux qui ne sont pas couverts par Live Unit Testing (bécher à moitié plein avec un symbole bleu « ➖ »). Les méthodes sans test n’affichent aucun un symbole. La figure suivante montre les quatre types de méthodes.

  ![Image](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnostiquer et corriger les échecs des tests

À partir du test ayant échoué, vous pouvez facilement déboguer le code du produit, apporter des modifications et continuer à développer votre application. Étant donné que Live Unit Testing s’exécute en arrière-plan, il est inutile d’arrêter et de redémarrer Live Unit Testing pendant le débogage. Il vous suffit d’apporter les modifications et de continuer le cycle.

Par exemple, l’échec du test présenté à la figure précédente est dû à une hypothèse incorrecte dans la méthode de test stipulant que les caractères non alphabétiques renvoient `true` lorsqu’ils sont transmis à la méthode <xref:System.Char.IsLower%2A?displayProperty=fullName>. Une fois la méthode de test corrigée, nous pouvons nous apercevoir que tous les tests réussissent. Lors de ces opérations, nous n’avons pas besoin d’interrompre ni d’arrêter Live Unit Testing.

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing et l’Explorateur de tests

En règle générale, **l’Explorateur de tests** fournit l’interface qui vous permet d’exécuter, de déboguer et d’analyser vos résultats de test. Live Unit Testing s’intègre à **l’Explorateur de tests**. Quand Live Unit Testing n’est pas activé ou quand il est arrêté, **l’Explorateur de tests** affiche l’état des tests unitaires lors de la dernière exécution d’un test. Des modifications apportées au code source nécessitent que vous réexécutiez les tests. En revanche, lorsque Live Unit Testing est activé, l’état des tests unitaires dans **l’Explorateur de tests** est mis à jour immédiatement. Vous n’avez plus besoin d’exécuter explicitement vos tests unitaires.

> [!NOTE]
> Vous pouvez ouvrir **l’Explorateur de tests** en sélectionnant **Test** > **Windows** > **Explorateur de tests** dans le menu Visual Studio de niveau supérieur.

Vous pouvez remarquer que certains tests sont grisés dans **l’Explorateur de tests**. Par exemple, lorsque vous activez Live Unit Testing après l’ouverture d’un projet enregistré précédemment, **l’Explorateur de tests** affiche en grisé tous les tests à l’exception de ceux qui ont échoué, comme le montre l’illustration suivante. Dans ce cas, Live Unit Testing a réexécuté le test ayant échoué mais pas ceux qui ont réussi car les données persistantes de Live Unit Testing indiquent qu’aucune modification n’a été apportée depuis la dernière exécution réussie des tests.

  ![Image](media/lut-test-explorer.png)

Vous pouvez réexécuter tous les tests qui apparaissent en grisé en sélectionnant l’option **Exécuter tout** ou **Exécuter** dans le menu **Explorateur de tests**, ou en sélectionnant un ou plusieurs tests dans le menu **Explorateur de tests**, puis en cliquant avec le bouton droit pour sélectionner l’option **Exécuter les tests sélectionnés** ou **Déboguer les tests sélectionnés** dans le menu contextuel. À mesure que les tests sont exécutés, ils sont déplacent vers le haut de la liste.

Il existe certaines différences entre l’exécution automatique des tests et la mise à jour des résultats de test de Live Unit Testing et l’exécution explicite des tests à partir de **l’Explorateur de tests**. Ces différences incluent :

- L’exécution ou le débogage des tests depuis la fenêtre de l’Explorateur de tests exécute des fichiers binaires réguliers, tandis que Live Unit Testing exécute des fichiers binaires instrumentés.
- Live Unit Testing ne crée pas de domaine d’application pour exécuter des tests, mais exécute des tests à partir du domaine par défaut. Les tests exécutés depuis la fenêtre de **l’Explorateur de tests** créent un domaine d’application.
- Live Unit Testing exécute des tests dans chaque assembly de test de manière séquentielle. Si vous exécutez plusieurs tests depuis la fenêtre de **l’Explorateur de tests** et si le bouton **Exécuter les tests en parallèle** est sélectionné, les tests sont exécutés en parallèle.

## <a name="live-unit-testing-and-large-solutions"></a>Live Unit Testing et les grandes solutions

Si votre solution contient 10 projets ou plus, lorsque vous démarrez Live Unit Testing en l’absence de données persistantes ou que vous sélectionnez l’option **Test** > **Live Unit Testing** > **Réinitialiser et nettoyer** dans le menu Visual Studio de niveau supérieur, Visual Studio affiche la boîte de dialogue suivante pour vous avertir que l’exécution dynamique d’un grand nombre de tests dans de gros projets peut impacter sérieusement les performances. Si vous sélectionnez **OK**, Live Unit Testing exécute tous les tests de la solution. Si vous sélectionnez **Annuler**, vous pouvez sélectionner les tests à exécuter. Pour plus d’informations à ce sujet, consultez la section suivante, [Inclure et exclure des projets de test et des méthodes de test](#include-and-exclude-test-projects-and-test-methods).

 ![Boîte de dialogue Live Unit Testing pour les gros projets](media/lut-large-project.png)

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Inclure et exclure des projets de test et des méthodes de test

Pour les solutions comptant de nombreux projets de test, vous pouvez contrôler les projets et les méthodes individuelles d’un projet à inclure dans Live Unit Testing. Par exemple, si vous disposez d’une solution avec des centaines de projets de test, vous pouvez sélectionner un ensemble ciblé de projets de test à inclure dans Live Unit Testing. Il existe plusieurs manières de procéder, selon que vous souhaitez exclure tous les tests du projet ou de la solution, inclure ou exclure la plupart des tests, ou exclure des tests individuellement. Live Unit Testing enregistre l’état d’inclusion/d’exclusion en tant que paramètre utilisateur et le conserve quand une solution est fermée puis ouverte à nouveau.

**Exclusion de tous les tests d’un projet ou d’une solution**

Pour sélectionner les projets individuels dans les tests unitaires, procédez comme suit une fois Live Unit Testing démarré :

1.  Cliquez avec le bouton droit sur la solution dans **l’Explorateur de solutions** et choisissez **Live Tests** > **Exclure** pour exclure toute la solution.
1.  Cliquez avec le bouton droit sur chaque projet de test à inclure dans les tests et choisissez **Live Tests** > **Inclure**.

**Exclusion de tests individuels de la fenêtre de l’éditeur de code**

Vous pouvez utiliser la fenêtre de l’éditeur de code pour inclure ou exclure des méthodes de test. Cliquez avec le bouton droit sur la signature de la méthode de test dans la fenêtre de l’éditeur de code, puis sélectionnez **Live Tests** > **Inclure [la méthode sélectionnée]**, **Live Tests** > **Exclure [la méthode sélectionnée]** ou **Live Tests** > **Exclure tout sauf [la méthode sélectionnée]**, où « la méthode sélectionnée » correspond à celle que vous avez sélectionnée dans la fenêtre de code.

**Exclusion de tests par programmation**

Vous pouvez appliquer l’attribut <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> pour exclure par programme des méthodes, des classes ou des structures de la génération de couverture dans Live Unit Testing.

Vous pouvez également utiliser les attributs suivants pour exclure des méthodes individuelles de Live Unit Testing :

- Pour xUnit : `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Pour NUnit : `[Category("SkipWhenLiveUnitTesting")]`
- Pour MSTest : `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Voir aussi

- [Outils de test de code](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blog sur Live Unit Testing](https://go.microsoft.com/fwlink/?linkid=842514)
- [FAQ Live Unit Testing](live-unit-testing-faq.md)
- [Vidéo Channel 9 : Live Unit Testing dans Visual Studio 2017](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
