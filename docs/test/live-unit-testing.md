---
title: Live Unit Testing dans Visual Studio | Microsoft Docs
ms.date: 2017-03-07
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
ms.assetid: 5b51fb96-94f4-4926-92b9-262156c05b85
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: c559290c8e88c8b4e37feabc7014188fad15434d
ms.openlocfilehash: 0a939044b9806236cf55333c30bce24ae0fdb28a
ms.contentlocale: fr-fr
ms.lasthandoff: 06/08/2017

---

# <a name="live-unit-testing-with-visual-studio-2017"></a>Live Unit Testing avec Visual Studio 2017

Lorsque vous développez une application, Live Unit Testing exécute automatiquement tous les tests unitaires affectés en arrière-plan et présente les résultats et la couverture du code dans l’IDE de Visual Studio en temps réel. Lorsque vous modifiez votre code, Live Unit Testing fournit des commentaires sur l’impact de vos modifications sur les tests existants et vous indique si le code que vous avez ajouté est couvert par un ou plusieurs tests existants. Cela vous rappellera d’écrire des tests unitaires lorsque vous créez des correctifs de bogues ou que vous ajoutez des fonctionnalités.

> [!NOTE]
> Live Unit Testing est disponible pour les projets Visual Basic et C# qui ciblent .NET Core ou le .NET Framework dans l’édition Enterprise de Visual Studio 2017.

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
   <td>xunit 2.0</td> 
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter version 3.5.1</td>  
   <td>NUnit version 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.11</td>
   <td>MSTest.TestFramework 1.1.11</td>
</tr>
</table>

Si vous avez d’anciennes références de framework de test et d’adaptateur issues de vos projets existants, veillez à les supprimer. (Veillez à supprimer la référence à `Microsoft.VisualStudio.QualityTools.UnitTestFramework`, si vous utilisez MSTest.) Ajoutez les nouvelles références si Live Unit Testing ne fonctionne pas pour vous. 

Dans certains cas, vous devez peut-être restaurer explicitement les packages NuGet référencés par les projets dans la solution pour que Live Unit Testing fonctionne. Pour ce faire, générez une version explicite de la solution (sélectionnez **Générer**, **Régénérer la solution** à partir du menu de Visual Studio de niveau supérieur) ou restaurez les packages dans la solution (cliquez avec le bouton droit sur la solution et sélectionnez **Restaurer des packages NuGet**) avant d’activer Live Unit Testing. 

#   <a name="configuring-live-unit-testing"></a>Configuration de Live Unit Testing

Vous pouvez configurer Live Unit Testing en sélectionnant **Outils**, **Options** à partir du menu de Visual Studio de niveau supérieur, puis en sélectionnant **Live Unit Testing** dans le volet gauche de la boîte de dialogue **Options**. La figure suivante montre les options de configuration disponibles de Live Unit Testing disponibles dans la boîte de dialogue.

  ![Image](./media/lut-options.png)

Les options configurables sont les suivantes :

- L’exécution automatique de Live Unit Testing lorsqu’une solution est ouverte.
- L’interruption de Live Unit Testing lorsqu’une solution est générée et déboguée ou lorsque la batterie d’un système passe en dessous d’un seuil défini.
- L’intervalle après lequel un cas de test expire ; la valeur par défaut est 30 secondes. 
- Le nombre de processus de test que Live Unit Testing crée. 
- Le niveau des informations écrites dans la fenêtre **Sortie** de Live Unit Testing. Les options incluent : aucune journalisation (Aucune), messages d’erreur uniquement (Erreur), erreur et messages d’information (Info, la valeur par défaut) ou tous les détails (Commentaires).

Vous pouvez également afficher une sortie détaillée dans la fenêtre **Sortie** de Live Unit Testing en affectant une valeur de « 1 » à une variable d’environnement au niveau de l’utilisateur nommée `VS_UTE_DIAGNOSTICS` et en redémarrant Visual Studio. 

Pour capturer les messages détaillés du journal MSBuild depuis Live Unit Testing vers un fichier, définissez la variable d’environnement au niveau de l’utilisateur `LiveUnitTesting_BuildLog` sur le nom du fichier qui contiendra le journal.

