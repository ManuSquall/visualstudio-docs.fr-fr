---
title: Créer une installation réseau
description: Découvrez comment créer un point d’installation réseau pour le déploiement de Visual Studio en entreprise.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 080c4450cfcdca28386811865229af75303beb6a
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307529"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Créer une installation réseau de Visual Studio

Parfois, un administrateur d’entreprise souhaite créer un point d’installation réseau contenant des fichiers Visual Studio qui peuvent être déployés sur des stations de travail clientes. Cela permet de faciliter les scénarios dans lesquels les ordinateurs clients peuvent avoir des autorisations limitées ou un accès limité à Internet, ou lorsque les équipes internes souhaitent effectuer des tests de compatibilité avant que leur organisation ne se normalise sur une version particulière de l’ensemble d’outils de développement. Nous avons conçu Visual Studio pour qu’un administrateur puisse _créer une disposition réseau_ qui crée essentiellement un cache de fichiers situé sur un partage réseau statique interne qui comprend tous les fichiers Visual Studio pour l’installation initiale et toutes les futures mises à jour de produits.

 > [!NOTE]
 >  - Si vous avez plusieurs éditions de Visual Studio en cours d’utilisation au sein de votre entreprise (par exemple, Visual Studio 2019 Professional et Visual Studio 2019 Enterprise), vous devez créer un partage d’installation réseau distinct pour chaque édition.
 >  - Nous vous recommandons de choisir la façon dont vous souhaitez que les clients reçoivent les mises à jour du produit _avant_ d’effectuer l’installation initiale du client.  Il est ainsi plus facile de vérifier que vos options de configuration sont correctement définies. Vos choix incluent le fait que les clients obtiennent des mises à jour à partir de l’emplacement de la disposition du réseau ou d’Internet. 
 >  - La mise en page d’origine de l’installation de Visual Studio et toutes les mises à jour de produit ultérieures doivent se trouver dans le même répertoire réseau pour garantir le bon fonctionnement de la fonctionnalité de réparation et de désinstallation.

## <a name="download-the-visual-studio-bootstrapper"></a>Télécharger le programme d’amorçage de Visual Studio

Téléchargez un fichier de programme d’amorçage pour l’édition de Visual Studio souhaitée. Veillez à choisir **Enregistrer**, puis choisissez **ouvrir le dossier**.

::: moniker range="vs-2017"

Pour obtenir le dernier programme d’amorçage pour Visual Studio 2017 version 15,9, accédez à la page [versions précédentes de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) et téléchargez l’un des fichiers de programme d’amorçage suivants :

| Édition                                      | Nom de fichier            |
|----------------------------------------------|---------------------|
| Visual Studio 2017 Enterprise version 15,9   | vs_enterprise.exe   |
| Visual Studio 2017 professionnel version 15,9 | vs_professional.exe |
| Outils de génération Visual Studio 2017 version 15,9  | vs_buildtools.exe   |

Les autres programmes d’amorçage pris en charge incluent vs_feedbackclient.exe, vs_teamexplorer.exe, vs_testagent.exe, vs_testcontroller.exe et vs_testprofessional.exe.

::: moniker-end

::: moniker range="vs-2019"

Commencez par Télécharger le programme d’amorçage de Visual Studio 2019 à partir de la [page téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) ou de la page [versions de Visual Studio 2019](/visualstudio/releases/2019/history#installing-an-earlier-release) pour la version et l’édition de Visual Studio que vous avez choisies.  Votre programme d’installation &mdash; ou pour être plus précis, un fichier de programme d’amorçage &mdash; correspondra ou sera semblable à l’un des éléments suivants :

| Édition                    | Télécharger                                                                                                                                                                                                                           |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019)     |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools  | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

