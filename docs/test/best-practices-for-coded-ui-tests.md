---
title: Meilleures pratiques pour les tests codés de l'interface utilisateur
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed2ab3ff15e94bf0e014b99b6451840e6f26a04e
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896016"
---
# <a name="best-practices-for-coded-ui-tests"></a>Bonnes pratiques pour les tests codés de l’interface utilisateur

Cette rubrique décrit certaines recommandations pour le développement de tests codés de l’interface utilisateur.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="best-practices"></a>meilleures pratiques recommandées.

Utilisez les instructions suivantes pour créer un test codé de l'interface utilisateur flexible.

-   Utilisez le **Générateur de test codé de l’interface utilisateur** dès que possible.

-   Ne modifiez pas le fichier *UIMap.designer.cs* directement. Si vous modifiez le fichier, les changements apportés à ce dernier vont être remplacés.

-   Créez votre test en tant que séquence de méthodes enregistrées. Pour plus d’informations sur la manière d’enregistrer une méthode, consultez [Création de tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md).

-   Chaque méthode enregistrée doit agir sur une page, un formulaire ou une boîte de dialogue unique. Créez une méthode de test pour chaque nouvelle page, nouveau formulaire ou nouvelles boîte de dialogue.

-   Quand vous créez une méthode, utilisez un nom significatif au lieu du nom par défaut. Un nom significatif permet d'identifier l'objectif de la méthode.

-   Si possible, limitez chaque méthode enregistrée à moins de 10 actions. Cette approche modulaire facilite le remplacement d'une méthode si l'interface utilisateur change.

-   Créez chaque assertion à l’aide du **Générateur de test codé de l’interface utilisateur**, qui ajoute automatiquement une méthode d’assertion au fichier *UIMap.Designer.cs*.

-   Si l'interface utilisateur change, réenregistrez les méthodes de test ou les méthodes d'assertion, ou bien réenregistrez les sections affectées d'une méthode de test existante.

-   Créez un fichier <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> distinct pour chaque module de votre application testée. Pour plus d’informations, consultez [Test d’une grande application avec plusieurs mappages d’IU](../test/testing-a-large-application-with-multiple-ui-maps.md).

-   Dans l'application testée, utilisez des noms significatifs quand vous créez les contrôles d'interface utilisateur. L’utilisation de noms significatifs apporte plus de clarté et de simplicité aux noms de contrôles générés automatiquement.

-   Si vous créez des assertions en codant avec l’API, créez une méthode pour chaque assertion dans le cadre de la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> qui se trouve dans le fichier *UIMap.cs*. Pour exécuter l’assertion, appelez cette méthode à partir de votre méthode de test.

-   Si vous codez directement avec l’API, utilisez les propriétés et méthodes dans les classes générées dans le fichier *UIMap.Designer.cs* de votre code autant que possible. Ces classes facilitent votre travail, le rendent plus fiable et vous permettent d'augmenter votre productivité.

Les tests codés de l'interface utilisateur s'adaptent automatiquement à de nombreuses modifications dans l'interface utilisateur. Si, par exemple, un élément d'interface utilisateur a changé de position ou de couleur, la plupart du temps, le test codé de l'interface utilisateur trouve quand même le bon élément.

Durant une série de tests, les contrôles d’IU sont localisés par le framework de tests à l’aide d’un ensemble de propriétés de recherche. Les propriétés de recherche sont appliquées à chaque classe de contrôle dans les définitions créées par le **Générateur de test codé de l’interface utilisateur** dans le fichier *UIMap.Designer.cs*. Les propriétés de recherche contiennent des paires nom-valeur de noms de propriété et des valeurs de propriété qui peuvent servir à identifier le contrôle, comme les propriétés <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A> et <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> du contrôle. Si les propriétés de recherche ne sont pas modifiées, le test codé de l'interface utilisateur trouve correctement le contrôle dans l'interface utilisateur. Si les propriétés de recherche changent, les tests codés de l’interface utilisateur ont un algorithme de correspondance intelligent qui applique des paramètres heuristiques pour rechercher des contrôles et des fenêtres dans l’IU. Quand l'interface utilisateur a changé, vous pouvez peut-être modifier les propriétés de recherche des éléments précédemment identifiés pour vérifier qu'ils sont trouvés.

## <a name="if-your-user-interface-changes"></a>Si votre interface utilisateur change

Les interfaces utilisateur changent souvent au cours du développement. Voici quelques façons de réduire l'effet de ces changements :

-   Recherchez la méthode enregistrée qui référence ce contrôle, puis utilisez le **Générateur de test codé de l’interface utilisateur** pour réenregistrer les actions de cette méthode. Vous pouvez utiliser le même nom pour la méthode pour écraser les actions existantes.

-   Si un contrôle a une assertion qui n'est plus valide :

    -   Supprimez la méthode qui contient l'assertion.

    -   Supprimez l'appel à cette méthode depuis la méthode de test.

    -   Ajouter une nouvelle assertion en faisant glisser le bouton en forme de croix sur le contrôle d'interface utilisateur, ouvrez le mappage d'interface utilisateur, puis ajoutez la nouvelle assertion.

Pour plus d’informations sur la manière d’enregistrer des tests codés de l’interface utilisateur, consultez [Utiliser l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md).

## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Si un processus en arrière-plan doit être terminé pour que le test puisse continuer

Vous devez peut-être attendre qu'un processus se termine pour pouvoir poursuivre avec l'action d'interface utilisateur suivante. Pour ce faire, vous pouvez utiliser <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> afin d’attendre avant de poursuivre le test, comme dans l’exemple suivant :

```csharp
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [Utiliser l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md)
- [Création de tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md)
- [Test d’une grande application avec plusieurs mappages d’IU](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Plateformes et configurations prises en charge pour les tests codés de l’interface utilisateur et les enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)