---
title: Personnaliser un codeSpace (version préliminaire)
description: En savoir plus sur la personnalisation d’un codeSpace.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 9072676dfc96ffc6286f81785048eca8ec46b0b8
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850505"
---
# <a name="how-to-customize-a-codespace-preview"></a>Comment personnaliser un codeSpace (version préliminaire)

GitHub Codespaces fournit un environnement de développement complet dans le Cloud. Pour le développement basé sur Windows à l’aide de Visual Studio 2019, les instances par défaut de GitHub Codespaces fournissent un excellent point de départ, mais vous pouvez également personnaliser l’environnement pour votre projet spécifique.

## <a name="installed-software"></a>Logiciel installé

Windows codespaces est fourni avec de nombreux frameworks et outils déjà installés pour vous permettre de commencer immédiatement. Le tableau ci-dessous répertorie les applications et les fonctionnalités disponibles dans tous les environnements Windows codeSpace.

| Application                                         | Alias de chemin | Version            |
|---------------------------------------------|------------|--------------------|
| .NET                                        | N/A        | 4.8                |
| Runtime .NET Core                           | dotnet     | 2,1, 3,1           |
| SDK .NET Core                               | dotnet     | 2,1, 3.1.3, 3.1.4  |
| Azure CLI                                   | AZ         | 2.5                |
| Chocolatey                                  | choco      | 0.10.15            |
| CMake                                       | cmake      | 3.17               |
| Git                                         | git        | 2,26               |
| Microsoft Build                             | MSBuild    | 16.7               |
| Édition Microsoft SQL Server Express 2019   | N/A        | 15.0               |
| Ninja                                       | Ninja      | 1.8.2              |
| Node.js                                     | node       | 12.16              |
| NPM                                         | npm        | 6.14               |
| Python                                      | python     | 3.7                |
| Gestionnaire de Package VC                          | vcpkg      | 2020,02            |
| Kit de développement logiciel (SDK) Windows                                 | N/A        | 10.0.18362         |

La liste ci-dessus n’est pas exhaustive et exclut de nombreux outils installés par Visual Studio (par exemple, IISExpress). Un composant peut également avoir une version mineure ou corrective différente de celle indiquée ci-dessus.

