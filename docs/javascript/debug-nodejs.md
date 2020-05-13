---
title: Déboguer une application JavaScript ou TypeScript
description: Visual Studio prend en charge pour le débogage des applications JavaScript et TypeScript dans Visual Studio
ms.date: 11/01/2019
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 3f8fa8fcd859a7464d471972689728dc556a79bd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75678972"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Déboguer une application JavaScript ou TypeScript dans Visual Studio

Vous pouvez déboguer un code JavaScript et TypeScript à l’aide de Visual Studio. Vous pouvez définir et atteindre des points d’arrêt, attacher le débogueur, inspecter des variables, afficher la pile des appels et utiliser d’autres fonctionnalités de débogage.

> [!TIP]
> Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/) pour l’installer gratuitement. Selon le type de développement d’applications que vous exécutez, vous devrez peut-être installer la **charge de travail de développement Node.js** avec Visual Studio.

## <a name="debug-server-side-script"></a>Déboguer un script côté serveur

1. Une fois votre projet ouvert dans Visual Studio, ouvrez un fichier JavaScript côté serveur (par exemple *server.js*), puis cliquez dans la marge à gauche pour définir un point d’arrêt :

    ![Définir un point d'arrêt](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code.

1. Pour exécuter votre application, appuyez sur **F5** (**Déboguer** > **Démarrer le débogage**).

    Le débogueur s’arrête au point d’arrêt que vous avez défini (l’instruction active est marquée en jaune). Vous pouvez maintenant inspecter l’état de votre application en pointant sur les variables situées dans la portée et en utilisant les fenêtres du débogueur, notamment les fenêtres **Variables locales** et **Espion**.

1. Appuyez sur **F5** pour continuer l’exécution de l’application.

1. Pour utiliser les outils de développement Chrome ou les outils F12, appuyez sur **F12**. Vous pouvez utiliser ces outils pour examiner le DOM et interagir avec l’application à l’aide de la console JavaScript.

## <a name="debug-client-side-script"></a>Débogage de script côté client

::: moniker range=">=vs-2019"
Visual Studio fournit un support de débogage côté client pour Chrome et Microsoft Edge (Chromium) seulement. Dans certains scénarios, le débogueur atteint automatiquement les points d’arrêt dans le code JavaScript et TypeScript et dans des scripts incorporés dans des fichiers HTML. Pour déboguer le script côté client dans ASP.NET applications, voir le blog [Debug JavaScript dans Microsoft Edge](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) et ce [post pour Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome). Pour débogage TypeScript dans ASP.NET Core, voir également [Créer une application ASP.NET Core avec TypeScript](tutorial-aspnet-with-typescript.md).
::: moniker-end
::: moniker range="vs-2017"
Visual Studio fournit un support de débogage côté client pour Chrome et Internet Explorer seulement. Dans certains scénarios, le débogueur atteint automatiquement les points d’arrêt dans le code JavaScript et TypeScript et dans des scripts incorporés dans des fichiers HTML. Pour déboguer le script côté client dans ASP.NET applications, voir le blog poste [client-côté débogage de projets ASP.NET dans Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
::: moniker-end

Pour les applications autres que ASP.NET, suivez les étapes décrites ici.

### <a name="prepare-your-app-for-debugging"></a>Préparez votre application pour le débogage

Si votre source est minimisée ou créée par un transpiler comme TypeScript ou Babel, utilisez des [mappages de sources](#generate_source_maps) pour bénéficier d’une meilleure expérience de débogage. Sans les mappages de sources, il est néanmoins possible d’attacher le débogueur à un script en cours d’exécution côté client. Mais vous pourrez seulement définir et atteindre des points d’arrêt dans le fichier minimisé ou transpilé, et non dans le fichier source d’origine. Par exemple, dans une application Vue.js, un script minimisé est passé sous forme de chaîne à une instruction `eval`, et il n’existe aucun moyen de parcourir ce code efficacement à l’aide du débogueur Visual Studio, à moins d’utiliser des mappages de sources. Dans des scénarios complexes de débogage, vous pouvez également utiliser Chrome Developer Tools ou F12 Tools pour Microsoft Edge à la place.

Pour aider à générer des cartes sources, voir [générer des cartes source pour débogage](#generate_source_maps).

### <a name="prepare-the-browser-for-debugging"></a><a name="prepare_the_browser_for_debugging"></a>Préparer le navigateur pour le débogage

::: moniker range=">=vs-2019"
Pour ce scénario, utilisez Microsoft Edge (Chromium), actuellement nommé **Microsoft Edge Beta** dans l’IDE, soit Chrome.
::: moniker-end
::: moniker range="vs-2017"
Pour ce scénario, utilisez Chrome.
::: moniker-end

1. Fermez toutes les fenêtres pour le navigateur cible.

   D’autres instances de navigateur peuvent empêcher le navigateur de s’ouvrir avec un débogage activé. (Les extensions de navigateur peuvent être en cours d’exécution et d’empêcher le mode de déboguer complètement, de sorte que vous devrez peut-être ouvrir Task Manager pour trouver des instances inattendues de Chrome.)

   ::: moniker range=">=vs-2019"
   Pour Microsoft Edge (Chromium), également arrêter toutes les instances de Chrome. Parce que les deux navigateurs utilisent la base de code de chrome, cela donne les meilleurs résultats.
   ::: moniker-end

2. Démarrez votre navigateur avec un débogage activé.

    ::: moniker range=">=vs-2019"
    À partir de Visual Studio 2019, vous pouvez définir le drapeau au lancement `--remote-debugging-port=9222` du navigateur en sélectionnant Parcourir **avec...** > de la barre d’outils **Debug,** puis en choisissant **Add**, puis en plaçant le drapeau dans le champ **Arguments.** Utilisez un nom amical différent pour le navigateur comme **Edge avec Debugging** ou **Chrome avec Debugging**. Pour plus d’informations, consultez les [notes de publication](/visualstudio/releases/2019/release-notes-v16.2).

    ![Définissez votre navigateur pour ouvrir avec un débogage activé](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternativement, ouvrez la commande **Run** à partir du bouton Windows **Start** (clic droit et choisissez **Run**), et entrez la commande suivante :

    `msedge --remote-debugging-port=9222`

    ou

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Ouvrez la commande **Exécuter** à partir du bouton **Démarrer** de Windows (cliquez avec le bouton droit de la souris et choisissez **Exécuter**), puis entrez la commande suivante :

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Cela commence votre navigateur avec débogage activé.

    L’application n’est pas encore en cours d’exécution, de sorte que vous obtenez une page de navigateur vide.

### <a name="attach-the-debugger-to-client-side-script"></a>Attachez le débbuggeur au script côté client

Pour joindre le débbugger de Visual Studio et les points d’arrêt du code côté client, le débagénaire a besoin d’aide pour identifier le processus correct. Voici une façon d’y parvenir.

1. Passez à Visual Studio, puis définissez un point d’arrêt dans votre code source, qui peut être un fichier JavaScript, un fichier TypeScript ou un fichier JSX. (Définissez le point d’arrêt dans une ligne de code qui permet des points d’arrêt, tels qu’une déclaration de retour ou une déclaration var.)

    ![Définir un point d'arrêt](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Pour trouver le code spécifique dans un fichier transpilé, utilisez **Ctrl**+**F** (**Modifier** > **trouver et remplacer** > **Quick Find**).

    Pour le code côté client, pour atteindre un point d’arrêt dans un fichier TypeScript, *.vue*, ou fichier JSX nécessite généralement l’utilisation de [cartes source](#generate_source_maps). Une carte source doit être configurée correctement pour prendre en charge le débogage dans Visual Studio.

2. Sélectionnez votre navigateur cible comme cible de débogé dans Visual Studio, puis appuyez sur **Ctrl**+**F5** (**Debug** > **Start Without Debugging**) pour exécuter l’application dans le navigateur.

    ::: moniker range=">=vs-2019"
    Si vous avez créé une configuration de navigateur avec un nom amical, choisissez cela comme votre cible de débogé.
    ::: moniker-end

    L’application s’ouvre dans un nouvel onglet du navigateur.

3. Choisissez **Debug** > **Attach to Process**.

    > [!TIP]
    > A partir de Visual Studio 2017, une fois que vous attachez au processus la première fois en suivant ces étapes, vous pouvez rapidement réattacher au même processus en choisissant **Debug** > **Reattach à Traiter**.

4. Dans la boîte de dialogue **Attach to Process,** obtenez une liste filtrée des instances de navigateur auxquelles vous pouvez vous joindre.
    ::: moniker range=">=vs-2019"
    Dans Visual Studio 2019, choisissez le débbugger correct pour votre navigateur cible, **JavaScript (Chrome)** ou **JavaScript (Microsoft Edge - Chromium)** dans le **Attach to** field, type **chrome** ou **bord** dans la boîte de filtre pour filtrer les résultats de recherche.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans Visual Studio 2017, choisissez le **code Webkit** dans le **fixeur** au champ, **tapez** le chrome dans la boîte de filtre pour filtrer les résultats de recherche.
    ::: moniker-end

5. Sélectionnez le processus de navigateur avec le port hôte correct (localhost dans cet exemple), et **sélectionnez Attach**.

    Le port (par exemple, 1337) peut également apparaître dans le champ **Titre** pour vous aider à sélectionner la bonne instance de navigateur.

    ::: moniker range=">=vs-2019"
    L’exemple suivant montre comment cela ressemble au navigateur Microsoft Edge (Chromium).

    ![Attacher au processus](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Attacher au processus](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Vous savez que le débogueur est correctement attaché quand l’Explorateur DOM et la console JavaScript s’ouvrent dans Visual Studio. Ces outils de débogage sont similaires aux outils de développement Chrome et aux outils F12 pour Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Si le débogénaire ne se fixe pas et que vous voyez le message « Échec au lancement de l’adaptateur de débbug » ou « Impossible de s’attacher au processus. Une opération n’est pas légale dans l’état actuel.", utilisez le gestionnaire de tâches Windows pour fermer tous les cas du navigateur cible avant de démarrer le navigateur en mode débogage. Les extensions de navigateur peuvent être en cours d’exécution et d’empêcher le mode de débbug complet.

6. Étant donné que le code avec le point d’arrêt peut avoir déjà exécuté, actualisez votre page de navigateur. Si nécessaire, prenez des mesures pour provoquer l’exécution du code avec le point d’arrêt.

    Pendant que l’exécution du débogueur est en pause, vous pouvez examiner l’état de votre application en pointant sur les variables et en utilisant les fenêtres du débogueur. Vous pouvez faire avancer le débogueur en exécutant pas à pas le code (**F5**, **F10** et **F11**). Pour plus d’informations sur les caractéristiques de débogage de base, voir [d’abord regarder le débbugger](../debugger/debugger-feature-tour.md).

    Vous pouvez atteindre le point d’arrêt dans un fichier *.js* transpiled ou un fichier source, selon votre type d’application, quelles étapes vous avez suivi précédemment, et d’autres facteurs tels que l’état de votre navigateur. De toute façon, vous pouvez exécuter pas à pas le code et examiner les variables.

   * Si vous avez besoin de vous introduire dans le code dans un fichier Source TypeScript, JSX ou *.vue* et que vous n’êtes pas en mesure de le faire, assurez-vous que votre environnement est configuré correctement, tel que décrit dans la section [Dépannage.](#troubleshooting_source_maps)

   * Si vous avez besoin de pénétrer dans le code dans un fichier JavaScript transpilé (par exemple, *app-bundle.js*) et ne sont pas en mesure de le faire, supprimer le fichier de carte source, *filename.js.map*.

### <a name="troubleshooting-breakpoints-and-source-maps"></a><a name="troubleshooting_source_maps"></a>Points d’arrêt de dépannage et cartes sources

Si vous avez besoin de vous introduire dans le code dans un fichier source TypeScript ou JSX et que vous n’êtes pas en mesure de le faire, utilisez **Attach to Process** comme décrit dans les étapes précédentes pour joindre le débagé. Assurez-vous que votre environnement est configuré correctement :

* Vous avez fermé toutes les instances du navigateur, y compris les extensions Chrome (à l’aide du Task Manager), afin que vous puissiez exécuter le navigateur en mode débogé.
      
* Assurez-vous de [démarrer le navigateur en mode débogé](#prepare_the_browser_for_debugging).

* Assurez-vous que votre fichier de carte source inclut le chemin relatif correct à votre fichier source et qu’il n’inclut pas les préfixes non pris en compte tels que *webpack:///*, ce qui empêche le debugger Visual Studio de localiser un fichier source. Par exemple, une référence comme *webpack:///.app.tsx* pourrait être corrigée à *./app.tsx*. Vous pouvez le faire manuellement dans le fichier de carte source (ce qui est utile pour le test) ou par le biais d’une configuration de construction personnalisée. Pour plus d’informations, voir [Cartes source Generate pour débogage](#generate_source_maps).

Alternativement, si vous avez besoin de pénétrer dans le code dans un fichier source (par `debugger;` exemple, *app.tsx*) et ne sont pas en mesure de le faire, essayez d’utiliser l’instruction dans le fichier source, ou définir des points d’arrêt dans les outils de développeur Chrome (ou F12 Tools pour Microsoft Edge) à la place.

## <a name="generate-source-maps-for-debugging"></a><a name="generate_source_maps"></a> Générer des mappages de sources pour le débogage

Visual Studio permet d’utiliser et de générer des mappages de sources sur les fichiers sources JavaScript. Cela est souvent nécessaire si votre source est minimisée ou créée par un transpiler comme TypeScript ou Babel. Les options disponibles varient selon le type de projet.

* Par défaut, un projet TypeScript dans Visual Studio génère pour vous des mappages de sources. Pour plus d’informations, voir [Configurez les cartes source à l’aide d’un fichier tsconfig.json](#configure_source_maps).

* Dans un projet JavaScript, vous pouvez générer des cartes sources à l’aide d’un bundler comme le webpack et d’un compilateur comme le compilateur TypeScript (ou Babel), que vous pouvez ajouter à votre projet. Pour le compilateur TypeScript, vous devez également ajouter un fichier *tsconfig.json* et définir l’option `sourceMap` compilateur. Pour obtenir un exemple montrant comment procéder à l’aide d’une configuration webpack de base, consultez [Créer une application Node.js avec React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Si vous ne connaissez pas les mappages de sources, veuillez lire [Introduction aux mappages de sources JavaScript](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) avant de continuer. 

Afin de configurer les paramètres avancés pour les mappages de sources, utilisez un fichier *tsconfig.json* ou les paramètres du projet dans un projet TypeScript, mais pas les deux.

Pour activer le débogage à l’aide de Visual Studio, vous devez vous assurer que les références à votre fichier source dans la carte source générée sont correctes (cela peut nécessiter des tests). Par exemple, si vous utilisez le webpack, les références dans le fichier de carte source incluent le préfixe *webpack:///,* qui empêche Visual Studio de trouver un fichier source TypeScript ou JSX. Plus précisément, lorsque vous corrigez cela à des fins de débogage, la référence au fichier source (comme *app.tsx*), doit être changée de quelque chose comme *webpack:///./app.tsx* à quelque chose comme *./app.tsx*, qui permet de débogage (le chemin est par rapport à votre fichier source). L’exemple suivant montre comment vous pouvez configurer les cartes sources dans le webpack, qui est l’un des bundlers les plus courants, de sorte qu’ils travaillent avec Visual Studio.

(Webpack seulement) Si vous définissez le point d’arrêt dans un TypeScript du fichier JSX (plutôt qu’un fichier JavaScript transpilé), vous devez mettre à jour votre configuration webpack. Par exemple, dans *webpack-config.js*, vous devrez peut-être remplacer le code suivant :

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

par ce code :

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Il s’agit d’un paramètre de développement uniquement pour permettre le débogage de code côté client dans Visual Studio.

Pour les scénarios compliqués, les outils de navigateur (**F12**) fonctionnent parfois mieux pour débogage, car ils ne nécessitent pas de modifications aux préfixes personnalisés.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a><a name="configure_source_maps"></a>Configurer les cartes sources à l’aide d’un fichier tsconfig.json

Si vous ajoutez un fichier *tsconfig.json* à votre projet, Visual Studio traite la racine du répertoire comme un projet TypeScript. Pour ajouter le fichier, cliquez à droite sur votre projet dans Solution Explorer, puis choisissez **Ajouter > nouvel élément > Fichier de configuration TypeScript JSON**. Un fichier *tsconfig.json* comme ce qui suit est ajouté à votre projet.

```json
{
  "compilerOptions": {
    "noImplicitAny": false,
    "noEmitOnError": true,
    "removeComments": false,
    "sourceMap": true,
    "target": "es5"
  },
  "exclude": [
    "node_modules",
    "wwwroot"
  ]
}
```

#### <a name="compiler-options-for-tsconfigjson"></a>Options du compilateur pour tsconfig.json

* **inlineSourceMap**: Émettez un fichier unique avec des cartes sources au lieu de créer une carte source distincte pour chaque fichier source.
* **inlineSources**: Émettez la source à côté des cartes sources dans un seul fichier ; nécessite *inlineSourceMap* ou *sourceMap* à définir.
* **mapRoot**: Specifie l’emplacement où le débbuggeur doit trouver des fichiers de carte source *(.map)* au lieu de l’emplacement par défaut. Utilisez cet indicateur si les fichiers runtime *.map* doivent se trouver dans un emplacement autre que les fichiers *.js*. L’emplacement spécifié est incorporé dans le mappage de source pour diriger le débogueur vers l’emplacement des fichiers *.map*.
* **sourceMap**: Génère un fichier *.map* correspondant.
* **sourceRoot**: Précise l’emplacement où le débbuggeur doit trouver des fichiers TypeScript au lieu des emplacements sources. Utilisez cet indicateur si les sources runtime doivent se trouver dans un emplacement autre que celui défini au moment de la conception. L’emplacement spécifié est incorporé dans le mappage de source pour diriger le débogueur vers l’emplacement des fichiers sources.

Pour plus d’informations sur les options du compilateur, consultez la page [Options du compilateur](https://www.typescriptlang.org/docs/handbook/compiler-options.html) dans le manuel TypeScript.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Configurer les cartes sources à l’aide des paramètres du projet (projet TypeScript)

Vous pouvez également configurer les paramètres des mappages de sources à l’aide des propriétés du projet en double-cliquant sur le projet, puis en choisissant **Projet > Propriétés > Build TypeScript > Débogage**.

Ces paramètres de projet sont disponibles.

* **Générer des cartes sources** (équivalent à **sourceMap** en *tsconfig.json):* Génère correspondant *.map* fichier.
* **Spécifier le répertoire racinaire des cartes sources** (équivalent à **mapRoot** dans *tsconfig.json):* Précise l’emplacement où le débbuggeur devrait trouver des fichiers cartographiques au lieu des emplacements générés. Utilisez cet indicateur si les fichiers runtime *.map* doivent se trouver dans un emplacement autre que les fichiers .js. L’emplacement spécifié est incorporé dans le mappage de source pour diriger le débogueur vers l’emplacement des fichiers de mappages.
* **Spécifier l’annuaire racine des fichiers TypeScript** (équivalent à **sourceRoot** dans *tsconfig.json):* Précise l’emplacement où le débbuggeur devrait trouver des fichiers TypeScript au lieu d’emplacements source. Utilisez cet indicateur si les fichiers sources runtime doivent se trouver dans un emplacement autre que celui défini au moment de la conception. L’emplacement spécifié est incorporé dans le mappage de source pour diriger le débogueur vers l’emplacement des fichiers sources.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Déboguer JavaScript dans des fichiers dynamiques à l’aide de Razor (ASP.NET)

::: moniker range=">=vs-2019"
À partir de Visual Studio 2019, Visual Studio fournit un support de débogage pour Chrome et Microsoft Edge (Chromium) seulement.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio offre des fonctionnalités de débogage dans Chrome et Internet Explorer uniquement.
::: moniker-end

Cependant, vous ne pouvez pas automatiquement frapper les points d’arrêt sur les fichiers générés avec la syntaxe Razor (cshtml, vbhtml). Il existe deux approches permettant de déboguer ce type de fichier :

* **Placez `debugger;` la déclaration où vous voulez casser**: Cela provoque le script dynamique d’arrêter l’exécution et de commencer à débogage immédiatement pendant qu’il est créé.
* **Chargez la page et ouvrez le document dynamique sur Visual Studio**: vous devrez ouvrir le fichier dynamique tout en débogage, définir votre point d’arrêt, et rafraîchir la page pour que cette méthode fonctionne. Selon que vous utilisez Chrome ou Internet Explorer, vous trouverez le fichier en utilisant l’une des stratégies suivantes :

   Pour Chrome, accédez à l’**Explorateur de solutions > Script Documents (Documents de script) > YourPageName (Nom de votre page)**.

    > [!NOTE]
    > Quand vous utilisez Chrome, vous pouvez éventuellement recevoir un message indiquant qu’**aucune source n’est disponible entre les balises \<script>**. Cela n’est pas un problème, continuez simplement le débogage.

   ::: moniker range=">=vs-2019"
   Pour Microsoft Edge (Chromium), utilisez la même procédure que Chrome.
   ::: moniker-end

   ::: moniker range="vs-2017"
   Pour Internet Explorer, accédez à **l’Explorateur de solutions > Script Documents (Documents de script) > Windows Internet Explorer > YourPageName (Nom de votre page)**.
   ::: moniker-end

Pour plus d’informations, consultez [Débogage côté client de projets ASP.NET dans Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
