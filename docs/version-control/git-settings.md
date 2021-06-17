---
title: Paramètres git dans Visual Studio
titleSuffix: ''
description: Découvrez comment Visual Studio utilise les fichiers. gitconfig et les paramètres git pour gérer vos préférences
ms.date: 06/08/2021
ms.topic: conceptual
ms.author: prnadago
author: prnadago
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.manager: jmartens
monikerRange: '>=vs-2019'
ms.openlocfilehash: f8dd9781833706a73b82a71236d42cc71c9fb9ec
ms.sourcegitcommit: 113b7df611583307d3965984233a33355d6b0318
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2021
ms.locfileid: "112126685"
---
# <a name="git-settings-and-preferences-in-visual-studio"></a>Paramètres et préférences git dans Visual Studio

Dans Visual Studio, vous pouvez configurer et afficher les paramètres et préférences git courants, tels que votre nom et votre adresse de messagerie, vos outils de comparaison et de fusion préférés, et bien plus encore. Ces paramètres et préférences peuvent être affichés et configurés dans la **boîte de dialogue Options** , sur la page des **paramètres globaux git** (s’applique à tous vos référentiels) ou sur la page des **paramètres du référentiel git** (s’applique au référentiel actuel).

Vous pouvez configurer deux types de paramètres :

