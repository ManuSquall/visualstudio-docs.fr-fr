---
title: Didacticiel
description: Didacticiel pour devinit.
ms.date: 11/18/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 32d407c4803c2b50276145a2c9a66c2c501f05ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874419"
---
# <a name="tutorial"></a>Didacticiel

Dans ce didacticiel, nous allons explorer la configuration du [référentiel eShopOnWeb](https://github.com/andysterland/eShopOnWeb) avec Devinit et Codespaces. Ce didacticiel part du principe que devinit est déjà disponible, comme décrit dans la [page mise en route](getting-started-with-devinit.md).

## <a name="step-1-determining-setup-steps"></a>Étape 1 : détermination des étapes de configuration

Comme mentionné dans la [page mise](getting-started-with-devinit.md)en route, la première étape consiste toujours à déterminer les dépendances et les étapes de configuration de votre projet. Cela dépend du projet spécifique, mais il existe quelques questions à prendre en compte :

- À quels runtimes ou kits de développement logiciel dépendent votre projet ?
- Votre projet nécessite-t-il des packages (par exemple, du chocolat) ?
- Votre processus d’installation nécessite-t-il des actions à entreprendre (par exemple, l’exécution d’un script) ?
- Votre projet a-t-il des dépendances implicites sur tout ce qui est installé avec Visual Studio ?
  - Si c’est le cas, il est judicieux de les inclure également dans votre configuration devinit. De cette façon, vous pouvez éviter d’associer l’installation de Visual Studio.

L’une des meilleures façons de déterminer ces informations consiste à explorer les étapes de configuration manuelles dont vous disposez actuellement pour votre référentiel. Pour eShopOnWeb, vous devez gérer quelques éléments :

- Installation de la dernière version du kit SDK .NET Core
- Installation de la dernière version de .NET Entity Framework Core Tools CLI
- Installation de SQL Server 2019 Express
- Utilisation de l’interface CLI .NET Entity Framework pour mettre à jour la base de données locale vers la dernière migration

Ensuite, nous allons découvrir comment accomplir tout cela dans le contexte de devinit.

## <a name="step-2-the-devinitjson"></a>Étape 2 : le .devinit.jssur

Tout d’abord, nous voulons construire un [.devinit.jssur le fichier](devinit-json.md) et le placer à la racine de notre référentiel. Ce fichier inclut une série d’étapes qui seront exécutées ultérieurement dans le cadre d’une `devinit init` commande. Pour déterminer ce qui doit être inclus dans le `.devinit.json` fichier, nous pouvons suivre notre liste d’étapes de configuration et la comparer à la liste des [Outils devinit](devinit-tool-list.md). Nous allons maintenant effectuer les étapes de configuration ci-dessus.

| Étape                                                              | Devinit peut-il le gérer pour nous ?                                                                        |
| :---------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------  |
| Installer la dernière kit SDK .NET Core                                      | **Oui**. Nous pouvons utiliser l' [ `require-dotnetcoresdk` outil](tool-require-dotnetcoresdk.md)                  |
| Installer .NET Entity Framework Core Tools CLI                      | **Oui**. Nous pouvons utiliser l' [ `dotnet-toolinstall` outil](tool-dotnet-toolinstall.md)                        |
| Installer SQL Server 2019 Express                                   | **Oui**. Nous pouvons utiliser l' [ `choco-install` outil](tool-choco-install.md)                                  |
| Mettre à jour la base de données locale à l’aide de .NET Entity Framework                 | **Non**, mais nous continuons à le faire en combinant devinit avec un script !                               |

Maintenant que nous avons déterminé cela, commençons par un simple `.devinit.json` . Nous allons inclure une référence au [ `.devinit.json` schéma](https://json.schemastore.org/devinit.schema-2.0)et une `run` section vide :

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": []
}
```

À présent, nous allons ajouter des outils.

Tout d’abord, nous allons ajouter [`require-dotnetcoresdk`](tool-require-dotnetcoresdk.md) . À partir de la documentation de cet outil, nous pouvons voir que le comportement par défaut consiste à installer la dernière version du kit de développement logiciel (SDK). C’est exactement ce que nous voulons, nous allons donc l’ajouter à notre `.devinit.json` :

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    }
  ]
}
```

Deuxièmement, nous ajouterons [`dotnet-toolinstall`](tool-dotnet-toolinstall.md) pour installer l' `dotnet-ef` outil globalement. Dans la documentation, nous voyons que nous pouvons utiliser le `input` champ pour spécifier le nom de l’outil et le `additionalOptions` champ pour spécifier l’étendue globale :

```json
{
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    },
    {
      "comments": "Install latest version of the .NET Entity Framework Core Tools CLI.",
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global"
    }
  ]
}
```

Enfin, nous ajouterons [`choco-install`](tool-choco-install.md) pour installer le `sql-server-express` Package.

```json
{
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    },
    {
      "comments": "Install latest version of the .NET Entity Framework Core Tools CLI.",
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global"
    },
    {
      "comments": "Install SQL Server 2019 Express",
      "tool": "choco-install",
      "input": "sql-server-express"
    }
  ]
}
```

Maintenant que `.devinit.json` nous avons terminé, nous pouvons travailler sur un script d’installation qui s’occupera de l’exécution de devinit et de la mise à jour de la base de données locale.

## <a name="step-3-the-setup-script"></a>Étape 3 : le script d’installation

Pour gérer à la fois les devinit en cours d’exécution et la mise à jour de la base de données locale, nous allons créer un script qui exécute les commandes nécessaires. Nous allons créer un script PowerShell vide dans notre racine de référentiel, nommée `PostCloneSetup.ps1` . Tout d’abord, nous allons ajouter un appel à `devinit init` :

```powershell
devinit init
```

Lorsqu’il est exécuté, `devinit init` exécute tous les outils définis dans la `run` section de notre `.devinit.json` .

Enfin, nous voulons appeler `dotnet ef database update` pour la mise à jour de la base de données locale :

```powershell
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

Maintenant que notre script d’installation est terminé, nous devons ajouter un `.devcontainer.json` fichier qui l’exécutera lors de l’installation de codeSpace.

## <a name="step-4-the-devcontainerjson"></a>Étape 4 : .devcontainer.jssur

Pour vous assurer que notre script d’installation est exécuté pendant la création de notre codeSpace, nous allons utiliser un `.devcontainer.json` fichier. Comme pour les autres fichiers, il doit être placé dans la racine du référentiel.

Dans le `.devcontainer.json` fichier, il vous suffit d’appeler notre script de configuration dans le cadre du `postCreateCommand` . Ce sera exécuté dans le cadre du processus de création de codeSpace :

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```

C’est tout !

## <a name="step-5-trying-it-out"></a>Étape 5 : essai

Maintenant que nos étapes de configuration sont en place, essayons cela dans un codeSpace en direct à l’aide du [référentiel réel](https://github.com/andysterland/eShopOnWeb).

Tout d’abord, nous allons créer un codeSpace à l’aide de Visual Studio :

:::image type="content" source="media/eshoponweb-github-codespaces-prompt.png" alt-text="Création d’un codeSpace":::

Une fois la création de codeSpace démarrée, nous pouvons observer la progression de notre processus d’installation dans `C:\.vsonline\.vsoshared\vmTerminal.dat` :

:::image type="content" source="media/eshoponweb-watching-progress.png" alt-text="Surveillance de la progression de l’installation":::

Une fois l’exécution terminée, nous allons exécuter l’application via `Web.csproj` pour vérifier que tout fonctionne correctement :

:::image type="content" source="media/eshoponweb-csproj.png" alt-text="Exécution du projet":::

Une fois l’application générée et lancée, nous pouvons voir le magasin dans notre navigateur Web :

:::image type="content" source="media/eshoponweb-live.png" alt-text="Affichage du site":::

Notre processus d’installation fonctionnait correctement et nous sommes maintenant prêts à développer dans le projet eShopOnWeb.
