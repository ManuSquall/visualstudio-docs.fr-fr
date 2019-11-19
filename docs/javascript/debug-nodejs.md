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
ms.openlocfilehash: 0405488f6f456f22711498e81789881ffc5a0a8a
ms.sourcegitcommit: 308a2bdbea81df78bffc3a01afce4ab13131fabc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73912998"
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
Visual Studio assure uniquement la prise en charge du débogage côté client pour chrome et Microsoft Edge (chrome). Dans certains scénarios, le débogueur atteint automatiquement les points d’arrêt dans le code JavaScript et TypeScript et dans des scripts incorporés dans des fichiers HTML. Pour déboguer le script côté client dans les applications ASP.NET, consultez le billet de blog [Déboguer du code JavaScript dans Microsoft Edge](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) et ce [billet pour Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome).
::: moniker-end
::: moniker range="vs-2017"
Visual Studio assure uniquement la prise en charge du débogage côté client pour chrome et Internet Explorer. Dans certains scénarios, le débogueur atteint automatiquement les points d’arrêt dans le code JavaScript et TypeScript et dans des scripts incorporés dans des fichiers HTML. Pour déboguer le script côté client dans les applications ASP.NET, consultez le billet [de blog débogage côté client des projets ASP.net dans Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
::: moniker-end

Pour les applications autres que ASP.NET, suivez les étapes décrites ici.

### <a name="prepare-your-app-for-debugging"></a>Préparer votre application pour le débogage

Si votre source est minimisée ou créée par un transpiler comme TypeScript ou Babel, utilisez des [mappages de sources](#generate_source_maps) pour bénéficier d’une meilleure expérience de débogage. Sans les mappages de sources, il est néanmoins possible d’attacher le débogueur à un script en cours d’exécution côté client. Mais vous pourrez seulement définir et atteindre des points d’arrêt dans le fichier minimisé ou transpilé, et non dans le fichier source d’origine. Par exemple, dans une application Vue.js, un script minimisé est passé sous forme de chaîne à une instruction `eval`, et il n’existe aucun moyen de parcourir ce code efficacement à l’aide du débogueur Visual Studio, à moins d’utiliser des mappages de sources. Dans les scénarios de débogage complexes, vous pouvez également utiliser Chrome Outils de développement ou F12 Tools pour Microsoft Edge à la place.

Pour obtenir de l’aide pour générer des mappages de source, consultez [générer des mappages de sources pour le débogage](#generate_source_maps).

### <a name="prepare_the_browser_for_debugging"></a>Préparer le navigateur pour le débogage

::: moniker range=">=vs-2019"
Pour ce scénario, utilisez Microsoft Edge (chrome), actuellement nommé **Microsoft Edge Beta** dans l’IDE, ou chrome.
::: moniker-end
::: moniker range="vs-2017"
Pour ce scénario, utilisez Chrome.
::: moniker-end

1. Fermez toutes les fenêtres du navigateur cible.

   D’autres instances de navigateur peuvent empêcher l’ouverture du navigateur avec le débogage activé. (Les extensions de navigateur sont peut-être en cours d’exécution et empêchent le mode de débogage complet. par conséquent, vous devrez peut-être ouvrir le gestionnaire des tâches pour rechercher des instances inattendues de

   ::: moniker range=">=vs-2019"
   Pour Microsoft Edge (chrome), arrêtez également toutes les instances de chrome. Étant donné que les deux navigateurs utilisent la base de code de chrome, cela donne les meilleurs résultats.
   ::: moniker-end

2. Démarrez votre navigateur avec le débogage activé.

    ::: moniker range=">=vs-2019"
    À compter de Visual Studio 2019, vous pouvez définir l’indicateur `--remote-debugging-port=9222` au lancement du navigateur en sélectionnant **Parcourir avec...** > dans la barre d’outils **Déboguer** , puis en sélectionnant **Ajouter**et en définissant l’indicateur dans le champ **arguments** . Utilisez un autre nom convivial pour le navigateur, tel que **Edge avec débogage** ou **chrome avec débogage**. Pour plus d’informations, consultez les [notes de publication](/visualstudio/releases/2019/release-notes-v16.2).

    ![Configurer votre navigateur pour qu’il s’ouvre avec le débogage activé](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Vous pouvez également ouvrir la commande **exécuter** à partir du bouton **Démarrer** de Windows (cliquez avec le bouton droit et choisissez **exécuter**), puis entrez la commande suivante :

    `msedge --remote-debugging-port=9222`

    ni

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Ouvrez la commande **Exécuter** à partir du bouton **Démarrer** de Windows (cliquez avec le bouton droit de la souris et choisissez **Exécuter**), puis entrez la commande suivante :

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Cela démarre votre navigateur avec le débogage activé.

    L’application n’est pas encore en cours d’exécution. vous disposez donc d’une page de navigateur vide.

### <a name="attach-the-debugger-to-client-side-script"></a>Attacher le débogueur au script côté client

Pour attacher le débogueur de Visual Studio et atteindre des points d’arrêt dans le code côté client, le débogueur a besoin d’aide pour identifier le processus correct. Voici une façon d’y parvenir.

1. Basculez vers Visual Studio, puis définissez un point d’arrêt dans votre code source, qui peut être un fichier JavaScript, un fichier de base de code ou un fichier JSX. (Définissez le point d’arrêt dans une ligne de code qui autorise les points d’arrêt, par exemple une instruction return ou une déclaration var.)

    ![Définir un point d'arrêt](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Pour rechercher le code spécifique dans un fichier compilé, utilisez **Ctrl**+**F** (**modifier** > **Rechercher et remplacer** > **recherche rapide**).

    Pour le code côté client, pour atteindre un point d’arrêt dans un fichier de base de code ou un fichier JSX, vous devez généralement utiliser des [mappages de source](#generate_source_maps). Un mappage source doit être configuré correctement pour prendre en charge le débogage dans Visual Studio.

2. Sélectionnez votre navigateur cible comme cible de débogage dans Visual Studio, puis appuyez sur **Ctrl**+**F5** (**Déboguer** > exécuter **sans débogage**) pour exécuter l’application dans le navigateur.

    ::: moniker range=">=vs-2019"
    Si vous avez créé une configuration de navigateur avec un nom convivial, choisissez-la comme cible de débogage.
    ::: moniker-end

    L’application s’ouvre dans un nouvel onglet du navigateur.

3. Choisissez **Déboguer** > **Attacher au processus**.

    > [!TIP]
    > À compter de Visual Studio 2017, une fois que vous avez attaché le processus la première fois en suivant ces étapes, vous pouvez le rattacher rapidement au même processus en choisissant **Déboguer** > **rattacher au processus**.

4. Dans la boîte de dialogue **attacher au processus** , récupérez une liste filtrée des instances de navigateur auxquelles vous pouvez attacher.

    ::: moniker range=">=vs-2019"
    Dans Visual Studio 2019, choisissez le débogueur approprié pour votre navigateur cible, **JavaScript (chrome)** ou **JavaScript (Microsoft Edge-chrome)** dans le champ **attacher à** , tapez **chrome** ou **bord** dans la zone de filtre pour filtrer résultats de la recherche.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans Visual Studio 2017, choisissez **code WebKit** dans le champ **attacher à** , tapez **chrome** dans la zone de filtre pour filtrer les résultats de la recherche.
    ::: moniker-end

5. Sélectionnez le processus du navigateur avec le port d’hôte correct (localhost dans cet exemple), puis sélectionnez **attacher**.

    Le port (par exemple, 1337) peut également apparaître dans le champ **titre** pour vous aider à sélectionner l’instance de navigateur appropriée.

    ::: moniker range=">=vs-2019"
    L’exemple suivant montre comment cela recherche le navigateur Microsoft Edge (chrome).

    ![Attacher au processus](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Attacher au processus](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Vous savez que le débogueur est correctement attaché quand l’Explorateur DOM et la console JavaScript s’ouvrent dans Visual Studio. Ces outils de débogage sont similaires aux outils de développement Chrome et aux outils F12 pour Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Si le débogueur ne s’attache pas et que vous voyez le message « échec du lancement de l’adaptateur de débogage » ou «impossible d’attacher au processus. Une opération n’est pas autorisée dans l’état actuel.», utilisez le gestionnaire des tâches Windows pour fermer toutes les instances du navigateur cible avant de démarrer le navigateur en mode débogage. Les extensions de navigateur peuvent être en cours d’exécution et empêchent le mode de débogage complet.

6. Étant donné que le code avec le point d’arrêt peut avoir déjà été exécuté, actualisez la page de votre navigateur. Si nécessaire, prenez des mesures pour provoquer l’exécution du code avec le point d’arrêt.

    Pendant que l’exécution du débogueur est en pause, vous pouvez examiner l’état de votre application en pointant sur les variables et en utilisant les fenêtres du débogueur. Vous pouvez faire avancer le débogueur en exécutant pas à pas le code (**F5**, **F10** et **F11**). Pour plus d’informations sur les fonctionnalités de débogage de base, consultez [premier aperçu du débogueur](../debugger/debugger-feature-tour.md).

    Vous pouvez atteindre le point d’arrêt dans un fichier *. js* ou un fichier source compilé, en fonction de votre type d’application, des étapes que vous avez suivies précédemment, ainsi que d’autres facteurs tels que l’état de votre navigateur. De toute façon, vous pouvez exécuter pas à pas le code et examiner les variables.

   * Si vous devez vous arrêter dans du code dans un fichier source de machine à écrire, JSX ou *. vue* et que vous ne pouvez pas le faire, assurez-vous que votre environnement est configuré correctement, comme décrit dans la section [résolution des problèmes](#troubleshooting_source_maps) .

   * Si vous devez vous arrêter dans du code dans un fichier JavaScript compilé (par exemple, *app-bundle. js*) et que vous ne pouvez pas le faire, supprimez le fichier de mappage source, *nom_fichier. js. map*.

### <a name="troubleshooting_source_maps"></a>Dépannage des points d’arrêt et des mappages de sources

Si vous devez vous arrêter dans du code dans un fichier source de machine à écrire ou JSX et que vous ne pouvez pas le faire, utilisez **attacher au processus** comme décrit dans les étapes précédentes pour attacher le débogueur. Assurez-vous que votre environnement est correctement configuré :

* Vous avez fermé toutes les instances de navigateur, y compris les extensions chrome (à l’aide du gestionnaire des tâches), afin de pouvoir exécuter le navigateur en mode débogage.
      
* Veillez [à démarrer le navigateur en mode débogage](#prepare_the_browser_for_debugging).

* Assurez-vous que votre fichier de mappage source inclut le chemin d’accès relatif correct à votre fichier source et qu’il n’inclut pas de préfixes non pris en charge, tels que *WebPack:///* , ce qui empêche le débogueur Visual Studio de localiser un fichier source. Par exemple, une référence comme *WebPack:///.app.TSX* peut être corrigée en *./app.TSX*. Vous pouvez effectuer cette opération manuellement dans le fichier de mappage source (ce qui est utile pour les tests) ou par le biais d’une configuration de build personnalisée. Pour plus d’informations, consultez [générer des mappages de sources pour le débogage](#generate_source_maps).

Sinon, si vous devez vous arrêter dans le code d’un fichier source (par exemple, *app. TSX*) et que vous ne pouvez pas le faire, essayez d’utiliser l’instruction `debugger;` dans le fichier source, ou définissez des points d’arrêt dans le outils de développement chrome (ou les outils F12 pour Microsoft Edge) à la place.

## <a name="generate_source_maps"></a> Générer des mappages de sources pour le débogage

Visual Studio permet d’utiliser et de générer des mappages de sources sur les fichiers sources JavaScript. Cela est souvent nécessaire si votre source est minimisée ou créée par un transpiler comme TypeScript ou Babel. Les options disponibles varient selon le type de projet.

* Par défaut, un projet TypeScript dans Visual Studio génère pour vous des mappages de sources. Pour plus d’informations, consultez [configurer des mappages de sources à l’aide d’un fichier TSConfig. JSON](#configure_source_maps).

* Dans un projet JavaScript, vous pouvez générer des mappages de sources à l’aide d’un bundle, comme WebPack, et d’un compilateur tel que le compilateur de création de code (ou Babel), que vous pouvez ajouter à votre projet. Pour le compilateur de machine à écrire, vous devez également ajouter un fichier *tsconfig. JSON* et définir l’option du compilateur `sourceMap`. Pour obtenir un exemple montrant comment procéder à l’aide d’une configuration webpack de base, consultez [Créer une application Node.js avec React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Si vous ne connaissez pas les mappages de sources, veuillez lire [Introduction aux mappages de sources JavaScript](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) avant de continuer. 

Afin de configurer les paramètres avancés pour les mappages de sources, utilisez un fichier *tsconfig.json* ou les paramètres du projet dans un projet TypeScript, mais pas les deux.

Pour activer le débogage à l’aide de Visual Studio, vous devez vous assurer que la ou les références à votre fichier source dans le mappage source généré sont correctes (cela peut nécessiter des tests). Par exemple, si vous utilisez WebPack, les références figurant dans le fichier de mappage source incluent le préfixe *WebPack:///* , qui empêche Visual Studio de trouver un fichier source de machine à écrire ou jsx. Plus précisément, lorsque vous corrigez ceci à des fins de débogage, la référence au fichier source (par exemple, *app. TSX*) doit être remplacée par une *valeur telle* que *./app.TSX*, qui active le débogage ( le chemin d’accès est relatif à votre fichier source). L’exemple suivant montre comment vous pouvez configurer des mappages de sources dans WebPack, qui est l’un des bundleeurs les plus courants, afin qu’ils fonctionnent avec Visual Studio.

(WebPack uniquement) Si vous définissez le point d’arrêt dans une machine à écrire de fichier JSX (au lieu d’un fichier JavaScript compilé), vous devez mettre à jour la configuration de votre WebPack. Par exemple, dans *WebPack-config. js*, vous devrez peut-être remplacer le code suivant :

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

par le code suivant :

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Il s’agit d’un paramètre de développement uniquement pour activer le débogage du code côté client dans Visual Studio.

Pour les scénarios complexes, les outils de navigation (**F12**) fonctionnent parfois mieux pour le débogage, car ils ne nécessitent pas de modifications des préfixes personnalisés.

### <a name="configure_source_maps"></a>Configurer des mappages de sources à l’aide d’un fichier TSConfig. JSON

Si vous ajoutez un fichier *tsconfig.json* à votre projet, Visual Studio traite la racine du répertoire comme un projet TypeScript. Pour ajouter le fichier, cliquez avec le bouton droit sur votre projet dans Explorateur de solutions, puis choisissez **ajouter > nouvel élément > fichier de configuration d’une machine à écrire JSON**. Un fichier *tsconfig.json* comme ce qui suit est ajouté à votre projet.

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

* **inlineSourceMap**: émettez un fichier unique avec les mappages de source au lieu de créer un mappage source distinct pour chaque fichier source.
* **inlineSources**: émettez la source avec les mappages de source dans un seul fichier ; requiert la définition de *inlineSourceMap* ou *mappage* .
* **mapRoot**: spécifie l’emplacement où le débogueur doit rechercher les fichiers de mappage source ( *. map*) à la place de l’emplacement par défaut. Utilisez cet indicateur si les fichiers runtime *.map* doivent se trouver dans un emplacement autre que les fichiers *.js*. L’emplacement spécifié est incorporé dans le mappage de source pour diriger le débogueur vers l’emplacement des fichiers *.map*.
* **mappage**: génère un fichier *. map* correspondant.
* **SourceRoot**: spécifie l’emplacement où le débogueur doit rechercher les fichiers de machine à écrire au lieu des emplacements sources. Utilisez cet indicateur si les sources runtime doivent se trouver dans un emplacement autre que celui défini au moment de la conception. L’emplacement spécifié est incorporé dans le mappage de source pour diriger le débogueur vers l’emplacement des fichiers sources.

Pour plus d’informations sur les options du compilateur, consultez la page [Options du compilateur](https://www.typescriptlang.org/docs/handbook/compiler-options.html) dans le manuel TypeScript.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Configurer des mappages de sources à l’aide des paramètres de projet (projet de machine à écrire)

Vous pouvez également configurer les paramètres des mappages de sources à l’aide des propriétés du projet en double-cliquant sur le projet, puis en choisissant **Projet > Propriétés > Build TypeScript > Débogage**.

Ces paramètres de projet sont disponibles.

* **Générer des mappages de source** (équivalent à **mappage** dans *tsconfig. JSON*) : génère le fichier *. map* correspondant.
* **Spécifiez le répertoire racine des mappages de sources** (équivalent à **mapRoot** dans *tsconfig. JSON*) : spécifie l’emplacement où le débogueur doit trouver les fichiers de mappage au lieu des emplacements générés. Utilisez cet indicateur si les fichiers runtime *.map* doivent se trouver dans un emplacement autre que les fichiers .js. L’emplacement spécifié est incorporé dans le mappage de source pour diriger le débogueur vers l’emplacement des fichiers de mappages.
* **Spécifier le répertoire racine des fichiers de base de** code (équivalent à **SourceRoot** dans *tsconfig. JSON*) : spécifie l’emplacement où le débogueur doit rechercher les fichiers de définition de code au lieu des emplacements sources. Utilisez cet indicateur si les fichiers sources runtime doivent se trouver dans un emplacement autre que celui défini au moment de la conception. L’emplacement spécifié est incorporé dans le mappage de source pour diriger le débogueur vers l’emplacement des fichiers sources.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Déboguer JavaScript dans des fichiers dynamiques à l’aide de Razor (ASP.NET)

::: moniker range=">=vs-2019"
À compter de Visual Studio 2019, Visual Studio fournit uniquement la prise en charge du débogage pour chrome et Microsoft Edge (chrome).
::: moniker-end
::: moniker range="vs-2017"
Visual Studio offre des fonctionnalités de débogage dans Chrome et Internet Explorer uniquement.
::: moniker-end

Toutefois, vous ne pouvez pas atteindre automatiquement des points d’arrêt sur des fichiers générés avec syntaxe Razor (cshtml, vbhtml). Il existe deux approches permettant de déboguer ce type de fichier :

* **Placez l’instruction `debugger;` à l’endroit où vous souhaitez**arrêter l’exécution : le script dynamique arrête alors l’exécution et démarre immédiatement le débogage pendant sa création.
* **Charger la page et ouvrir le document dynamique sur Visual Studio**: vous devez ouvrir le fichier dynamique pendant le débogage, définir votre point d’arrêt et actualiser la page pour que cette méthode fonctionne. Selon que vous utilisez Chrome ou Internet Explorer, vous trouverez le fichier en utilisant l’une des stratégies suivantes :

   Pour Chrome, accédez à l’**Explorateur de solutions > Script Documents (Documents de script) > YourPageName (Nom de votre page)** .

    > [!NOTE]
    > Quand vous utilisez Chrome, vous pouvez éventuellement recevoir un message indiquant qu’**aucune source n’est disponible entre les balises \<script>** . Cela n’est pas un problème, continuez simplement le débogage.

   ::: moniker range=">=vs-2019"
   Pour Microsoft Edge (chrome), utilisez la même procédure que Chrome.
   ::: moniker-end

   ::: moniker range="vs-2017"
   Pour Internet Explorer, accédez à **l’Explorateur de solutions > Script Documents (Documents de script) > Windows Internet Explorer > YourPageName (Nom de votre page)** .
   ::: moniker-end

Pour plus d’informations, consultez [Débogage côté client de projets ASP.NET dans Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
