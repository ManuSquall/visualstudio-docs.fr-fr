---
title: Déboguer une application JavaScript ou TypeScript
description: Visual Studio prend en charge pour le débogage des applications JavaScript et TypeScript dans Visual Studio
ms.date: 12/03/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 29b58d588a07be8ba25ab844da171222c57df545
ms.sourcegitcommit: 8bfabab73b39b3b3e68a3e8dc225515e8b310fed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2019
ms.locfileid: "54398232"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Déboguer une application JavaScript ou TypeScript dans Visual Studio

Vous pouvez déboguer un code JavaScript et TypeScript à l’aide de Visual Studio. Vous pouvez définir et atteindre des points d’arrêt, attacher le débogueur, inspecter des variables, afficher la pile des appels et utiliser d’autres fonctionnalités de débogage.

> [!TIP]
> Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement. Selon le type de développement d’applications que vous exécutez, vous devrez peut-être installer la **charge de travail de développement Node.js** avec Visual Studio.

## <a name="debug-server-side-script"></a>Déboguer un script côté serveur

1. Une fois votre projet ouvert dans Visual Studio, ouvrez un fichier JavaScript côté serveur (par exemple *server.js*), puis cliquez dans la marge à gauche pour définir un point d’arrêt :

    ![Définir un point d’arrêt](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code.

1. Pour exécuter votre application, appuyez sur **F5** (**Déboguer** > **Démarrer le débogage**).

    Le débogueur s’arrête au point d’arrêt que vous avez défini (l’instruction active est marquée en jaune). Vous pouvez maintenant inspecter l’état de votre application en pointant sur les variables situées dans la portée et en utilisant les fenêtres du débogueur, notamment les fenêtres **Variables locales** et **Espion**.

1. Appuyez sur **F5** pour continuer l’exécution de l’application.

1. Pour utiliser les outils de développement Chrome ou les outils F12, appuyez sur **F12**. Vous pouvez utiliser ces outils pour examiner le DOM et interagir avec l’application à l’aide de la console JavaScript.

## <a name="debug-client-side-script"></a>Débogage de script côté client

Visual Studio offre des fonctionnalités de débogage dans Chrome et Internet Explorer uniquement. Dans certains scénarios, le débogueur atteint automatiquement les points d’arrêt dans le code JavaScript et TypeScript et dans des scripts incorporés dans des fichiers HTML.

Si votre source est minimisée ou créée par un transpiler comme TypeScript ou Babel, utilisez des [mappages de sources](#generate_sourcemaps) pour bénéficier d’une meilleure expérience de débogage. Sans les mappages de sources, il est néanmoins possible d’attacher le débogueur à un script en cours d’exécution côté client. Mais vous pourrez seulement définir et atteindre des points d’arrêt dans le fichier minimisé ou transpilé, et non dans le fichier source d’origine. Par exemple, dans une application Vue.js, un script minimisé est passé sous forme de chaîne à une instruction `eval`, et il n’existe aucun moyen de parcourir ce code efficacement à l’aide du débogueur Visual Studio, à moins d’utiliser des mappages de sources. Dans certains scénarios de débogage complexes, vous pouvez également utiliser les outils de développement Chrome ou les outils F12 pour Microsoft Edge.

Pour attacher le débogueur depuis Visual Studio et atteindre des points d’arrêt dans du code côté client, vous devez généralement aider le débogueur à identifier le processus approprié. Voici une façon d’y parvenir en utilisant Chrome.

### <a name="attach-the-debugger-to-client-side-script-using-chrome"></a>Attacher le débogueur à un script côté client à l’aide de Chrome

1. Fermez toutes les fenêtres de Chrome.

    Cette action est nécessaire pour pouvoir exécuter Chrome en mode débogage.

2. Ouvrez la commande **Exécuter** à partir du bouton **Démarrer** de Windows (cliquez avec le bouton droit de la souris et choisissez **Exécuter**), puis entrez la commande suivante :

    `chrome.exe --remote-debugging-port=9222`

    Cette commande Chrome démarre avec l’activation du débogage.

3. Basculez vers Visual Studio et définissez un point d’arrêt dans votre code source. (Définissez le point d’arrêt dans une ligne de code autorisant les points d’arrêt, par exemple une instruction `return` ou une déclaration `var`).

    ![Définir un point d’arrêt](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Si vous avez besoin rechercher un code spécifique dans un fichier volumineux généré, utilisez **Ctrl**+**F** (**Édition** > **Rechercher et remplacer**  >  **Recherche rapide**).

4. Chrome étant sélectionné comme cible de débogage dans Visual Studio, appuyez sur **Ctrl**+**F5** (**Déboguer** > **Exécuter sans débogage**) pour exécuter l’application dans le navigateur.

    L’application s’ouvre dans un nouvel onglet du navigateur.

    Si Chrome est disponible sur votre ordinateur, mais n’apparaît pas dans les options, choisissez **Naviguer avec** dans la liste déroulante des cibles de débogage et sélectionnez Chrome comme cible de navigateur par défaut (choisissez **Définir comme programme par défaut**).

5. Choisissez **Déboguer** > **Attacher au processus**.

6. Dans la boîte de dialogue **Attacher au processus**, choisissez **Code WebKit** dans le champ **Attacher à**, puis tapez **chrome** dans la zone de filtre pour filtrer les résultats de la recherche.

    **Code WebKit** est la valeur requise pour Chrome, qui est un navigateur basé sur Webkit.

7. Sélectionnez le processus Chrome et le port d’hôte approprié (1337 dans cette illustration), puis sélectionnez **Attacher**.

    ![Attacher au processus](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Vous savez que le débogueur est correctement attaché quand l’Explorateur DOM et la console JavaScript s’ouvrent dans Visual Studio. Ces outils de débogage sont similaires aux outils de développement Chrome et aux outils F12 pour Microsoft Edge.

    > [!NOTE]
    > Si le débogueur ne s’attache pas et que vous voyez le message « Impossible de s’attacher au processus. Une opération n’est pas légale dans l’état actuel. », utilisez le Gestionnaire des tâches pour fermer toutes les instances de Chrome avant de démarrer Chrome en mode débogage. Les extensions Chrome peuvent être en cours d’exécution et empêcher le mode débogage complet.

8. Si le code avec le point d’arrêt s’est déjà exécuté, actualisez la page de votre navigateur pour atteindre le point d’arrêt.

    Pendant que l’exécution du débogueur est en pause, vous pouvez examiner l’état de votre application en pointant sur les variables et en utilisant les fenêtres du débogueur. Vous pouvez faire avancer le débogueur en exécutant pas à pas le code (**F5**, **F10** et **F11**).

    Pour un fichier JavaScript minimisé ou transpilé, vous pouvez atteindre le point d’arrêt dans le fichier JavaScript transpilé ou à son emplacement mappé dans votre fichier TypeScript (à l’aide des mappages de sources), selon l’état de votre environnement et de votre navigateur. De toute façon, vous pouvez exécuter pas à pas le code et examiner les variables.

    * Si vous devez arrêter l’exécution du code dans un fichier TypeScript et que vous n’y parvenez pas, utilisez **Attacher au processus** comme décrit dans la procédure précédente pour attacher le débogueur. Ouvrez ensuite le fichier TypeScript généré dynamiquement à partir de l’Explorateur de solutions en ouvrant **Documents de script** > **filename.tsx**, définissez un point d’arrêt, puis actualisez la page dans votre navigateur (définissez le point d’arrêt dans une ligne de code qui autorise les points d’arrêt, par exemple l’instruction `return` ou une déclaration `var`).

        Sinon, si vous devez arrêter l’exécution du code dans un fichier TypeScript et que vous n’y parvenez pas, essayez d’utiliser l’instruction `debugger;` dans le fichier TypeScript, ou définissez des points d’arrêt dans les outils de développement Chrome à la place.

    * Si vous devez arrêter l’exécution du code dans un fichier JavaScript transpilé (par exemple, *app-bundle.js*) et que vous n’y parvenez pas, supprimez le fichier de mappage de source, *filename.js.map*.

     > [!TIP]
     > Une fois que vous avez effectué l’attachement au processus la première fois en suivant ces étapes, vous pouvez rapidement effectuer un rattachement au même processus dans Visual Studio 2017 en choisissant **Déboguer** > **Rattacher au processus**.

## <a name="generate_sourcemaps"></a> Générer des mappages de sources pour le débogage

Visual Studio permet d’utiliser et de générer des mappages de sources sur les fichiers sources JavaScript. Cela est souvent nécessaire si votre source est minimisée ou créée par un transpiler comme TypeScript ou Babel. Les options disponibles varient selon le type de projet.

* Par défaut, un projet TypeScript dans Visual Studio génère pour vous des mappages de sources.

* Dans un projet JavaScript, vous devez générer des mappages de sources à l’aide d’un bundler comme webpack et d’un compilateur comme TypeScript (ou Babel), que vous pouvez ajouter à votre projet. Pour le compilateur TypeScript, vous devez également ajouter un fichier *tsconfig.json*. Pour obtenir un exemple montrant comment procéder à l’aide d’une configuration webpack de base, consultez [Créer une application Node.js avec React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Si vous ne connaissez pas les mappages de sources, veuillez lire [Introduction aux mappages de sources JavaScript](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) avant de continuer.

Afin de configurer les paramètres avancés pour les mappages de sources, utilisez un fichier *tsconfig.json* ou les paramètres du projet dans un projet TypeScript, mais pas les deux.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a>Configurer des mappages de sources à l’aide d’un fichier tsconfig.json

Si vous ajoutez un fichier *tsconfig.json* à votre projet, Visual Studio traite la racine du répertoire comme un projet TypeScript. Pour ajouter le fichier, cliquez avec le bouton droit sur votre projet dans l’Explorateur de solutions, puis choisissez **Add (Ajouter) > New Item (Nouvel élément) > Web > Scripts > TypeScript JSON Configuration File (Fichier de configuration JSON TypeScript)**. Un fichier *tsconfig.json* comme ce qui suit est ajouté à votre projet.

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

* **inlineSourceMap** : émettre un seul fichier avec des mappages de sources au lieu de créer un mappage de source distinct pour chaque fichier source.
* **inlineSources** : émettre la source en même temps que les mappages de sources au sein d’un seul fichier ; nécessite la définition de *inlineSourceMap* ou de *sourceMap*.
* **mapRoot** : spécifie l’emplacement où le débogueur doit trouver les fichiers du mappage de source (*.map*) au lieu de l’emplacement par défaut. Utilisez cet indicateur si les fichiers runtime *.map* doivent se trouver dans un emplacement autre que les fichiers *.js*. L’emplacement spécifié est incorporé dans le mappage de source pour diriger le débogueur vers l’emplacement des fichiers *.map*.
* **sourceMap** : génère le fichier *.map* correspondant.
* **sourceRoot** : spécifie l’emplacement où le débogueur doit trouver les fichiers TypeScript au lieu des emplacements sources. Utilisez cet indicateur si les sources runtime doivent se trouver dans un emplacement autre que celui défini au moment de la conception. L’emplacement spécifié est incorporé dans le mappage de source pour diriger le débogueur vers l’emplacement des fichiers sources.

Pour plus d’informations sur les options du compilateur, consultez la page [Options du compilateur](https://www.typescriptlang.org/docs/handbook/compiler-options.html) dans le manuel TypeScript.

### <a name="configure-source-maps-using-project-settings"></a>Configurer des mappages de sources à l’aide des paramètres du projet

Vous pouvez également configurer les paramètres des mappages de sources à l’aide des propriétés du projet en double-cliquant sur le projet, puis en choisissant **Projet > Propriétés > Build TypeScript > Débogage**.

Ces paramètres de projet sont disponibles.

* **Générer des mappages de sources** (équivalent à **sourceMap** dans *tsconfig.json*) : génère le fichier *.map* correspondant.
* **Spécifier le répertoire racine des mappages de sources** (équivalent à **mapRoot** dans *tsconfig.json*) : spécifie l’emplacement où le débogueur doit trouver les fichiers de mappages au lieu des emplacements générés. Utilisez cet indicateur si les fichiers runtime *.map* doivent se trouver dans un emplacement autre que les fichiers .js. L’emplacement spécifié est incorporé dans le mappage de source pour diriger le débogueur vers l’emplacement des fichiers de mappages.
* **Spécifier le répertoire racine des fichiers TypeScript** (équivalent à **sourceRoot** dans *tsconfig.json*) : spécifie l’emplacement où le débogueur doit trouver les fichiers TypeScript au lieu des emplacements sources. Utilisez cet indicateur si les fichiers sources runtime doivent se trouver dans un emplacement autre que celui défini au moment de la conception. L’emplacement spécifié est incorporé dans le mappage de source pour diriger le débogueur vers l’emplacement des fichiers sources.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Déboguer JavaScript dans des fichiers dynamiques à l’aide de Razor (ASP.NET)

Visual Studio offre des fonctionnalités de débogage dans Chrome et Internet Explorer uniquement. Il attache automatiquement les points d’arrêt à JavaScript/TypeScript et à des scripts incorporés dans les fichiers HTML.

Le débogage des fichiers générés dynamiquement n’est pas automatique. Vous ne pouvez pas atteindre automatiquement des points d’arrêt dans les fichiers générés avec la syntaxe Razor (cshtml, vbhtml). Il existe deux approches permettant de déboguer ce type de fichier :

* **Placer l’instruction `debugger;` où vous souhaitez créer le point d’arrêt** : cela interrompt l’exécution du script dynamique et démarre aussitôt le débogage pendant la création de ce script.
* **Charger la page et ouvrir le document dynamique dans Visual Studio** : pour que cette méthode fonctionne, vous devrez ouvrir le fichier dynamique pendant le débogage, définir votre point d’arrêt, puis actualiser la page. Selon que vous utilisez Chrome ou Internet Explorer, vous trouverez le fichier en utilisant l’une des stratégies suivantes :

   Pour Chrome, accédez à l’**Explorateur de solutions > Script Documents (Documents de script) > YourPageName (Nom de votre page)**.

    > [!NOTE]
    > Lorsque vous utilisez Chrome, vous pouvez obtenir un message `no source is available between `<script>` tags.` This is OK, just continue debugging.

   Pour Internet Explorer, accédez à **l’Explorateur de solutions > Script Documents (Documents de script) > Windows Internet Explorer > YourPageName (Nom de votre page)**.

Pour plus d’informations, consultez [Débogage côté client de projets ASP.NET dans Google Chrome](https://blogs.msdn.microsoft.com/webdev/2016/11/21/client-side-debugging-of-asp-net-projects-in-google-chrome/).
