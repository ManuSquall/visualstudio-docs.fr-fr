---
title: Créer une application Vue.js à l’aide de Node.js
description: Vous pouvez créer des applications Node.js dans Visual Studio à l’aide du framework Vue.js
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 338e53d576e9f4d73b32c3f432223480d9e708c3
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683933"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Créer une application Vue.js à l’aide de Node.js Tools pour Visual Studio

Visual Studio prend en charge le développement d’applications avec le framework [Vue.js](https://vuejs.org/) en JavaScript ou TypeScript.

Les nouvelles fonctionnalités suivantes prennent en charge le développement d’applications Vue.js dans Visual Studio :

* Prise en charge des blocs de script, de style et de modèle dans les fichiers *.vue*
* Reconnaissance de l’attribut `lang` dans les fichiers *.vue*
* Modèles de fichier et de projet vue.js

## <a name="prerequisites"></a>Prérequis

* Vous devez avoir installé Visual Studio 2017 version 15.8 ou ultérieure et la charge de travail **Développement Node.js**.

    > [!IMPORTANT]
    > Cet article nécessite des fonctionnalités qui sont uniquement disponibles à partir de Visual Studio 2017 version 15.8.

    ::: moniker range=">=vs-2019"
    Si une version requise n’est pas déjà installée, installez [Visual Studio 2019](https://visualstudio.microsoft.com/downloads).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.
    ::: moniker-end

    Si vous devez installer la charge de travail mais que vous disposez déjà de Visual Studio, accédez à **Outils**  >  **obtenir des outils et des fonctionnalités...**, qui ouvre le Visual Studio installer. Choisissez la charge de travail **Développement Node.js**, puis choisissez **Modifier**.

* Pour créer le projet ASP.NET Core, les charges de travail Développement web et ASP.NET et Développement multiplateforme .NET Core doivent être installées.

* Le runtime Node.js doit être installé.

    Si vous ne l’avez pas déjà fait, installez la version LTS à partir du site web [Node.js](https://nodejs.org/en/download/). En règle générale, Visual Studio détecte automatiquement le runtime Node.js installé. S’il ne détecte aucun runtime installé, vous pouvez configurer votre projet pour faire référence au runtime installé dans la page de propriétés. (Après avoir créé un projet, cliquez avec le bouton droit sur le nœud de projet, puis choisissez **Propriétés**).

## <a name="create-a-vuejs-project-using-nodejs"></a>Créer un projet Vue.js à l’aide de Node.js

Vous pouvez utiliser les nouveaux modèles Vue.js pour créer un projet. L’utilisation du modèle représente la façon la plus simple de bien démarrer. Pour obtenir une procédure détaillée, consultez [Utiliser Visual Studio pour créer votre première application Vue.js](../javascript/quickstart-vuejs-with-nodejs.md).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>Créer un projet Vue.js avec ASP.NET Core et l’interface de ligne de commande Vue

Vue.js fournit une interface de ligne de commande officielle permettant de générer des modèles automatiques rapidement pour les projets. Si vous souhaitez utiliser l’interface de ligne de commande pour créer votre application, suivez les étapes décrites dans cet article pour configurer votre environnement de développement.

> [!IMPORTANT]
> Ces étapes supposent que vous connaissez déjà le framework Vue.js. Dans le cas contraire, visitez [Vue.js](https://vuejs.org/) pour en savoir plus sur le framework.

### <a name="create-a-new-aspnet-core-project"></a>Créer un projet ASP.NET Core

Pour cet exemple, vous utilisez une application ASP.NET Core (C#) vide. Toutefois, vous pouvez choisir parmi un éventail de projets et langages de programmation.

#### <a name="create-an-empty-project"></a>Créer un projet vide

* Ouvrez Visual Studio et créez un projet.

    ::: moniker range=">=vs-2019"
    Dans Visual Studio 2019, choisissez **créer un nouveau projet** dans la fenêtre démarrer. Si la fenêtre de démarrage n’est pas ouverte , choisissez  >  **fenêtre démarrage** de fichier. Tapez **application Web**, choisissez **C#** comme langue, puis choisissez **ASP.net Core vide**, puis **suivant**. Dans l’écran suivant, nommez le projet **client-App**, puis choisissez **suivant**.

    Choisissez le Framework cible recommandé (.NET Core 3,1) ou .NET 5, puis choisissez **créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **Visual C#**, puis choisissez **Web**. Dans le volet central, choisissez **Application web ASP.NET Core**, tapez le nom **client-app**, puis choisissez **OK**.

    Sélectionnez **Vide**, puis cliquez sur **OK**.

    Visual Studio crée le projet qui s’ouvre dans l’Explorateur de solutions (volet droit).
    ::: moniker-end

    Si vous ne voyez pas le modèle de projet **Application web ASP.NET Core**, vous devez d’abord installer les charges de travail **Développement web et ASP.NET** et **Développement .NET Core**. Pour installer les charges de travail, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet** (sélectionnez **Fichier** > **Nouveau** > **Projet**). Visual Studio Installer est lancé. Sélectionnez les charges de travail nécessaires.

#### <a name="configure-the-project-startup-file"></a>Configurer le fichier de démarrage du projet

* Ouvrez le fichier *./Startup.cs* et ajoutez les lignes suivantes à la méthode Configure :

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Installer l’interface CLI Vue

Pour installer le module npm vue-cli, ouvrez une invite de commandes et tapez `npm install --g vue-cli` ou `npm install -g @vue/cli` pour la version 3.0 (actuellement en version bêta).

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Générer automatiquement des modèles pour une nouvelle application cliente à l’aide de l’interface CLI Vue

1. Accédez à l’invite de commandes et remplacez le répertoire actif par votre dossier racine du projet.

1. Tapez `vue init webpack client-app` et suivez les étapes quand vous êtes invité à répondre à des questions supplémentaires.

    > [!NOTE]
    > Pour les fichiers *.vue*, vous devez utiliser WebPack ou un framework similaire avec un chargeur qui effectuera la conversion. TypeScript et Visual Studio ne savent pas compiler des fichiers *.vue*. Il en va de même pour le regroupement : TypeScript ne sait pas convertir des modules ES2015 (autrement dit, les instructions `import` et `export`) en un seul fichier *.js* final à charger dans le navigateur. Ici encore, WebPack est la meilleure solution. Pour exécuter ce processus dans Visual Studio à l’aide de MSBuild, vous devez commencer par un modèle Visual Studio. À l’heure actuelle, il n’existe aucun modèle ASP.NET préconfiguré pour le développement Vue.js.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Modifier la configuration de webpack pour installer les fichiers générés sur wwwroot

* Ouvrez le fichier *./client-app/config/index.js* et remplacez `build.index` et `build.assetsRoot` par le chemin wwwroot :

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Indiquer au projet de générer l’application cliente chaque fois qu’une build est déclenchée

1. Dans Visual Studio, accédez à propriétés du **projet**  >    >  **événements de build**.

1. Dans **Ligne de commande de l’événement pré-build**, tapez `npm --prefix ./client-app run build`.

#### <a name="configure-webpacks-output-module-names"></a>Configurer les noms de module de sortie de webpack

* Ouvrez le fichier *./client-app/build/webpack.base.conf.js* et ajoutez les propriétés suivantes à la propriété de sortie :

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Ajouter la prise en charge de TypeScript avec l’interface CLI Vue

Ces étapes nécessitent vue-cli 3.0 qui est actuellement en version bêta.

1. Accédez à l’invite de commandes et remplacez le répertoire actif par le dossier racine du projet.

1. Tapez `vue create client-app`, puis choisissez **Manually select features** (Sélectionner manuellement les fonctionnalités).

1. Choisissez **Typescript**, puis sélectionnez les autres options de votre choix.

1. Suivez les étapes restantes et répondez aux questions.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Configurer un projet Vue.js pour TypeScript

1. Ouvrez le fichier *./client-app/tsconfig.json* et ajoutez `noEmit:true` aux options du compilateur.

    En définissant cette option, vous évitez d’encombrer votre projet chaque fois que vous générez dans Visual Studio.

1. Créez ensuite un fichier *vue.config.js* dans *./client-app/* et ajoutez le code suivant.

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    Le code précédent configure webpack et définit le dossier wwwroot.

#### <a name="build-with-vue-cli-30"></a>Générer avec vue-cli 3.0

Un problème inconnu avec vue-cli 3.0 peut empêcher l’automatisation du processus de génération. Chaque fois que vous essayez d’actualiser le dossier wwwroot, vous devez exécuter la commande `npm run build` sur le dossier client-app.

Vous pouvez aussi générer le projet vue-cli 3.0 comme un événement pré-build en utilisant les propriétés du projet ASP.NET. Faites un clic droit sur le projet, choisissez **Propriétés** et ajoutez les commandes suivantes dans l’onglet **Build** sous la zone de texte **Ligne de commande de l'événement pré-build**.

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>Limites

* L’attribut `lang` prend uniquement en charge les langages JavaScript et TypeScript. Les valeurs acceptées sont : js, jsx, ts et tsx.
* L’attribut `lang` ne fonctionne pas avec les balises de modèle ni de style.
* Le débogage des blocs de script dans les fichiers *.vue* n’est pas pris en charge en raison de sa nature prétraitée.
* TypeScript ne reconnaît pas les fichiers *.vue* comme modules. Vous avez besoin d’un fichier qui contient du code tel que le suivant pour indiquer à TypeScript à quoi ressemblent les fichiers *.vue* (le modèle vue-cli 3.0 inclut déjà ce fichier).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* L’exécution de la commande `npm run build` comme un événement pré-build sur les propriétés du projet ne fonctionne pas lors de l’utilisation de vue-cli 3.0.

## <a name="see-also"></a>Voir aussi

- [Guide de mise en route Vue](https://vuejs.org/v2/guide).
- [Projet CLI vue d’interface](https://github.com/vuejs/vue-cli).
- [Documentation sur la configuration de webpack](https://webpack.js.org/configuration/).