Les autres programmes d’amorçage pris en charge incluent [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)et [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

::: moniker range=">=vs-2022"

>![!TIP]
> Les versions commercialisées de Visual Studio 2022 ne sont pas encore disponibles, les programmes d’amorçage ci-dessous concernent la version préliminaire de Visual Studio 2022.
Commencez par Télécharger le programme d’amorçage de Visual Studio 2022 à partir de la [page de téléchargements Visual Studio](https://aka.ms/vs2022preview).

| Édition                    | Télécharger                                                                             |
|----------------------------|--------------------------------------------------------------------------------------|
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/preview/bootstrapper/vs_enterprise.exe)     |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/17/preview/bootstrapper/vs_professional.exe) |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Si vous avez précédemment téléchargé un fichier de programme d’amorçage et que vous souhaitez vérifier la version, voici comment procéder. Dans Windows, ouvrez l’Explorateur de fichiers, cliquez avec le bouton droit sur le fichier du programme d’amorçage, choisissez **Propriétés**, cliquez sur l’onglet **Détails** , puis affichez le numéro de **version du produit** . Pour faire correspondre ce nombre à une version de Visual Studio, consultez [numéros de build et dates de publication de Visual Studio](visual-studio-build-numbers-and-release-dates.md).

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Si vous avez précédemment téléchargé un fichier de programme d’amorçage et que vous souhaitez vérifier la version, voici comment procéder. Dans Windows, ouvrez l’Explorateur de fichiers, cliquez avec le bouton droit sur le fichier du programme d’amorçage, choisissez **Propriétés**, cliquez sur l’onglet **Détails** , puis affichez le numéro de **version du produit** . Pour faire correspondre ce nombre à une version de Visual Studio, consultez mises en production de [Visual studio 2019](/visualstudio/releases/2019/history).

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Si vous avez précédemment téléchargé un fichier de programme d’amorçage et que vous souhaitez vérifier la version, voici comment procéder. Dans Windows, ouvrez l’Explorateur de fichiers, cliquez avec le bouton droit sur le fichier du programme d’amorçage, choisissez **Propriétés**, cliquez sur l’onglet **Détails** , puis affichez le numéro de **version du produit** . Pour faire correspondre ce nombre à une version de Visual Studio, consultez mises en production de [Visual studio 2022](/visualstudio/releases/2022/history).

::: moniker-end

## <a name="create-an-offline-installation-folder"></a>Créer un dossier d’installation hors connexion

Vous devez avoir une connexion Internet pour terminer cette étape.

