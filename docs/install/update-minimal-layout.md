---
title: Mettre à jour Visual Studio avec une disposition hors connexion minimale
description: Découvrez comment mettre à jour Visual Studio à l’aide d’une disposition hors connexion minimale.
ms.date: 05/18/2021
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9971007ed38a1f09aa28145ead468f6e5383eeae
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973605"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>Mettre à jour Visual Studio avec une disposition hors connexion minimale

Pour les ordinateurs qui ne sont pas connectés à Internet, la création d’une disposition minimale est le moyen le plus simple et le plus rapide de mettre à jour vos instances de Visual Studio hors connexion.

L’outil Configuration minimale génère une disposition adaptée spécifiquement aux besoins de votre équipe. Les administrateurs d’entreprise peuvent utiliser cet outil pour créer une ou plusieurs mises à jour pour la plupart des versions de Visual Studio 2017 et 2019. Contrairement à une mise en page complète de Visual Studio, une disposition minimale contient uniquement les packages mis à jour. par conséquent, elle est toujours plus petite et plus rapide à générer et à déployer. Vous pouvez réduire davantage la taille de la disposition des mises à jour en spécifiant uniquement les langues, les charges de travail et les composants souhaités.

## <a name="how-to-generate-a-minimal-layout"></a>Comment générer une disposition minimale

> [!IMPORTANT]
> Ces instructions supposent que vous avez déjà créé et utilisé des dispositions. Pour plus d’informations sur la façon de procéder, consultez la page [mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md) .
>
> Pour mieux comprendre le cycle de vie de Visual Studio, consultez la page relative au [cycle de vie et à la maintenance du produit Visual Studio](/visualstudio/releases/2019/servicing) .
>

Cet outil crée des dispositions de mise à jour pour Visual Studio 2017 (15,9) et les versions ultérieures. La disposition peut être déployée sur des ordinateurs réseau/hors connexion pour mettre à jour des instances de Visual Studio. Lors de la création d’une [disposition normale](update-a-network-installation-of-visual-studio.md), tous les packages de cette version particulière sont téléchargés. La création d’une disposition normale est requise pour la réparation, la désinstallation et d’autres opérations standard sur les instances de Visual Studio. La disposition minimale télécharge uniquement les packages mis à jour. il est donc plus petit et plus facile à copier sur des ordinateurs hors connexion.

