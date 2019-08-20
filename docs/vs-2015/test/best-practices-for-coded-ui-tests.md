---
title: Meilleures pratiques pour les tests codés de l’interface utilisateur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
ms.assetid: d5aef766-a24c-4f1f-ac9b-e5462b6627d4
caps.latest.revision: 41
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1a631823ce39e5655bba611f90c2869e8dff1d8f
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871674"
---
# <a name="best-practices-for-coded-ui-tests"></a>Meilleures pratiques pour les tests codés de l'interface utilisateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique décrit les pratiques recommandées à suivre pour développer des tests codés de l'interface utilisateur.

 **Spécifications**

- Visual Studio Enterprise

## <a name="best-practices"></a>Meilleures pratiques
 Utilisez les instructions suivantes pour créer un test codé de l'interface utilisateur flexible.

- Utilisez le **Générateur de test codé de l’interface utilisateur** dès que possible.

- Ne modifiez pas le fichier `UIMap.designer.cs` directement. Si vous le modifiez, les modifications apportées au fichier sont écrasées.

- Créez votre test en tant que séquence de méthodes enregistrées. Pour plus d’informations sur la manière d’enregistrer un méthode, consultez [Création de tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

- Chaque méthode enregistrée doit agir sur une page, un formulaire ou une boîte de dialogue unique. Créez une méthode de test pour chaque nouvelle page, nouveau formulaire ou nouvelles boîte de dialogue.

- Quand vous créez une méthode, utilisez un nom significatif au lieu du nom par défaut. Un nom significatif permet d'identifier l'objectif de la méthode.

- Si possible, limitez chaque méthode enregistrée à moins de 10 actions. Cette approche modulaire facilite le remplacement d'une méthode si l'interface utilisateur change.

- Créez chaque assertion à l’aide du **Générateur de test codé de l’interface utilisateur**, qui ajoute automatiquement une méthode d’assertion au fichier `UIMap.Designer.cs`.

- Si l'interface utilisateur change, réenregistrez les méthodes de test ou les méthodes d'assertion, ou bien réenregistrez les sections affectées d'une méthode de test existante.

- Créez un fichier [UIMap](/previous-versions/dd580454(v=vs.140)) distinct pour chaque module de votre application testée. Pour plus d’informations, consultez [Test d’une grande application avec plusieurs mappages d’IU](../test/testing-a-large-application-with-multiple-ui-maps.md).

- Dans l'application testée, utilisez des noms significatifs quand vous créez les contrôles d'interface utilisateur. Le sens et la facilité d'utilisation des noms de contrôles générés automatiquement sont ainsi renforcés.

- Si vous créez des assertions en codant avec l’API, créez une méthode pour chaque assertion dans la partie de la classe [UIMap](/previous-versions/dd580454(v=vs.140)) qui se trouve `UIMap.cs` dans le fichier. Appelez cette méthode depuis votre méthode de test pour exécuter l'assertion.

- Si vous codez directement avec l'API, utilisez les propriétés et méthodes dans les classes générées dans le fichier `UIMap.Designer.cs` de votre code autant que possible. Ces classes facilitent votre travail, le rendent plus fiable et vous permettent d'augmenter votre productivité.

  Les tests codés de l'interface utilisateur s'adaptent automatiquement à de nombreuses modifications dans l'interface utilisateur. Si, par exemple, un élément d'interface utilisateur a changé de position ou de couleur, la plupart du temps, le test codé de l'interface utilisateur trouve quand même le bon élément.

  Pendant l’exécution d’un test, les contrôles d’interface utilisateur sont localisés par le framework de test à l’aide d’un jeu de propriétés de recherche qui sont appliquées à chaque classe de contrôle dans les définitions créées par le **Générateur de test codé de l’interface utilisateur** dans le fichier `UIMap.Designer.cs`. Les propriétés de recherche contiennent des paires nom-valeur de noms de propriété et des valeurs de propriété qui peuvent servir à identifier le contrôle, comme les propriétés <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A> et <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> du contrôle. Si les propriétés de recherche ne sont pas modifiées, le test codé de l'interface utilisateur trouve correctement le contrôle dans l'interface utilisateur. Si les propriétés de recherche sont modifiées, les tests codés de l'interface utilisateur ont un algorithme de correspondance intelligent qui applique des paramètres heuristiques pour rechercher des contrôles et fenêtres dans l'interface utilisateur. Quand l'interface utilisateur a changé, vous pouvez peut-être modifier les propriétés de recherche des éléments précédemment identifiés pour vérifier qu'ils sont trouvés.

## <a name="what-to-do-if-your-user-interface-changes"></a>Que faire si votre interface utilisateur change ?
 Les interfaces utilisateur changent souvent au cours du développement. Voici quelques façons de réduire l'effet de ces changements :

- Trouvez la méthode enregistrée qui référence ce contrôle et utilisez le **Générateur de test codé de l’interface utilisateur** pour réenregistrer les actions de cette méthode. Vous pouvez utiliser le même nom pour la méthode pour écraser les actions existantes.

- Si un contrôle a une assertion qui n'est plus valide :

  - Supprimez la méthode qui contient l'assertion.

  - Supprimez l'appel à cette méthode depuis la méthode de test.

  - Ajouter une nouvelle assertion en faisant glisser le bouton en forme de croix sur le contrôle d'interface utilisateur, ouvrez le mappage d'interface utilisateur, puis ajoutez la nouvelle assertion.

  Pour plus d’informations sur la manière d’enregistrer des tests codés de l’interface utilisateur, consultez [Utiliser l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md).

## <a name="what-to-do-if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Que faire si un processus en arrière-plan doit être terminé pour que le test puisse continuer ?
 Vous devez peut-être attendre qu'un processus se termine pour pouvoir poursuivre avec l'action d'interface utilisateur suivante. Pour cela, vous pouvez utiliser <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> pour attendre avant de continuer le test comme dans l'exemple suivant.

```
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Voir aussi

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [Utiliser l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md)
- [Création de tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Test d’une grande application avec plusieurs mappages d’IU](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Plateformes et configurations prises en charge pour les tests codés de l’interface utilisateur et les enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