- [Paramètres git](#git-settings) -les paramètres de cette section correspondent aux paramètres git enregistrés dans les fichiers de configuration git. Ces paramètres peuvent être affichés et modifiés dans Visual Studio, mais ils sont gérés par des fichiers de configuration git.
- [Paramètres Visual Studio](#visual-studio-settings) -les paramètres de cette section configurent les paramètres et les préférences liés à git qui sont gérés par Visual Studio.

## <a name="how-to-configure-settings"></a>Procédure de configuration des paramètres

1. Pour configurer les paramètres git dans Visual Studio, choisissez **paramètres** dans le menu git de niveau supérieur.

   :::image type="content" source="media/git-menu-settings.png" alt-text="Le menu git avec une légende à la commande paramètres.":::

2. Choisissez paramètres **globaux git** ou **paramètres de référentiel git** pour afficher et configurer les paramètres de niveau global ou de référentiel.

   :::image type="content" source="media/source-control-settings.png" alt-text="Volet de navigation de la boîte de dialogue Options avec une légende pour les paramètres git.":::

3. Vous pouvez configurer plusieurs paramètres git courants, comme décrit dans les sections suivantes de cet article. Après avoir configuré les paramètres de votre choix, sélectionnez **OK** pour enregistrer les paramètres mis à jour.

   :::image type="content" source="media/ok-button.png" alt-text="Zone d’affichage de la boîte de dialogue Options avec une légende pour le bouton OK.":::

## <a name="git-settings"></a>Paramètres git

Vous pouvez également configurer et vérifier certains des paramètres de configuration git les plus courants. Vous pouvez afficher et modifier les paramètres suivants dans Visual Studio, même s’ils sont gérés par des fichiers de configuration git.

- [Nom et e-mail](#name-and-email)
- [Nettoyer les branches distantes pendant l’extraction](#prune-remote-branches-during-fetch)
- [Rebaser la branche locale lors de l’extraction](#rebase-local-branch-when-pulling)
- [Fournisseur réseau de chiffrement](#cryptographic-network-provider)
- [Assistance des informations d’identification](#credential-helper)
- [Outils de fusion de & diff](#diff--merge-tools)
- [Fichiers git](#git-files)
- [Dépôts distants](#remotes)
- [Autres paramètres](#other-settings)

>[!NOTE]
>Les paramètres git configurés dans les **paramètres globaux** de Visual Studio correspondent aux paramètres du fichier de configuration spécifique à l’utilisateur de git, et les paramètres dans les **paramètres du référentiel** correspondent aux paramètres dans le fichier de configuration spécifique au référentiel. Pour plus d’informations sur la configuration de git, consultez le [chapitre sur la personnalisation de](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration)git, la documentation de la configuration [git](https://git-scm.com/docs/git-config)et la [référence à la Git Pro sur les fichiers de configuration](https://git-scm.com/docs/git-config#FILES). Pour configurer les paramètres git non exposés dans Visual Studio, utilisez la `git config` commande pour écrire une valeur dans vos fichiers de configuration : `git config [--local|--global|--system] section.key value` .

### <a name="name-and-email"></a>Nom et e-mail

Le nom et l’adresse de messagerie que vous fournissez seront utilisés comme informations de validation pour toute validation que vous effectuez. Ce paramètre est disponible à la fois dans les étendues globales et de dépôt, et correspond aux `git config` paramètres [user.name](https://git-scm.com/docs/git-config#Documentation/git-config.txt-username) et [User.email](https://git-scm.com/docs/git-config#Documentation/git-config.txt-useremail) .

1. Dans le menu git, accédez à **paramètres**. Pour définir votre nom d’utilisateur et votre adresse de messagerie au niveau global, accédez à **paramètres globaux git**. pour définir votre nom d’utilisateur et votre adresse de messagerie au niveau du référentiel, accédez à **git référentiel Settings**.

2. Indiquez votre nom d’utilisateur et votre adresse de messagerie, puis choisissez **OK** pour les enregistrer. 

   :::image type="content" source="media/user-email-setting.png" alt-text="Volet des paramètres globaux git dans la boîte de dialogue Options avec une légende pour le nom d’utilisateur d’un e-mail.":::

### <a name="prune-remote-branches-during-fetch"></a>Nettoyer les branches distantes pendant l’extraction

Le nettoyage supprime les branches de suivi à distance qui n’existent plus sur la télécommande et vous aide à maintenir la liste des branches nette et à jour. Ce paramètre est disponible à la fois dans les étendues globales et de dépôt, et correspond au `git config` paramètre [Fetch. prune](https://git-scm.com/docs/git-config#Documentation/git-config.txt-fetchprune) .

Nous vous recommandons d’affecter la **valeur true** à cette option au niveau global. Les paramètres valides sont les suivants :

- True (recommandé)
- False
- Unset (valeur par défaut)

1. Dans le menu git, accédez à **paramètres**. Accédez à **paramètres globaux git** pour configurer cette option au niveau global. Accédez à **paramètres du référentiel git** pour configurer cette option au niveau référentiel.

2. Définissez **nettoyer les branches distantes pendant l’extraction** sur **true** (recommandé). Sélectionnez **OK** pour enregistrer.

:::image type="content" source="media/prune-setting.png" alt-text="Capture d’écran montrant « nettoyer les branches distantes pendant l’extraction » en surbrillance et avec « true » sélectionné dans la liste déroulante.":::    

### <a name="rebase-local-branch-when-pulling"></a>Rebaser la branche locale lors de l’extraction

La relocalisation met de côté les modifications apportées par les validations dans la branche active qui ne sont pas dans la branche en amont, réinitialise la branche actuelle à la branche en amont, puis applique les modifications qui ont été mises de côté. Ce paramètre est disponible à la fois dans les étendues globales et de dépôt, et correspond au `git config` paramètre [pull. rebase](https://git-scm.com/docs/git-config#Documentation/git-config.txt-pullrebase) . Les paramètres valides sont les suivants :

- True : rebaser la branche active en plus de la branche amont après l’extraction.
- False : fusionner la branche actuelle dans la branche en amont.
- Unset (valeur par défaut) : sauf spécification contraire dans d’autres fichiers de configuration, fusion de la branche active dans la branche en amont.
- Interactive : rebase en mode interactif.
- Conserver : rebase sans aplatir les validations de fusion créées localement.

1. Dans le menu git, accédez à **paramètres**. Accédez à **paramètres globaux git** pour configurer cette option au niveau global. Accédez à **paramètres du référentiel git** pour configurer cette option au niveau référentiel.

2. Définissez **rebaser la branche locale lors** de l’extraction jusqu’au paramètre souhaité, puis sélectionnez **OK** pour enregistrer.

    :::image type="content" source="media/rebase-setting.png" alt-text="Capture d’écran qui indique « rebaser la branche locale quand l’extraction est sélectionnée et «true » dans la liste déroulante.":::

Il n’est pas possible de configurer `pull.rebase` en mode **interactif** dans Visual Studio. Visual Studio ne dispose pas d’une prise en charge interactive de rebase.
Pour configurer `pull.rebase` pour utiliser le mode interactif, utilisez la ligne de commande.

### <a name="cryptographic-network-provider"></a>Fournisseur réseau de chiffrement

Le fournisseur de réseau de chiffrement est un paramètre de configuration git au niveau de l’étendue globale qui configure le serveur principal TLS/SSL à utiliser au moment de l’exécution et qui correspond au `git config` paramètre [http. sslBackend](https://git-scm.com/docs/git-config#Documentation/git-config.txt-httpsslBackend) . Les valeurs sont les suivantes :

- OpenSSL : utilisez [OpenSSL](https://www.openssl.org/) pour les protocoles TLS et SSL.
- Canal sécurisé : utilisez le [canal sécurisé (SChannel)](/windows/win32/secauthn/secure-channel) pour les protocoles TLS et SSL. Schannel est la solution Windows native, qui accède au magasin d’informations d’identification Windows, ce qui permet de gérer la gestion des certificats à l’ensemble de l’entreprise.
- Unset (valeur par défaut) : si ce paramètre est désactivé, OpenSSL est la valeur par défaut.

1. Dans le menu git, accédez à **paramètres**. Accédez à **paramètres globaux git** pour configurer ce paramètre.

2. Définissez **fournisseur de réseau de chiffrement** sur la valeur souhaitée, puis sélectionnez **OK** pour enregistrer.

   :::image type="content" source="media/network-provider-setting.png" alt-text="Capture d’écran montrant « fournisseur réseau de chiffrement » en surbrillance avec « OpenSSL » sélectionné dans la liste déroulante.":::

### <a name="credential-helper"></a>Assistance des informations d’identification

Lorsque Visual Studio effectue une opération git distante, le point de terminaison distant peut rejeter la demande, car elle nécessite des informations d’identification à fournir avec la requête. À ce moment-là, git appelle une application d’assistance des informations d’identification, qui retournera les informations d’identification nécessaires pour effectuer l’opération, puis retentera la demande. Le programme d’assistance des informations d’identification utilisé correspond au `git config` paramètre [Credential. Helper](https://git-scm.com/docs/gitcredentials) . Elle est disponible dans l’étendue globale avec les valeurs suivantes :

- GCM pour Windows : utilisez [git Credential Manager pour Windows](https://github.com/microsoft/Git-Credential-Manager-for-Windows) comme programme d’assistance.
- GCM Core : utilisez [git Credential Manager Core](https://github.com/microsoft/Git-Credential-Manager-Core) comme programme d’assistance.
- Unset (valeur par défaut) : si ce paramètre est désactivé, le programme d’assistance des informations d’identification défini dans la configuration système est utilisé. À partir de Git pour Windows 2,29, le programme d’assistance des informations d’identification par défaut est GCM Core.

1. Dans le menu git, accédez à **paramètres**. Accédez à **paramètres globaux git** pour configurer ce paramètre.

2. Définissez **assistance des informations d’identification** à la valeur souhaitée, puis sélectionnez **OK** pour enregistrer.

:::image type="content" source="media/credential-helper-setting.png" alt-text="Capture d’écran montrant le paramètre d’assistance des informations d’identification dans la boîte de dialogue Options.":::

### <a name="diff--merge-tools"></a>Outils de fusion de & diff

Git affiche les différences et les conflits de fusion dans vos outils préférés. Les paramètres de cette section correspondent aux paramètres `git config` [diff. Tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) et [Merge. Tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool) . Vous pouvez configurer Git pour utiliser Visual Studio comme outil de fusion ou de comparaison dans les paramètres **globaux git** et les **paramètres de dépôt git** en sélectionnant **utiliser Visual Studio**. Pour configurer d’autres outils de comparaison et de fusion, utilisez `git config` avec le commutateur [diff. Tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) ou [Merge. Tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool) .

:::image type="content" source="media/tools-setting.png" alt-text="Capture d’écran qui montre la section permettant de définir l’outil diff et l’outil de fusion par défaut dans la boîte de dialogue Options.":::

### <a name="git-files"></a>Fichiers git

Vous pouvez utiliser la section **fichiers git** dans l’étendue des **paramètres du référentiel git** pour afficher et modifier les fichiers [gitignore](https://git-scm.com/docs/gitignore) et [gitattributes](https://git-scm.com/docs/gitattributes) de votre référentiel.

:::image type="content" source="media/git-files-setting.png" alt-text="Capture d’écran qui montre la section permettant d’afficher et de modifier les fichiers d’attributs et d’ignore dans votre référentiel.":::

### <a name="remotes"></a>Dépôts distants

Vous pouvez utiliser le volet **distants** sous **paramètres du référentiel git** pour configurer les distants de votre référentiel. Ce paramètre correspond à la commande [à distance git](https://git-scm.com/docs/git-remote) et vous permet d’ajouter, de modifier ou de supprimer des paramètres distants.

:::image type="content" source="media/remotes-settings.png" alt-text="Capture d’écran montrant le volet distants git dans la boîte de dialogue Options.":::

### <a name="other-settings"></a>Autres paramètres

Pour afficher tous les autres paramètres de configuration git, vous pouvez ouvrir et afficher les fichiers de configuration eux-mêmes, ou vous pouvez exécuter `git config --list` pour afficher les paramètres.

## <a name="visual-studio-settings"></a>Paramètres Visual Studio

Les paramètres suivants gèrent les préférences git dans Visual Studio et sont gérés par Visual Studio au lieu des fichiers de configuration git. Tous les paramètres de cette section sont configurés dans la page des **paramètres globaux git** .

- [Emplacement par défaut](#default-location)
- [Fermer les solutions ouvertes qui ne sont pas sous git lors de l’ouverture d’un référentiel](#close-open-solutions-not-under-git-when-opening-a-repository)
- [Activer le téléchargement d’images créées à partir de sources tierces](#enable-download-of-author-images-from-third-party-sources)
- [Valider les modifications après la fusion par défaut](#commit-changes-after-merge-by-default)
- [Activer Push--force](#enable-push---force-with-lease)
- [Ouvrir le dossier dans Explorateur de solutions lors de l’ouverture d’un référentiel git](#open-folder-in-solution-explorer-when-opening-a-git-repository)
- [Charger automatiquement la solution lors de l’ouverture d’un référentiel git](#automatically-load-the-solution-when-opening-a-git-repository)
- [Extraire automatiquement les branches avec un double-clic ou la touche entrée](#automatically-check-out-branches-with-double-click-or-the-enter-key)

### <a name="default-location"></a>Localisation par défaut

L' **emplacement par défaut** configure le dossier par défaut dans lequel les dépôts sont clonés.

:::image type="content" source="media/default-location-setting.png" alt-text="Capture d’écran montrant le champ emplacement par défaut dans la boîte de dialogue Options.":::

### <a name="close-open-solutions-not-under-git-when-opening-a-repository"></a>Fermer les solutions ouvertes qui ne sont pas sous git lors de l’ouverture d’un référentiel

Par défaut, Visual Studio ferme toutes les solutions ou tous les dossiers ouverts lorsque vous basculez vers un autre référentiel. Dans ce cas, il peut également charger la solution ou le dossier du nouveau référentiel en fonction de si vous choisissez d’ouvrir le [dossier dans Explorateur de solutions lors de l’ouverture d’un dépôt git](#open-folder-in-solution-explorer-when-opening-a-git-repository) et de [charger automatiquement la solution lors de l’ouverture d’un référentiel git](#automatically-load-the-solution-when-opening-a-git-repository). Cela maintient la cohérence entre le code ouvert et le référentiel ouvert. Toutefois, si votre solution n’est pas dans la même racine de dossier que votre référentiel, vous souhaiterez peut-être laisser la solution ouverte lorsque vous basculez vers son référentiel. Vous pouvez le faire avec ce paramètre. Les valeurs sont les suivantes :

- Oui : lorsqu’un dépôt est ouvert, la solution actuellement ouverte est toujours fermée
- Non : lorsqu’un dépôt est ouvert, Visual Studio vérifie si la solution actuelle est sous git. Si ce n’est pas le cas, la solution reste ouverte.
- Toujours demander (valeur par défaut) : quand cette option est définie, vous pouvez faire un choix dans une boîte de dialogue par dépôt ouvert, que vous souhaitiez laisser la solution actuelle ouverte ou fermée.

:::image type="content" source="media/close-sln-setting.png" alt-text="Capture d’écran montrant le paramètre fermer la solution dans la boîte de dialogue Options.":::


### <a name="enable-download-of-author-images-from-third-party-sources"></a>Activer le téléchargement d’images créées à partir de sources tierces

Activer le téléchargement d’images créées à partir de sources tierces est un paramètre spécifique à Visual Studio au niveau de la portée globale. Lorsque cette option est activée, les images d’auteur sont téléchargées à partir du [service d’images Gravatar](https://en.gravatar.com/), si elles sont disponibles, et affichées dans les vues de validation et d’historique.

:::image type="content" source="media/download-image-setting.png" alt-text="Capture d’écran montrant la case à cocher pour activer le téléchargement d’images créées à partir d’une source tierce dans la boîte de dialogue Options. ":::

>[!IMPORTANT]
>Afin de fournir des images d’auteur dans les vues de validation et d’historique, l’outil crée un hachage MD5 pour les adresses de messagerie de l’auteur stockées dans le référentiel actif. Ce hachage est ensuite envoyé à Gravatar pour rechercher une valeur de hachage correspondante pour les utilisateurs qui se sont déjà inscrits au service. Si une correspondance est trouvée, l’image de l’utilisateur est récupérée du service et affichée dans Visual Studio. Les utilisateurs qui n’ont pas configuré le service renverront une image générée de façon aléatoire. Notez que les adresses e-mail ne sont pas enregistrées par Visual Studio et ne sont jamais partagées avec Gravatar ou tout autre tiers.

### <a name="commit-changes-after-merge-by-default"></a>Valider les modifications après la fusion par défaut

Lorsque l’option **valider les modifications après la fusion par défaut** est activée, Git crée automatiquement une nouvelle validation lorsqu’une branche est fusionnée avec la branche active.

:::image type="content" source="media/merge-commit-setting.png" alt-text="Capture d’écran montrant la case à cocher pour valider les modifications après la fusion par défaut dans la boîte de dialogue Options.":::

- Lorsque `git merge` cette option est activée, les commandes émises par Visual Studio sont exécutées avec l' `--commit` option.
- Quand cette option est désactivée, `git merge` les commandes émises par Visual Studio sont exécutées avec les `--no-commit --no-ff` options.

Pour plus d’informations sur ces options, consultez [--validation et--no-commit](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---commit) et [--no-FF](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---no-ff).

### <a name="enable-push---force-with-lease"></a>Activer Push--force-with-Lease

Quand cette option est activée, ce paramètre vous permet de le faire dans `push --force-with-lease` Visual Studio. Par défaut, **activer Push--force-with-Lease** est désactivé.

:::image type="content" source="media/push-force-setting.png" alt-text="Capture d’écran montrant la case à cocher pour activer l’option push force avec bail dans la boîte de dialogue Options.":::

Pour plus d’informations, consultez [Push--force-with-Lease](https://git-scm.com/docs/git-push#Documentation/git-push.txt---no-force-with-lease).

### <a name="open-folder-in-solution-explorer-when-opening-a-git-repository"></a>Ouvrir le dossier dans Explorateur de solutions lors de l’ouverture d’un référentiel git
<!-- todo: write section -->
Quand vous utilisez Visual Studio pour ouvrir ou basculer vers un référentiel git, Visual Studio charge le contenu git pour vous permettre d’afficher les modifications, les validations, les branches et la gestion de votre référentiel à partir de l’IDE. En outre, Visual Studio chargera également le code du référentiel dans Explorateur de solutions. Visual Studio analyse le dossier de référentiel à la recherche de solutions, de CMakeLists.txt ou de tout autre fichier de vue qu’il reconnaît et les affiche sous forme de liste dans Explorateur de solutions. À partir de là, vous pouvez sélectionner une solution à charger ou le dossier pour afficher le contenu du répertoire. Lorsque vous désactivez cette case à cocher, Visual Studio n’ouvre pas le dossier du référentiel dans Explorateur de solutions. Cela vous permettra essentiellement d’ouvrir Visual Studio en tant que gestionnaire de référentiel git uniquement. Ce paramètre est activé par défaut.

:::image type="content" source="media/open-folder-setting.png" alt-text="Capture d’écran montrant la case à cocher permettant d’ouvrir le dossier lors de l’ouverture d’un référentiel git dans la boîte de dialogue Options.":::

### <a name="automatically-load-the-solution-when-opening-a-git-repository"></a>Charger automatiquement la solution lors de l’ouverture d’un référentiel git

Ce paramètre s’applique uniquement lorsque le paramètre [ouvrir le dossier dans Explorateur de solutions lors de l’ouverture d’un référentiel git](#open-folder-in-solution-explorer-when-opening-a-git-repository) est activé. Lorsque vous ouvrez un référentiel git dans Visual Studio et que l’analyse des dossiers suivante détecte qu’il n’existe qu’une seule solution dans votre référentiel, Visual Studio charge automatiquement cette solution. Si vous désactivez le paramètre, le Explorateur de solutions affichera la solution unique présente dans le référentiel dans la liste des vues. Mais il ne chargera pas la solution. Par défaut, ce paramètre est désactivé.

:::image type="content" source="media/load-solution-setting.png" alt-text="Capture d’écran montrant la case à cocher pour charger automatiquement la solution lors de l’ouverture d’un référentiel git dans la boîte de dialogue Options.":::

### <a name="automatically-check-out-branches-with-double-click-or-the-enter-key"></a>Extraire automatiquement les branches avec un double-clic ou la touche entrée

La fenêtre dépôt git contient une liste des branches affichées dans une arborescence. Une seule sélection d’une branche permet de faire basculer le volet historique de validation pour afficher les validations de la branche sélectionnée. Pour extraire une branche, vous pouvez cliquer avec le bouton droit pour ouvrir le menu contextuel et sélectionner **extraire**. Si vous activez ce paramètre, le fait de double-cliquer ou d’appuyer sur la touche entrée permet d’extraire la branche et d’afficher ses validations. 
  
:::image type="content" source="media/checkout-branch-setting.png" alt-text="Capture d’écran montrant la case à cocher pour extraire des branches à l’aide de la touche double-clic ou entrée dans la boîte de dialogue Options.":::


## <a name="see-also"></a>Voir aussi

> [!IMPORTANT]
> Si vous avez une suggestion pour nous, faites-le nous savoir ! Nous apprécions l’occasion de vous contacter en cas de décisions de conception via le portail de la [**communauté des développeurs**](https://aka.ms/vsgitsuggestions) .

- [Prise en main de git et GitHub dans le didacticiel Visual Studio](/learn/modules/visual-studio-github-push/) sur Microsoft Learn
- Vidéo [Getting started with Git in Visual Studio](https://www.youtube.com/watch?v=GCZ9x3yqkyc) sur YouTube
- [Productivité améliorée avec git dans Visual Studio billet de](https://devblogs.microsoft.com/visualstudio/enhanced-productivity-with-git-in-visual-studio/) blog
- [Options (boîte de dialogue)](../ide/reference/options-dialog-box-visual-studio.md)