Des détails spécifiques sur les infrastructures et les outils préinstallés sont fournis dans la section Détails sur les [logiciels installés](#installed-software-specifics) ci-dessous.

## <a name="modifications-to-a-codespace"></a>Modifications apportées à un codeSpace
 
Une fois que vous avez créé un codeSpace, toutes les modifications apportées à ce codeSpace spécifique sont conservées alors que l’instance codeSpace est disponible sur GitHub Codespaces. Vous pouvez cloner des référentiels supplémentaires, installer des outils et des générateurs d’applications et ajouter d’autres ressources de développement, et ces modifications sont conservées même lorsque le codeSpace est suspendu. Toutefois, si vous supprimez un codeSpace, toutes les modifications ont disparu.

> [!NOTE]
> Si vous supprimez un codeSpace, toutes les modifications apportées à un référentiel local (en attente ou validé) dans le codeSpace seront perdues. Veillez à envoyer les modifications du référentiel à un emplacement distant avant de supprimer un codeSpace.

Quand vous êtes connecté à un codeSpace avec Visual Studio, vous pouvez utiliser le terminal Visual Studio pour exécuter les outils en ligne de commande. Vous pouvez utiliser PowerShell ou l’invite de commandes Windows, les deux étant élevés sous le compte administrateur local. Pour en savoir plus sur le terminal Visual Studio, consultez le blog de l’annonce sur les [terminaux Visual Studio](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/).

## <a name="customize-a-codespace"></a>Personnaliser un codespace

La valeur réelle de GitHub Codespaces est fournie lorsque vous pouvez créer des environnements de développement uniques et reproductibles dans le Cloud et les adapter à votre propre travail, ainsi qu’à ceux de votre équipe. En générant sur une instance GitHub Codespaces par défaut, vous pouvez personnaliser ce qui est installé et configuré lorsque vous créez un nouveau codeSpace.

Les sections suivantes décrivent deux méthodes de configuration codeSpace à l’aide de *.devcontainer.jssur* et *.devinit.jssur* les fichiers. Ces fichiers vous permettent de configurer les infrastructures et les outils d’installation d’un codeSpace et, lorsqu’ils sont ajoutés à votre référentiel, toute personne créant un codeSpace basé sur votre dépôt aura le même environnement de développement distant.

## <a name="customize-with-devcontainerjson"></a>Personnaliser avec devcontainer.js

Lorsqu’un codeSpace est créé, GitHub Codespaces recherche une [*devcontainers.jssur*](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) le fichier à la racine de votre référentiel et utilise les paramètres dans pour personnaliser les codeSpace ou les instances clientes qui se connectent à celui-ci (navigateur-éditeur de base, Visual Studio ou Visual Studio code). La plupart des *devcontainer.jssur* les paramètres s’appliquent aux codespaces basés sur Linux ou aux deux autres clients, mais certains sont disponibles pour Windows Codespaces et Visual Studio.

Le *devcontainer.jssur* le fichier peut être placé dans l’un des deux emplacements d’un référentiel :

1. *{Repository-root}/.devcontainer.jssur*
2. *{Repository-root}/.devcontainer/devcontainer.js*

GitHub Codespaces prend en charge les *devcontainer.jssuivantes sur* les propriétés. La définition de Visual Studio Code propriétés spécifiques est utile si vous vous attendez à vous connecter à votre codeSpace avec les autres clients en plus de Visual Studio. 

* `extensions` -Un tableau d’extensions de la place de [marché Visual Studio code](https://marketplace.visualstudio.com/vscode) qui doivent être installées.
* `settings`  : Ensemble de [paramètres de Visual Studio code](https://code.visualstudio.com/docs/getstarted/settings) à appliquer.
* `forwardPorts`-Un port ou un tableau de ports qui doivent être transférés automatiquement localement lorsque le codeSpace est en cours d’exécution.
* `postCreateCommand` -Une chaîne de commande ou une liste d’arguments de commande à exécuter après la création du codeSpace.

> [!NOTE]
> Les fichiers **devcontainer.js** sont également utilisés pour prendre en charge Visual Studio code le [développement à distance](https://code.visualstudio.com/docs/remote/remote-overview)et ont des propriétés supplémentaires non traitées dans ce document. Ces propriétés supplémentaires peuvent être ajoutées en toute sécurité au fichier, mais seront ignorées par Codespaces. Pour plus d’informations, consultez la [devcontainer.jssur la page de référence](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) sur code.VisualStudio.com.

## <a name="customize-with-devinit"></a>Personnaliser avec devinit

[devinit](../../devinit/getting-started-with-devinit.md) est un outil de ligne de commande inclus dans Windows codespaces qui vous permet d’installer des frameworks et des outils dans votre environnement. Il peut être exécuté manuellement à partir d’une invite de commandes ( `devinit run -t require-dotnetcoresdk` ), mais sa véritable puissance provient de la création d’un [ *.devinit.jspersonnalisé sur le*](../../devinit/devinit-json.md) fichier pour configurer de manière uniforme un codeSpace à chaque fois que vous en créez un.

`devinit` comprend un ensemble d’outils permettant d’installer des éléments spécifiques, tels que des SQL Server et des Azure CLI, ainsi que des gestionnaires de packages généraux tels que Chocolate, NPM et vcpkg. Vous trouverez la liste complète des `devinit` outils dans la documentation sur les [outils disponibles](../../devinit/devinit-tool-list.md) .

### <a name="devinitjson"></a>devinit.js

Bien que vous puissiez exécuter `devinit` directement la ligne de commande, nous vous recommandons de créer des [*devinit.jssur*](../../devinit/devinit-json.md) les fichiers de configuration, qui décrivent l’ensemble d' `devinit` Outils à exécuter. 

Par exemple, pour installer le [Kit SDK .net Core](/dotnet/core/sdk), un *.devinit.js* peut se présenter comme suit :

```json
{
    "run": [
        {
            "comments": "We need the .NET Core SDK."
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

Lorsque vous créez un *.devinit.jssur* le fichier à la racine de votre projet, il est utilisé lorsque vous exécutez `devinit init` . Par défaut, `devinit.exe` recherche le fichier aux emplacements suivants :

1. *{Current-Directory} \\.devinit.js*
2. *{Current-Directory} \\.devinit\devinit.js*

### <a name="running-devinit-when-creating-a-codespace"></a>Exécution de devinit lors de la création d’un codeSpace

Vous pouvez demander à GitHub Codespaces de s’exécuter `devinit` après la création d’un codeSpace à l’aide de la `postCreateCommand` propriété dans un *devcontainers.jssur* le fichier. Comme indiqué ci-dessus, GitHub Codespaces recherche une *devcontainer.jssur* le fichier dans votre référentiel cloné afin de personnaliser l’instance codeSpace ou client et exécute toutes les commandes décrites dans la `postCreateCommand` propriété.

En spécifiant `devinit init` , `devinit` est exécuté à l’aide de votre *devinit.jssur* la configuration.

```json
{
  "postCreateCommand": "devinit init"
}
```

### <a name="an-example"></a>Exemple

Voici un exemple simple d’installation de l’outil en ligne de commande Entity Framework .NET Core, `dotnet-ef` .

**devcontainer.js**

Contenu de l' *.devcontainer.jssur* le fichier dans la racine référentiel. 

```json
{
  "postCreateCommand": "devinit init"
}
```

**devinit.js**

Contenu du *.devinit.jssur* le fichier. Ce fichier doit se trouver dans le même dossier que *.devcontainer.js*.

```json
{
    "run": [
        {
            "comments": "Install the Entity Framework tools",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
        }
     ]
}
```

Vous trouverez d’autres `devinit` exemples dans la `devinit` [liste d’exemples](../../devinit/sample-readme.md).

## <a name="port-forwarding"></a>Réacheminement de port

GitHub Codespaces permet d’accéder aux applications et aux services exécutés dans les environnements distants au moyen de la réacheminement de port. Par défaut, aucun port n’est transféré pour des problèmes de sécurité. Toutefois, vous pouvez spécifier certains ports à ouvrir dans un codeSpace.

### <a name="configure-port-forwarding"></a>Configurer le réacheminement de port

S’il existe un ou plusieurs ports qui doivent être transférés par défaut pour un référentiel donné, ceux-ci peuvent être configurés dans *devcontainer.js* avec la `forwardPorts` propriété.

* `forwardPorts` -Un port ou un tableau de ports qui doivent être transférés automatiquement localement lorsque l’environnement est en cours d’exécution.

## <a name="installed-software-specifics"></a>Caractéristiques logicielles installées

### <a name="microsoft-sql-server"></a>Microsoft SQL Server

Microsoft SQL Server 2019 Express Edition est disponible et s’exécute en tant que service local dans l’environnement Windows codeSpace. L’utilisateur actuel, sur lequel votre application et le terminal Visual Studio s’exécutent, disposent de droits d’administrateur SQL sur le serveur SQL Server. Pour administrer le serveur, vous devez utiliser PowerShell dans le terminal Visual Studio ou d’autres outils de ligne de commande tels que `dotnet-ef` . Actuellement SQL Server Management Studio et d’autres outils d’administration à distance ne sont pas disponibles.

#### <a name="example-connection-string"></a>Exemple de chaîne de connexion

Voici un exemple de chaîne de connexion pour se connecter au serveur MS SQL Server local.

```csharp
"Server=(LocalDB);Integrated Security=true;"
```

### <a name="azure-cli"></a>Azure CLI

Le Azure CLI est installé dans tous les environnements codeSpace Windows et est disponible sur le chemin d’accès en tant que `az` .

#### <a name="using-azure-resources"></a>Utilisation des ressources Azure

Si vous utilisez une identité de Azure Active Directory pour authentifier votre application auprès des ressources Azure, vous devez d’abord vous connecter à Azure à partir du terminal Visual Studio. Pour vous connecter, utilisez la `login` commande Azure CLI avec le déroulement de la connexion de l’appareil (comme indiqué dans l’exemple ci-dessous). Une fois connecté, votre application et votre session Terminal Server doivent être en mesure d’utiliser cette identité.

```powershell
> az login --use-device-code
```

Vous pouvez en savoir plus sur la `az login` commande dans la [documentation](/cli/azure/reference-index#az_login)de Azure CLI.

## <a name="see-also"></a>Voir aussi

- [Qu’est-ce que GitHub Codespaces ?](codespaces-overview.md)
- [Utilisation de Visual Studio avec un codeSpace](use-visual-studio-with-codespaces.md)