Ouvrez une invite de commandes, accédez au répertoire dans lequel vous avez téléchargé le programme d’amorçage et utilisez les paramètres du programme d’amorçage tels que définis dans la page [utiliser les paramètres de ligne de commande pour installer Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) afin de créer et de gérer votre cache d’installation réseau. Des exemples courants de création de dispositions initiales sont illustrés ci-dessous et dans des [exemples de paramètres de ligne de commande pour l’installation de Visual Studio](../install/command-line-parameter-examples.md).  

   > [!IMPORTANT]
   > Une disposition initiale complète pour un seul paramètre régional de langue nécessite environ 35 Go d’espace disque pour Visual Studio Community et 42 Go pour Visual Studio Enterprise. Les [paramètres régionaux de langue](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) supplémentaires nécessitent environ deux Go chacun. Pour plus d’informations, consultez la section [personnaliser la disposition du réseau](#customize-the-network-layout) . N’oubliez pas que les mises à jour de mise en page ultérieures doivent également être stockées dans ce même emplacement réseau, de sorte que le contenu du répertoire de l’emplacement de la disposition du réseau peut devenir très volumineux au fil du temps.  

- Pour créer une disposition initiale de Visual Studio Enterprise avec tous les langages et toutes les fonctionnalités, exécutez :

  ```vs_enterprise.exe --layout c:\VSLayout```

- Pour créer une disposition initiale de Visual Studio Professional avec tous les langages et toutes les fonctionnalités, exécutez :

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Modifier le fichier response.json

Vous pouvez modifier le `response.json` fichier pour définir les valeurs par défaut qui sont utilisées lors de l’exécution du programme d’installation.  Par exemple, vous pouvez configurer le `response.json` fichier pour sélectionner un ensemble spécifique de charges de travail qui doivent être sélectionnées automatiquement. Vous pouvez également configurer l' `response.json` pour spécifier si le client doit uniquement recevoir les fichiers mis à jour à partir de l’emplacement de la disposition réseau. Pour plus d’informations, consultez [automatiser l’installation de Visual Studio avec un fichier réponse](../install/automated-installation-with-response-file.md). 

Si vous rencontrez un problème avec le programme d’amorçage de Visual Studio en levant une erreur lorsque vous le couplez avec un `response.json` fichier, consultez [résoudre les erreurs liées au réseau lorsque vous installez ou utilisez Visual Studio](../install/troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) pour plus d’informations.

## <a name="copy-the-layout-to-a-network-share"></a>Copier la disposition sur un partage réseau

Hébergez la disposition sur un partage réseau pour qu’elle puisse être exécutée à partir des ordinateurs clients.

L’exemple suivant utilise [`xcopy`](/windows-server/administration/windows-commands/xcopy/) . Vous pouvez également utiliser [`robocopy`](/windows-server/administration/windows-commands/robocopy/) , si vous le souhaitez.

::: moniker range="vs-2017"

Exemple :

```shell
xcopy /e c:\VSLayout \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```shell
xcopy /e c:\VSLayout \\server\products\VS2019
```

::: moniker-end

::: moniker range=">=vs-2022"

```shell
xcopy /e c:\VSLayout \\server\products\VS2022
```

::: moniker-end

> [!IMPORTANT]
> Pour éviter toute erreur, vérifiez que votre chemin de la disposition complet fait moins de 80 caractères.

## <a name="customize-the-network-layout"></a>Personnaliser la disposition réseau

Plusieurs options vous permettent de personnaliser votre disposition réseau. Vous pouvez créer une disposition partielle qui contient uniquement un ensemble spécifique de [paramètres régionaux de langue](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [charges de travail, composants et leurs dépendances recommandées ou facultatives](workload-and-component-ids.md). Cela peut s’avérer utile si vous savez que vous allez uniquement déployer un sous-ensemble de charges de travail sur les stations de travail clientes. Les paramètres de ligne de commande standard permettant de personnaliser la disposition incluent :

* `--add` pour spécifier des [ID de charge de travail ou de composant](workload-and-component-ids.md). <br>Si `--add` est utilisé, seuls les composants et les charges de travail spécifiés avec `--add` sont téléchargés.  Si `--add` n’est pas utilisé, l’ensemble des charges de travail et des composants est téléchargé.
* `--includeRecommended` pour inclure tous les composants recommandés pour les ID de charge de travail spécifiés
* `--includeOptional` pour inclure tous les composants recommandés et facultatifs pour les ID de charge de travail spécifiés.
* `--lang` pour spécifier les [paramètres régionaux de langue](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Voici quelques exemples montrant comment créer une disposition partielle personnalisée.

* Pour télécharger tous composants et les charges de travail dans une langue, exécutez :

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Pour télécharger tous composants et les charges de travail de plusieurs langues, exécutez :

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Pour télécharger une charge de travail pour toutes les langues, exécutez :

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Pour télécharger deux charges de travail et un composant facultatif dans trois langues, exécutez :

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Pour télécharger deux charges de travail et tous leurs composants recommandés :

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* Pour télécharger deux charges de travail et tous leurs composants recommandés et facultatifs, exécutez :

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

### <a name="save-your-layout-options"></a>Enregistrer vos options de disposition

Lorsque vous exécutez une commande de disposition, les options que vous spécifiez sont enregistrées (par exemple, les langues et les charges de travail). Les commandes de disposition suivantes englobent toutes les options précédentes.  Voici un exemple de disposition avec une charge de travail pour l’anglais uniquement :

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Lorsque vous souhaitez mettre à jour cette disposition vers une version plus récente, vous n’avez pas à spécifier de paramètres de ligne de commande supplémentaires. Les paramètres précédents sont enregistrés et utilisés par toutes les commandes de disposition suivantes dans ce dossier de disposition.  La commande suivante met à jour la disposition partielle existante.

```shell
vs_enterprise.exe --layout c:\VSLayout
```

Lorsque vous voulez ajouter une charge de travail supplémentaire, suivez cet exemple qui montre comment faire. Dans ce cas, nous allons ajouter une langue localisée et la charge de travail Azure.  À présent, Managed Desktop et Azure sont inclus dans cette disposition.  Les ressources de langue pour l’anglais et l’allemand sont comprises pour toutes ces charges de travail. La disposition est mise à jour avec la dernière version disponible.

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Si vous souhaitez passer d’une disposition existante à une disposition complète, utilisez l’option --all, comme indiqué dans l’exemple suivant.

```shell
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Effectuer un déploiement à partir d’une installation réseau

Les administrateurs peuvent déployer Visual Studio sur les stations de travail clientes dans le cadre d’un script d’installation. Les utilisateurs qui disposent de droits d’administrateur peuvent aussi exécuter le programme d’installation directement à partir du partage pour installer Visual Studio sur leur ordinateur.

* Les utilisateurs peuvent effectuer l’installation en exécutant la commande suivante : <br>

    ```shell
    \\server\products\VS\vs_enterprise.exe
    ```

* Les administrateurs peuvent effectuer l’installation en mode sans assistance en exécutant la commande suivante :

    ```shell
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Pour éviter toute erreur, vérifiez que votre chemin de la disposition complet fait moins de 80 caractères.

> [!TIP]
> Quand elle est exécutée dans le cadre d’un fichier de commandes, l’option `--wait` garantit que le processus `vs_enterprise.exe` attend que l’installation soit terminée avant de retourner un code de sortie.
>
> C’est utile si un administrateur d’entreprise souhaite effectuer d’autres opérations sur une installation terminée (par exemple, pour [appliquer une clé de produit sur une installation réussie](automatically-apply-product-keys-when-deploying-visual-studio.md)), alors qu’il doit attendre que l’installation se termine pour gérer le code de retour de cette installation.
>
> Si vous n’utilisez pas `--wait`, le processus `vs_enterprise.exe` s’arrête avant que l’installation soit terminée et retourne un code de sortie incorrect qui ne représente pas l’état de l’opération d’installation.
>

::: moniker range=">=vs-2019"
> [!IMPORTANT]
> Pour les installations hors connexion, si vous recevez un message d’erreur indiquant « un produit correspondant aux paramètres suivants est introuvable », vérifiez que vous utilisez le `--noweb` commutateur avec la version 16.3.5 ou ultérieure.
>
::: moniker-end

Lorsque vous installez à partir d’une disposition, le contenu qui est installé est acquis à partir de la disposition. Toutefois, si vous sélectionnez un composant qui ne se trouve pas dans la disposition, celui-ci est téléchargé à partir d’Internet.  Si vous voulez empêcher le programme d’installation de Visual Studio de télécharger le contenu manquant dans la disposition, utilisez l’option `--noWeb`. Si `--noWeb` est utilisé et qu’un contenu à installer est absent de la disposition, l’installation échoue.

> [!TIP]
> Si vous souhaitez installer à partir d’une source hors connexion sur un ordinateur non connecté à Internet, spécifiez les `--noWeb` `--noUpdateInstaller` options et. La première empêche le téléchargement de charges de travail mises à jour, de composants, etc. Ce dernier empêche le programme d’installation de se mettre à jour automatiquement à partir du Web.

> [!IMPORTANT]
> L' `--noWeb` option n’empêche pas le programme d’installation de Visual Studio sur un ordinateur connecté à Internet de vérifier la présence de mises à jour. Pour plus d’informations, consultez la page [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md).

### <a name="error-codes"></a>Codes d’erreur

Si vous avez utilisé le paramètre `--wait`, en fonction du résultat de l’opération, la variable d’environnement `%ERRORLEVEL%` a l’une des valeurs suivantes :

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Mettre à jour une disposition d’installation réseau

Quand les mises à jour de produit deviennent disponibles, vous avez la possibilité de [mettre à jour la disposition d’installation réseau](update-a-network-installation-of-visual-studio.md) pour intégrer les packages mis à jour.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Comment créer une disposition pour une version antérieure de Visual Studio

Tout d’abord, vous devez comprendre qu’il existe deux types d’amorçages Visual Studio : un qui peut être caractérisé par les mots « latest », « Current », « persistent » et « Tip », et l’autre qui signifie essentiellement « Fixed version » (version fixe). Les deux types de fichiers de programme d’amorçage ont exactement le même nom, et la meilleure façon de distinguer le type est de prêter attention à l’emplacement à partir duquel vous l’avez obtenu. Les programmes d’amorçage Visual Studio disponibles sur la [page téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) sont considérés comme des programmes d’amorçage Visual Studio persistants et ils installent (ou mettent à jour) la dernière version disponible dans le canal au moment de l’exécution du programme d’amorçage. Les programmes d’amorçage Visual Studio disponibles sur la page Visual Studio [2019 releases](/visualstudio/releases/2019/history) visual [Studio 2022](/visualstudio/releases/2022/history)  , ou ceux qui sont incorporés à l’intérieur de la mise à jour de l’administrateur dans le catalogue Microsoft Update, installent une version fixe particulière du produit.

Par conséquent, si vous téléchargez aujourd’hui un programme d’amorçage Visual Studio persistant et que vous l’exécutez six mois plus tard, il installe la version de Visual Studio qui est à jour au moment de l’exécution du programme d’amorçage. Il est conçu pour toujours installer les derniers bits et vous tenir à jour.

Si vous téléchargez un programme d’amorçage à liaison fixe, ou si vous exécutez une mise à jour d’administrateur que vous avez téléchargée à partir du catalogue Microsoft, il installera toujours une version particulière du produit, quel que soit le moment de son exécution.

Enfin, vous pouvez créer une disposition réseau à l’aide de l’un de ces programmes d’amorçage, et la version qui sera créée dans la disposition dépend du programme d’amorçage que vous utilisez, par exemple, il s’agit d’une version fixe ou actuelle. Vous pouvez ensuite mettre à jour la disposition du réseau à l’aide de n’importe quel programme d’amorçage ultérieur, ou vous pouvez également utiliser le package de mise à jour administrateur à partir du catalogue de Microsoft Update. Quelle que soit la façon dont vous mettez à jour la disposition, la disposition mise à jour résultante sera un cache de package qui contient une version particulière du produit, et il se comportera alors comme un programme d’amorçage de lien fixe. Ainsi, chaque fois que le client est installé à partir de la disposition, le client installe la version spécifique de Visual Studio qui existe dans la mise en page (même si une version plus récente peut exister en ligne).

### <a name="how-to-get-support-for-your-offline-installer"></a>Comment obtenir de l’assistance pour votre programme d’installation hors connexion

Si vous rencontrez un problème avec votre installation hors connexion, nous voulons le savoir. Le meilleur moyen de nous en faire part est d’utiliser l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio.md). Lorsque vous utilisez cet outil, vous pouvez nous envoyer la télémétrie et des journaux, dont nous avons besoin pour nous aider à diagnostiquer et à résoudre le problème.

Nous offrons également une option de support par [**chat sur les installations**](https://visualstudio.microsoft.com/vs/support/#talktous) (en anglais uniquement) pour les problèmes liés à l’installation.

D’autres options de support sont également à votre disposition. Pour obtenir la liste, consultez notre page [Commentaires](../ide/feedback-options.md).

## <a name="see-also"></a>Voir aussi

- [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
- [Mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Résoudre les erreurs liées au réseau lorsque vous installez ou utilisez Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
- [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md)
- [Maintenance et cycle de vie des produits Visual Studio](/visualstudio/releases/2019/servicing/)
- [Mettre à jour Visual Studio tout en étant sur une ligne de base de maintenance](update-servicing-baseline.md)
- [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
- [Installer les certificats nécessaires à l’installation hors connexion de Visual Studio](install-certificates-for-visual-studio-offline.md)
