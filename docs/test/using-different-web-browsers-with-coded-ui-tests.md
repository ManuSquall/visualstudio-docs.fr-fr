---
title: Utilisation de différents navigateurs Web avec des tests codés de l'interface utilisateur
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: afbcd419f1890e3414d0076d0a4664df5f941938
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036236"
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>Utiliser différents navigateurs web avec des tests codés de l’interface utilisateur

Les tests codés de l'interface utilisateur peuvent automatiser le test des applications web en enregistrant vos tests à l'aide d'Internet Explorer. Vous pouvez ensuite personnaliser votre test et l'utiliser à l'aide d'Internet Explorer ou d'autres types de navigateurs pour ces applications web.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

Installez d’abord les [composants Selenium pour les tests codés de l’interface utilisateur sur plusieurs navigateurs](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

## <a name="whats-supported-across-all-web-browsers"></a>Quelles sont les opérations prises en charge par tous les navigateurs web ?

-   [Ajouter du code personnalisé pour contrôler les fonctionnalités](https://blogs.msdn.microsoft.com/devops/2012/12/09/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/) comme les propriétés, la recherche et les objets waiter de lecture.

-   Boîtes de dialogue et menus contextuels

-   [Exécuter le code JavaScript de base sans type de retour](https://blogs.msdn.microsoft.com/devops/2013/01/18/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

-   Résilience de recherche (avec concordance active) et [améliorations des performances](https://blogs.msdn.microsoft.com/devops/2012/01/31/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Pourquoi dois-je utiliser les tests codés de l'interface utilisateur sur différents types de navigateur web ?

Lorsque vous testez votre application web à l'aide de divers types de navigateurs web, l'expérience d'interface utilisateur des utilisateurs susceptibles d'utiliser des navigateurs différents est mieux émulée. Par exemple, votre application peut inclure un contrôle ou un code dans Internet Explorer qui n'est pas compatible avec d'autres navigateurs web. En exécutant les tests codés de l'interface utilisateur sur d'autres navigateurs, vous pouvez détecter et corriger les problèmes avant qu'ils aient une incidence sur vos clients.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Comment enregistrer et lire les tests d'interface utilisateur codés des applications web à l'aide des navigateurs web pris en charge ?

**Enregistrement :** vous devez utiliser le générateur de test codé de l’interface utilisateur pour enregistrer le test de votre application web à l’aide d’Internet Explorer. Vous pouvez éventuellement ajouter un code de validation personnalisé pour les contrôles testés à l’aide d’un jeu prédéfini de propriétés, de la même manière que pour les tests codés de l’interface utilisateur. Pour plus d’informations, consultez [Utiliser l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Vous ne pouvez pas enregistrer des tests codés de l'interface utilisateur à l'aide des navigateurs Google Chrome ou Mozilla Firefox.

 **Lecture avec Internet Explorer :** quand aucun navigateur n’est explicitement spécifié, les tests s’exécutent par défaut sur Internet Explorer. Vous pouvez déclarer explicitement le navigateur à utiliser en définissant la propriété **BrowserWindow.CurrentBrowser** dans le code de votre test. Pour Internet Explorer, cette propriété doit être définie sur **IE** ou **Internet Explorer**.

 **Lecture avec des navigateurs web autres qu’Internet Explorer** : pour lire sur les navigateurs web autres qu’Internet Explorer, modifiez la propriété BrowserWindow.CurrentBrowser dans votre code de test et définissez-la sur **Firefox** ou **Chrome**.

 Pour lire les tests sur les navigateurs web autres qu’IE, vous devez installer les **composants Selenium pour les tests codés de l’interface utilisateur sur plusieurs navigateurs**.

### <a name="install-selenium-components"></a>Installer les composants Selenium

1.  Dans le menu **Outils** , choisissez **Extensions et mises à jour**.

2.  Dans la boîte de dialogue **Mises à jour de produit et d’extension**, recherchez `Selenium components for Cross Browser Testing`.

3.  Mettez en surbrillance l’extension et choisissez **Télécharger**.

    > [!TIP]
    > Vous pouvez également télécharger les composants Selenium pour le test codé de l’interface utilisateur sur plusieurs navigateurs [ici](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

Pour plus d’informations sur la création et l’utilisation des tests codés de l’interface utilisateur, consultez [Créer des tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md).

### <a name="enable-debugging"></a>Activer le débogage

Pour activer le débogage de votre application web, vous devez utiliser les options de configuration suivantes :

1.  Activer Uniquement mon code :

    1.  Dans le menu **Outils**, choisissez **Options**, puis **Débogage**.

    2.  Sélectionnez **Activer Uniquement mon code**.

2.  Désactiver les exceptions CLR :

    1.  Dans le menu **Déboguer**, choisissez **Exceptions**.

    2.  Pour **Exceptions CLR**, désactivez **Non géré par l’utilisateur**.

Si vous ne voyez pas l’option de modification `BrowserWindow.CurrentBrowser` dans le test codé de l’interface utilisateur, vous utilisez peut-être une version de Visual Studio qui ne prend pas en charge les tests codés de l’interface utilisateur avec différents navigateurs web. Pour utiliser ces tests codés de l’interface utilisateur, vous devez utiliser l’édition Visual Studio Enterprise.

Voici quelques autres informations à connaître :

- Le navigateur web Apple Safari n'est pas pris en charge.

- L'action de démarrage du navigateur web doit faire partie du test codé de l'interface utilisateur.

   Si un navigateur web est déjà ouvert et que vous souhaitez exécuter des étapes sur ce navigateur, la lecture échoue, sauf si vous utilisez Internet Explorer. Il est donc recommandé d'inclure le démarrage de votre navigateur web à vos tests codés de l'interface utilisateur.

- L'automatisation d'actions d'interface utilisateur basées spécifiquement sur un navigateur, par exemple agrandir, réduire et restaurer, n'est pas prise en charge.

## <a name="tips"></a>Conseils

Vous pouvez configurer la sortie pour inclure des captures d'écran dans les journaux codés de l'interface utilisateur. Pour cela, vous devez définir des paramètres de configuration dans le fichier *QTAgent32.exe.config*. Par défaut, ce fichier est installé à l'endroit suivant :

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

Définissez les valeurs suivantes :

- `EqtTraceLevel` dans la section `system.diagnostics`.

- `<add name="EqtTraceLevel" value="4" />`

   Avec la valeur définie sur 3 ou plus, des captures d’écran sont prises pour chaque action. Lorsque la valeur est 1 ou 2, des captures sont prises uniquement pour les actions d'erreur.

Pour plus d’informations, consultez [Analyse des tests codés de l’interface utilisateur à l’aide des journaux de test codé de l’interface utilisateur](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="video-resources"></a>Ressources vidéo

 [Enregistrement dans IE et lecture dans tous les navigateurs](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

 [Créer des tests multinavigateurs avec le générateur de test codé de l’interface utilisateur](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

 [Créer des tests multi-navigateurs avec du code brut sans mapper l’interface utilisateur](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

 [Exécuter des tests multi-navigateurs de manière séquentielle sur plusieurs navigateurs](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

 [Résoudre les problèmes des tests multi-navigateurs](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

## <a name="see-also"></a>Voir aussi

- [Utiliser l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md)
- [Plateformes et configurations prises en charge pour les tests codés de l’interface utilisateur et les enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Analyser des tests codés de l’interface utilisateur à l’aide des journaux de tests codés de l’interface utilisateur](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