### <a name="installing-the-minimal-layout-tool"></a>Installation de l’outil de disposition minimal

 1. Tout d’abord, téléchargez l’outil de disposition minimal situé [ici](https://aka.ms/vs/installer/minimallayout). Veillez à choisir **Enregistrer** lorsque vous y êtes invité, puis sélectionnez **exécuter**.

     ![Enregistrer l’outil de disposition minimal](media/save-minimal-layout.png)

 2. Ensuite, acceptez l’invite du contrôle de compte d’utilisateur en cliquant sur **Oui**.

     ![Accepter le contrôle de compte d’utilisateur](media/accept-user-account-control.png)

 3. L’outil de disposition minimale sera installé sur `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` .

### <a name="how-to-use-the-minimal-layout-tool"></a>Comment utiliser l’outil de disposition minimal

`MinimalLayout.exe` utilise les commandes et options suivantes pour générer la disposition. Au moins une commande est requise pour exécuter l’outil. Voici comment exécuter l’outil :

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Commandes
* **Aperçu**: utilisez cette commande pour afficher un aperçu du nombre de packages à télécharger et de l’espace total utilisé pour créer cette disposition.
* **Générer**: utilisez cette commande pour générer la disposition minimale pour la mise à jour de Visual Studio.
* **Régénérer**: utilisez cette commande pour régénérer une disposition à l’aide d’un fichier réponse de disposition minimale existant. Chaque disposition minimale produit un `MinimalLayout.json` fichier réponse qui contient les paramètres d’entrée de disposition minimale d’origine. Vous pouvez utiliser la commande **régénérer** et un `MinimalLayout.json` fichier réponse pour régénérer la disposition minimale. Cela est utile si vous souhaitez créer une disposition minimale pour une nouvelle mise à jour de Visual Studio en fonction du fichier de réponse de la disposition minimale précédente.

   Pour cette commande, un `MinimalLayout.json` chemin d’accès de fichier d’une disposition déjà générée est requis.

    ```cmd
    MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
    ```

* **Vérifier**: utilisez cette commande pour déterminer si le dossier de disposition est endommagé.
* **Correctif**: utilisez cette commande pour corriger un dossier de disposition endommagé, y compris pour remplacer tous les packages manquants du dossier de disposition.

::: moniker range="vs-2019"

#### <a name="options"></a>Options

|Options    |Description    |Obligatoire ou facultatif |Exemple |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; dir&gt; |Spécifie un répertoire dans lequel créer une disposition hors connexion minimale.       |Obligatoire        |--targetLocation c:\VSLayout\ |
|--version de paramètre &lt;&gt;|La disposition hors connexion minimale sera générée à partir de cette version.   |Obligatoire|--Paramètre 16.4.0 |
|--version de targetVersion &lt;&gt;|La disposition en mode hors connexion minimale sera générée jusqu’à cette version, y compris.|Obligatoire|--targetVersion 16.4.4|
|--langues    |Spécifie les langues à inclure dans la disposition hors connexion minimale. Vous pouvez spécifier plusieurs valeurs, séparées par des espaces.    |Obligatoire    |--langues en-US fr-FR |
|--productIds &lt; un ou plusieurs ID de produit&gt;    |ID du ou des produits à partir desquels la disposition hors connexion minimale sera générée, en les séparant par des virgules. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|Obligatoire|--productIds Microsoft. VisualStudio. Product. entreprise, Microsoft. VisualStudio. Product. Professional |
|--filePath    |Chemin d’accès au fichier de l' MinimalLayout.jsdans un fichier à partir d’une disposition déjà créée. Cette option est utilisée uniquement avec la commande régénérer.     |Requis pour la commande régénérer    |--filePath C:\VSLayout\minimalLayout.jssur <br><br> **Notez que la commande régénérer ne prend que le chemin d’une option.** |
|--Ajouter &lt; un ou plusieurs ID de charge de travail ou de composant&gt;    |Spécifie un ou plusieurs ID de charge de travail ou de composant à ajouter. Des composants supplémentaires peuvent être ajoutés globalement à l’aide de--includeRecommended et/ou <br> –-includeOptional. Plusieurs charges de travail ou ID de composant peuvent être spécifiés, séparés par un espace.    |Facultatif    |--Ajoutez le composant Microsoft. VisualStudio. Workload. ManagedDesktop Microsoft. VisualStudio. Workload. NetWeb. GitHub. VisualStudio |
|--includeRecommended    |Inclut les composants recommandés pour toutes les charges de travail installées, mais pas les composants facultatifs.    |Facultatif    |Pour une charge de travail spécifique : <br> --Ajoutez Microsoft. VisualStudio. Workload. ManagedDesktop ; includeRecommended <br><br> À appliquer à toutes les charges de travail :--includeRecommended |
|--includeOptional |Inclut les composants facultatifs pour toutes les charges de travail installées, y compris les composants recommandés.    |Facultatif    |Pour une charge de travail spécifique : <br>--Ajoutez Microsoft. VisualStudio. Workload. ManagedDesktop ; includeOptional <br><br> À appliquer à toutes les charges de travail :--includeOptional |

::: moniker-end

::: moniker range="vs-2017"

#### <a name="options"></a>Options

|Options    |Description    |Obligatoire ou facultatif |Exemple |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; dir&gt; |Spécifie un répertoire dans lequel créer une disposition hors connexion minimale.       |Obligatoire        |--targetLocation c:\VSLayout\ |
|--version de paramètre &lt;&gt;|La disposition hors connexion minimale sera générée à partir de cette version.   |Obligatoire|--Paramètre 15.0.0 |
|--version de targetVersion &lt;&gt;|La disposition en mode hors connexion minimale sera générée jusqu’à cette version, y compris.|Obligatoire|--targetVersion 15.9.31|
|--langues    |Spécifie les langues à inclure dans la disposition hors connexion minimale. Vous pouvez spécifier plusieurs valeurs, séparées par des espaces.    |Obligatoire    |--langues en-US fr-FR |
|--productIds &lt; un ou plusieurs ID de produit&gt;    |ID du ou des produits à partir desquels la disposition hors connexion minimale sera générée, en les séparant par des virgules. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|Obligatoire|--productIds Microsoft. VisualStudio. Product. entreprise, Microsoft. VisualStudio. Product. Professional |
|--filePath    |Chemin d’accès au fichier de l' MinimalLayout.jsdans un fichier à partir d’une disposition déjà créée. Cette option est utilisée uniquement avec la commande régénérer.     |Requis pour la commande régénérer    |--filePath C:\VSLayout\minimalLayout.jssur <br><br> **Notez que la commande régénérer ne prend que le chemin d’une option.** |
|--Ajouter &lt; un ou plusieurs ID de charge de travail ou de composant&gt;    |Spécifie un ou plusieurs ID de charge de travail ou de composant à ajouter. Des composants supplémentaires peuvent être ajoutés globalement à l’aide de--includeRecommended et/ou <br> –-includeOptional. Plusieurs charges de travail ou ID de composant peuvent être spécifiés, séparés par un espace.    |Facultatif    |--Ajoutez le composant Microsoft. VisualStudio. Workload. ManagedDesktop Microsoft. VisualStudio. Workload. NetWeb. GitHub. VisualStudio |
|--includeRecommended    |Inclut les composants recommandés pour toutes les charges de travail installées, mais pas les composants facultatifs.    |Facultatif    |Pour une charge de travail spécifique : <br> --Ajoutez Microsoft. VisualStudio. Workload. ManagedDesktop ; includeRecommended <br><br> À appliquer à toutes les charges de travail :--includeRecommended |
|--includeOptional |Inclut les composants facultatifs pour toutes les charges de travail installées, y compris les composants recommandés.    |Facultatif    |Pour une charge de travail spécifique : <br>--Ajoutez Microsoft. VisualStudio. Workload. ManagedDesktop ; includeOptional <br><br> À appliquer à toutes les charges de travail :--includeOptional |

::: moniker-end

### <a name="generating-a-minimal-layout"></a>Génération d’une disposition minimale

> [!IMPORTANT]
>  Ces instructions supposent que vous avez déjà créé une disposition d’installation réseau. Pour plus d’informations sur la façon de procéder, consultez la page [créer une installation réseau de Visual Studio](create-a-network-installation-of-visual-studio.md) .

Créez une disposition minimale à l’aide de la commande **générer** pour la plage de versions spécifiée. Vous devez également connaître le productId, les langues et toutes les charges de travail spécifiques requises. Cette disposition minimale met à jour toutes les instances de Visual Studio à partir de la version de base jusqu’à la version cible, y compris.

Avant de créer la disposition, vous pouvez déterminer la taille totale du téléchargement et le nombre de packages inclus à l’aide de la commande **Aperçu** . Cette commande utilise les mêmes options que la commande **generate** , et les détails sont écrits dans la console.

Passons en revue quelques exemples illustrant comment prévisualiser, générer et régénérer une disposition minimale :

::: moniker range="vs-2019"

- Tout d’abord, voici un exemple de la façon d’afficher un aperçu d’une disposition pour Visual Studio Enterprise versions 16.4.0 vers 16.4.4 pour l’anglais uniquement.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- Voici comment générer cette même disposition avec une charge de travail.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- Et voici comment régénérer une disposition hors connexion minimale à l’aide d’un fichier réponse existant.

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Voici quelques autres exemples d’utilisation de la commande **generate** :

- Voici comment ajouter une charge de travail supplémentaire et inclure uniquement les packages recommandés.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Enfin, voici comment inclure plusieurs langues dans votre disposition minimale.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

::: moniker range="vs-2017"

- Tout d’abord, voici un exemple de la façon d’afficher un aperçu d’une disposition pour Visual Studio Enterprise versions 15.0.0 vers 15.9.31 pour l’anglais uniquement.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
    ```

- Voici comment générer cette même disposition avec une charge de travail.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- Et voici comment régénérer une disposition hors connexion minimale à l’aide d’un fichier réponse existant.

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Voici quelques autres exemples d’utilisation de la commande **generate** :

- Voici comment ajouter une charge de travail supplémentaire et inclure uniquement les packages recommandés.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Enfin, voici comment inclure plusieurs langues dans votre disposition minimale.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>Comment conserver une disposition minimale

Utilisez les commandes **verify** et **Fix** pour conserver votre disposition minimale après sa création. La commande **verify** détermine s’il existe des packages endommagés ou manquants dans la disposition minimale. Si vous rencontrez des problèmes après avoir exécuté la commande **verify** , utilisez la commande **Fix** pour corriger les packages manquants ou endommagés.

- Voici comment vérifier si une disposition présente des packages manquants ou endommagés :

    ```cmd
    MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
    ```

- Et voici comment corriger cette disposition :

    ```cmd
    MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
    ```

>[!NOTE]
> Cette disposition ne peut pas être utilisée pour réparer une installation de Visual Studio. Pour réparer une instance existante de Visual Studio, consultez [réparer Visual Studio](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Comment utiliser une disposition hors connexion minimale pour mettre à jour une installation existante de Visual Studio

Après avoir généré une disposition minimale, vous pouvez copier l’intégralité du dossier de disposition minimal sur un ordinateur client. Cette condition est requise si l’ordinateur n’a pas accès au dossier de disposition minimale à son emplacement d’origine.

Accédez au dossier et identifiez le nom de l’application du programme d’amorçage. Le nom de l’application du programme d’amorçage dépend de la valeur ProductId spécifiée lors de la génération de la disposition minimale. Reportez-vous au tableau ci-dessous pour obtenir des exemples courants.

|Valeur ProductId    |Nom de l'application|
|:-----------|:------------|
|Microsoft.VisualStudio.Product.Enterprise    |vs_enterprise.exe|
|Microsoft.VisualStudio.Product.Professional    |vs_professional.exe|
|Microsoft.VisualStudio.Product.BuildTools    |vs_buildtools.exe|

La mise à jour est appliquée à une instance de Visual Studio en deux étapes. Commencez par mettre à jour le Visual Studio Installer, puis mettez à jour Visual Studio.

1. **Mettre à jour le Visual Studio Installer**

    Exécutez la commande suivante, en remplaçant `vs_enterprise.exe`  le cas échéant par le nom correct de l’application du programme d’amorçage.

    ```cmd
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Mettre à jour l’application Visual Studio**

    Pour mettre à jour Visual Studio, vous devez spécifier le installPath de l’instance de Visual Studio que vous souhaitez mettre à jour. Si plusieurs instances de Visual Studio sont installées, chacune d’elles doit être mise à jour séparément. Nous vous recommandons vivement de spécifier l' `–noWeb` option avec la commande de mise à jour pour empêcher l’installation de composants qui ne sont pas dans la disposition minimale. Cela vous empêche de quitter Visual Studio dans un état inutilisable.

    Exécutez la commande suivante, en substituant le paramètre de ligne de commande installPath de manière appropriée. Veillez à utiliser également le nom correct de l’application du programme d’amorçage.

    ```cmd
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Outils de détection et de gestion des instances de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Guide pratique pour définir des paramètres dans un fichier réponse](automated-installation-with-response-file.md)
* [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md)
* [Maintenance et cycle de vie des produits Visual Studio](/visualstudio/releases/2019/servicing/)