## <a name="starting-pausing-and-stopping-live-unit-testing"></a>Démarrage, interruption et arrêt de Live Unit Testing

Pour activer Live Unit Testing, sélectionnez **Tester **, **Live Unit Testing**, **Démarrer** dans le menu Visual Studio de niveau supérieur. Une fois Live Unit Testing activé, les options disponibles dans le menu **Live Unit Testing** changent à partir d’un seul élément, de **Démarrer** à **Pause**, **Arrêter** et **Redémarrer**.

À tout moment, vous pouvez interrompre temporairement ou arrêter complètement Live Unit Testing. Vous souhaiterez peut-être le faire si, par exemple, vous êtes en pleine refactorisation et que vous savez que vos tests seront incorrects pendant un certain temps. Les trois options du menu sont :

- **Pause**, qui permet d’interrompre temporairement Live Unit Testing. 
    Lorsque Live Unit Testing est interrompu, votre visualisation de couverture n’apparaît pas dans l’éditeur, mais toutes les données collectées sont conservées. Pour réactiver Live Unit Testing, sélectionnez « Continuer » dans le menu Live Unit Testing. Live Unit Testing fera ce qu’il faut pour rattraper toutes les modifications apportées lorsqu’il était interrompu et mettra à jour les glyphes en conséquence. 
- **Arrêter** permet d’arrêter complètement Live Unit Testing. Live Unit Testing abandonne toutes les données qu’il a collectées.
- **Redémarrer** équivaut à sélectionner **Arrêter**, puis **Démarrer** dans le menu **Live Unit Testing**.

##  <a name="viewing-coverage-visualization-in-the-editor-as-you-type"></a>Affichage de la visualisation de couverture dans l’éditeur à mesure que vous tapez

Une fois activé, Live Unit Testing met à jour chaque ligne de code dans l’éditeur Visual Studio pour vous indiquer si le code que vous écrivez est couvert par les tests unitaires et si les tests qui le couvrent réussissent.  La figure suivante montre les lignes de code avec des résultats positifs et négatifs aux tests, ainsi que les lignes de code qui ne sont pas couvertes par les tests. Les lignes avec un symbole « ✓ » vert sont couvertes uniquement par les tests ayant réussi, les lignes assorties d’un symbole « 🞩 » rouge sont couvertes par un ou plusieurs tests ayant échoué et les lignes avec un symbole «  » bleu ne sont couvertes par aucun test.

  ![Image](./media/lut-codewindow.png)

La visualisation de couverture Live Unit Testing est immédiatement mise à jour lorsque vous modifiez le code dans l’éditeur de code. Lors du traitement des modifications, la visualisation change pour indiquer que les données ne sont pas à jour en ajoutant une image de minuteur en dessous des symboles de réussite, d’échec et de non-couverture, comme présenté dans la figure suivante.

  ![Image](./media/lut-codeupdating.png)
 
## <a name="getting-information-on-successful-or-failed-tests"></a>Obtention d’informations sur les réussites ou les échecs aux tests

En passant la souris sur le symbole de réussite ou d’échec dans la fenêtre de code, vous pouvez voir combien de tests ont atteint cette ligne. Si vous cliquez sur le symbole, vous pouvez voir l’état de chaque test, comme le montre la figure suivante.
 
  ![Image](./media/lut-failedinfo.png) 

Lorsque vous passez la souris sur le test ayant échoué dans l’info-bulle, celle-ci se développe pour fournir des informations supplémentaires sur l’échec, comme illustré dans l’image ci-dessous. Si vous cliquez sur le test ayant échoué dans l’info-bulle, vous pouvez y accéder directement.

  ![Image](./media/lut-failedmsg.png) 

## <a name="diagnosing-and-correcting-test-failures"></a>Diagnostics et corrections des échecs aux tests

À partir du test ayant échoué, vous pouvez facilement déboguer le code du produit, apporter des modifications et continuer à développer votre application. Étant donné que Live Unit Testing s’exécute en arrière-plan, il est inutile d’arrêter et de redémarrer Live Unit Testing pendant le débogage. Il vous suffit d’apporter les modifications et de continuer le cycle.

Par exemple, l’échec du test présenté à la figure précédente est dû à une hypothèse incorrecte dans la méthode de test stipulant que les caractères non alphabétiques renvoient `true` lorsqu’ils sont transmis à la méthode [Char.IsLower](xref:System.Char.IsLower(System.Char)). Une fois la méthode de test corrigée, nous pouvons nous apercevoir que tous les tests réussissent. Lors de ces opérations, nous n’avons pas besoin d’interrompre ni d’arrêter Live Unit Testing.

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing et l’Explorateur de tests

En règle générale, **l’Explorateur de tests** fournit l’interface qui vous permet d’exécuter, de déboguer et d’analyser vos résultats de test. Live Unit Testing s’intègre à **l’Explorateur de tests**. Quand Live Unit Testing n’est pas activé ou quand il est arrêté, **l’Explorateur de tests** affiche l’état des tests unitaires lors de la dernière exécution d’un test. Des modifications apportées au code source nécessitent que vous réexécutiez les tests. En revanche, lorsque Live Unit Testing est activé, l’état des tests unitaires dans **l’Explorateur de tests** est mis à jour immédiatement. Vous n’avez plus besoin d’exécuter explicitement vos tests unitaires. 

Toutefois, il existe certaines différences entre l’exécution automatique des tests et la mise à jour des résultats de test de Live Unit Testing et l’exécution explicite des tests à partir de **l’Explorateur de tests**. à savoir :

- L’exécution ou le débogage des tests depuis la fenêtre de l’Explorateur de tests exécute des fichiers binaires réguliers, tandis que Live Unit Testing exécute des fichiers binaires instrumentés. 
- Live Unit Testing ne crée pas de domaine d’application pour exécuter des tests, mais exécute des tests à partir du domaine par défaut. Les tests exécutés depuis la fenêtre de **l’Explorateur de tests** créent un domaine d’application.
- Live Unit Testing exécute des tests dans chaque assembly de test de manière séquentielle. Si vous exécutez plusieurs tests depuis la fenêtre de **l’Explorateur de tests** et si le bouton **Exécuter les tests en parallèle** est sélectionné, les tests seront exécutés en parallèle.

## <a name="including-and-excluding-test-projects-and-test-methods"></a>Inclusion et exclusion de projets de test et méthodes de test

Pour les solutions comptant de nombreux projets de test, vous pouvez contrôler les projets et les méthodes individuelles d’un projet à inclure dans Live Unit Testing. 

Par exemple, si vous disposez d’une solution avec des centaines de projets de test, vous pouvez sélectionner un ensemble ciblé de projets de test à inclure dans Live Unit Testing. Pour sélectionner les projets individuels dans les tests unitaires, procédez comme suit une fois Live Unit Testing démarré :

1.  Cliquez avec le bouton droit sur la solution dans l’Explorateur de solutions et choisissez **Live Tests** (Tests en direct), **Exclure** pour exclure toute la solution.
2.  Cliquez avec le bouton droit sur chaque projet de test à inclure dans les tests et choisissez **Live Tests** (Tests en direct), **Inclure**.
 
Utilisez la fenêtre de l’éditeur de code pour inclure ou exclure des méthodes de test. Cliquez avec le bouton droit sur la signature de la méthode de test dans la fenêtre de l’éditeur de code, puis sélectionnez **Live Tests** (Tests en direct), **Inclure** ou **Live Tests** (Tests en direct), **Exclure**. 

Vous pouvez également appliquer l’attribut [<ExcludeFromCodeCoverage>](https://msdn.microsoft.com/library/system.diagnostics.codeanalysis.excludefromcodecoverageattribute.aspx) pour exclure par programme des méthodes, des classes ou des structures de la génération de couverture dans Live Unit Testing.

Live Unit Testing enregistre l’état d’inclusion/d’exclusion en tant que paramètre utilisateur et le conserve quand une solution est fermée puis ouverte à nouveau. 

## <a name="see-also"></a>Voir aussi

[Live Unit Testing Blog](https://go.microsoft.com/fwlink/?linkid=842514)  (Blog sur Live Unit Testing)  
[Live Unit Testing FAQ](live-unit-testing-faq.md)   (FAQ Live Unit Testing)  
[Channel 9 Video: Live Unit Testing in Visual Studio 2017](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105) (Vidéo Channel 9 : Live Unit Testing dans Visual Studio 2017)


