---
title: L’expérience git dans Visual Studio 2019
titleSuffix: ''
description: Découvrez comment la nouvelle expérience git intégrée dans Visual Studio 2019 peut vous aider à être plus productif.
ms.date: 04/01/2021
ms.topic: overview
ms.author: tglee
author: TerryGLee
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.manager: jmartens
ms.openlocfilehash: 7ca09edada7715b9e7be754dbec22e1654288df8
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729310"
---
# <a name="git-experience-in-visual-studio"></a>Expérience git dans Visual Studio

Git est désormais l’expérience de contrôle de version par défaut dans Visual Studio 2019. Depuis la [version 16,6](/visualstudio/releases/2019/release-notes-v16.6), nous avons travaillé sur la création de l’ensemble de fonctionnalités et l’itération sur ce dernier en fonction de vos commentaires. La nouvelle expérience git est activée par défaut pour tout le monde avec la [version 16,8](/visualstudio/releases/2019/release-notes/).

> [!TIP]
> Git est le système de contrôle de version moderne le plus largement utilisé. Si vous êtes un développeur professionnel ou si vous apprenez à coder, git peut vous être très utile. Si vous débutez avec git, le https://git-scm.com/ site Web est un bon point de départ. Vous y trouverez des fiches récapitulatives, une documentation en ligne populaire et des vidéos de base git.

## <a name="how-to-use-git-in-visual-studio"></a>Comment utiliser Git dans Visual Studio

Nous allons vous montrer comment utiliser la nouvelle expérience git dans Visual Studio 2019, mais si vous souhaitez commencer par une présentation rapide, consultez la vidéo suivante : <br><br>*Longueur vidéo : 5,27 minutes*

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

Il existe trois façons de commencer à utiliser Git avec Visual Studio pour être plus productif :

- [Ouvrez un référentiel git existant](#open-an-existing-local-repository). Si votre code se trouve déjà sur votre ordinateur, vous pouvez l’ouvrir à l’aide de **fichier**  >  **ouvrir** le  >  **projet/solution** (ou **dossier**) et Visual Studio détecte automatiquement s’il dispose d’un référentiel git initialisé.
- [Créez un référentiel git](#create-a-new-git-repository). Si votre code n’est pas associé à git, vous pouvez créer un référentiel git.
- [Cloner un référentiel git existant](#clone-an-existing-git-repository). Si le code que vous souhaitez utiliser ne se trouve pas sur votre ordinateur, vous pouvez cloner les référentiels distants existants.

> [!NOTE]
> Depuis également la [version 16,8](/visualstudio/releases/2019/release-notes/), Visual Studio 2019 comprend une expérience de compte GitHub entièrement intégrée. Vous pouvez maintenant ajouter les comptes GitHub et GitHub Enterprise à votre trousseau. Vous serez en mesure de les ajouter et de les utiliser comme vous le feriez avec des comptes Microsoft, ce qui signifie que vous aurez plus de temps pour accéder à vos ressources GitHub dans Visual Studio. Pour plus d’informations, consultez la page [utiliser des comptes GitHub dans Visual Studio](../ide/work-with-github-accounts.md) .

## <a name="create-a-new-git-repository"></a>Créer un dépôt git

Si votre code n’est pas associé à git, vous pouvez commencer par créer un nouveau référentiel git. Pour ce faire, sélectionnez **git**  >  **créer un référentiel git** dans la barre de menus. Ensuite, dans la boîte de dialogue **créer un dépôt git** , entrez vos informations.

:::image type="content" source="media/git-create-repository.png" alt-text="La boîte de dialogue créer un dépôt git dans Visual Studio.":::

La boîte de dialogue **créer un dépôt git** vous permet de transmettre facilement votre nouveau référentiel à github. Par défaut, votre nouveau référentiel est privé, ce qui signifie que vous êtes le seul à pouvoir y accéder. Si vous décochez la case, votre référentiel est public, ce qui signifie que toute personne sur GitHub peut l’afficher.

> [!TIP]
> Que votre référentiel soit public ou privé, il est préférable de disposer d’une sauvegarde à distance de votre code stockée en toute sécurité sur GitHub, même si vous ne travaillez pas avec une équipe. Votre code est également mis à votre disposition, quel que soit l’ordinateur que vous utilisez.

Vous pouvez choisir de créer un référentiel Git local uniquement à l’aide de l’option **local uniquement** . Vous pouvez également lier votre projet local à un référentiel distant vide existant sur Azure DevOps ou tout autre fournisseur git à l’aide de l’option **Remote existante** .

## <a name="clone-an-existing-git-repository"></a>Cloner un référentiel git existant

Visual Studio offre une expérience de clonage simple. Si vous connaissez l’URL du référentiel que vous souhaitez Cloner, vous pouvez coller l’URL dans la section **emplacement du référentiel** , puis choisir l’emplacement du disque sur lequel vous souhaitez cloner Visual Studio.

:::image type="content" source="media/git-clone-repository.png" alt-text="La boîte de dialogue cloner un référentiel git dans Visual Studio.":::

Si vous ne connaissez pas l’URL du référentiel, Visual Studio vous permet d’accéder facilement à votre référentiel GitHub ou Azure DevOps existant et de le cloner.

### <a name="open-an-existing-local-repository"></a>Ouvrir un référentiel local existant

Après avoir cloné un référentiel ou en avoir créé un, Visual Studio détecte le dépôt git et l’ajoute à votre liste de **référentiels locaux** dans le menu git. À partir de là, vous pouvez rapidement accéder à vos référentiels git et basculer entre ceux-ci.

:::image type="content" source="media/git-local-repositories.png" alt-text="L’option dépôts locaux du menu git dans Visual Studio ":::

## <a name="view-files-in-solution-explorer"></a>Afficher les fichiers dans Explorateur de solutions

Lorsque vous clonez un référentiel ou ouvrez un référentiel local, Visual Studio vous bascule dans ce contexte git en enregistrant et en fermant les solutions et projets précédemment ouverts. Explorateur de solutions charge le dossier à la racine du référentiel git et analyse l’arborescence de répertoires pour tous les fichiers d’affichage. Il s’agit notamment de fichiers CMakeLists.txt ou avec l’extension de fichier. sln.

Visual Studio ajuste sa vue en fonction du fichier de vue que vous chargez dans Explorateur de solutions :

- Si vous clonez un référentiel qui contient un seul fichier. sln, Explorateur de solutions charge directement cette solution pour vous.
- Si Explorateur de solutions ne détecte pas les fichiers. sln dans votre référentiel, il charge l’affichage des dossiers par défaut.
- Si votre référentiel contient plusieurs fichiers. sln, Explorateur de solutions affiche la liste des vues disponibles dans laquelle vous pouvez effectuer votre choix.

Vous pouvez basculer entre la vue actuellement ouverte et la liste des affichages à l’aide du bouton **basculer les affichages** dans la barre d’outils Explorateur de solutions.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Explorateur de solutions avec le bouton basculer les vues sélectionné dans Visual Studio.":::

## <a name="git-changes-window"></a>Fenêtre Changements Git

Git effectue le suivi des modifications apportées aux fichiers dans votre référentiel au fur et à mesure que vous travaillez et sépare les fichiers de votre référentiel en trois catégories. Ces modifications sont équivalentes à ce que vous pouvez voir lorsque vous entrez la `git status` commande dans la ligne de commande :

- **Fichiers non modifiés**: ces fichiers n’ont pas été modifiés depuis votre dernière validation.
- **Fichiers modifiés**: ces fichiers ont été modifiés depuis votre dernière validation, mais vous ne les avez pas encore prédéfinis pour la prochaine validation.
- **Fichiers intermédiaires**: ces fichiers ont des modifications qui seront ajoutées à la prochaine validation.

Au fur et à mesure de votre travail, Visual Studio effectue le suivi des modifications apportées aux fichiers de votre projet dans la section **modifications** de la fenêtre **modifications git** .

:::image type="content" source="media/git-changes-window.png" alt-text="La fenêtre de modifications git dans Visual Studio.":::

Lorsque vous êtes prêt à modifier les modifications, cliquez sur le **+** bouton (plus) de chaque fichier que vous souhaitez mettre en scène, ou cliquez avec le bouton droit sur un fichier, puis sélectionnez **étape**. Vous pouvez également mettre en place tous vos fichiers modifiés d’un seul clic en cliquant sur le bouton « stage tout » **+** (plus) en haut de la section **modifications** .

Lorsque vous mettez en place une modification, Visual Studio crée une section **modifications intermédiaires** . Seules les modifications apportées à la section **modifications intermédiaires** sont ajoutées à la validation suivante, ce que vous pouvez faire en sélectionnant **valider les étapes intermédiaires**. La commande équivalente pour cette action est `git commit -m "Your commit message"` . Les modifications peuvent également être désactivées en cliquant sur le bouton **–** (moins). La commande équivalente pour cette action consiste `git reset <file_path>` à annuler l’étape d’un seul fichier ou `git reset <directory_path>` à désorganiser tous les fichiers d’un répertoire.

Vous pouvez également choisir de ne pas déployer vos fichiers modifiés en ignorant la zone de transit. Dans ce cas, Visual Studio vous permet de valider vos modifications directement sans avoir à les déployer. Entrez simplement votre message de validation, puis sélectionnez **valider tout**. La commande équivalente pour cette action est `git commit -a` .

Visual Studio facilite également la validation et la synchronisation d’un clic à l’aide des raccourcis **valider tout et pousser** et **valider tout et synchroniser** . Lorsque vous double-cliquez sur un fichier dans les sections **modifications** et **modifications intermédiaires** , vous pouvez voir une comparaison ligne par ligne avec la version non modifiée du fichier.

:::image type="content" source="media/git-file-version-compare.png" alt-text="Comparaison ligne par ligne des versions de fichiers dans Visual Studio ":::

> [!TIP]
> Vous pouvez associer un élément de travail Azure DevOps à une validation en utilisant le caractère « # » si vous êtes connecté au référentiel Azure DevOps. Vous pouvez connecter votre référentiel Azure DevOps via **Team Explorer**  >  **gérer les connexions**.

### <a name="select-an-existing-branch"></a>Sélectionner une branche existante

Visual Studio affiche la branche active dans le sélecteur en haut de la fenêtre **modifications git** .

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Les branches actuelles que vous pouvez afficher à l’aide du sélecteur en haut du sélecteur git change dans Visual Studio ":::

La branche active est également disponible dans la barre d’État dans le coin inférieur droit de l’IDE de Visual Studio.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Branches actuelles que vous pouvez afficher à l’aide de la barre d’état située dans l’angle inférieur droit de l’IDE de Visual Studio ":::

À partir des deux emplacements, vous pouvez basculer entre les branches existantes.

### <a name="create-a-new-branch"></a>Créer une branche

Vous pouvez également créer une nouvelle branche. La commande équivalente pour cette action est `git checkout -b <branchname>` .

La création d’une branche est aussi simple que l’entrée du nom de la branche et la base d’une branche existante.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Boîte de dialogue créer une nouvelle branche dans Visual Studio ":::

Vous pouvez choisir une branche locale ou distante existante comme base. La case à cocher **retirer la branche** vous permet de basculer automatiquement vers la branche nouvellement créée. La commande équivalente pour cette action est `git checkout -b <new-branch><existing-branch>` .

## <a name="git-repository-window"></a>Boîte de dépôt git

Visual Studio dispose d’une nouvelle fenêtre de **référentiel git** , qui est une vue consolidée de tous les détails de votre référentiel, y compris toutes les branches, les distants et les historiques de validation. Vous pouvez accéder à cette fenêtre directement à partir de **git** ou d’une **vue** dans la barre de menus ou à partir de la barre d’État.

### <a name="manage-branches"></a>Gérer les branches

Lorsque vous sélectionnez **gérer des branches** dans le menu **git** , vous voyez s’afficher l’arborescence des branches dans la fenêtre **dépôt git** . Dans le volet gauche, vous pouvez utiliser le menu contextuel pour valider des branches, créer des branches, fusionner, rebaser, sélectionner une cerise, et bien plus encore. Lorsque vous cliquez sur la branche, vous pouvez voir un aperçu de son historique des validations dans le volet droit.

### <a name="incoming-and-outgoing-commits"></a>Validations entrantes et sortantes

Lorsque vous extrayez une branche, la fenêtre **modifications git** contient un indicateur sous la liste déroulante branche, qui affiche le nombre de validations non extraites de la branche distante. Cet indicateur vous indique également le nombre de validations locales non push.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="La fenêtre modifications git qui affiche l’élément d’interface utilisateur déroulant d’indicateur dans Visual Studio ":::

L’indicateur fonctionne également comme un lien pour vous connecter à l’historique de validation de cette branche dans la fenêtre de **dépôt git** . Le haut de l’historique affiche désormais les détails de ces validations entrantes et sortantes. À partir de là, vous pouvez également décider d’extraire ou de pousser les validations.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Fenêtre de dépôt git qui affiche l’historique de validation d’une branche dans Visual Studio ":::

#### <a name="commit-details"></a>Détails de la validation

Lorsque vous double-cliquez sur une **validation**, Visual Studio ouvre ses détails dans une fenêtre outil distincte. À partir de là, vous pouvez annuler la validation, réinitialiser la validation, modifier le message de validation ou créer une étiquette sur la validation. Lorsque vous cliquez sur un fichier modifié dans la validation, Visual Studio ouvre la vue de **comparaison** côte à côte de la validation et de son parent.

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Boîte de dialogue détails de la validation dans Visual Studio ":::

## <a name="handle-merge-conflicts"></a>Gérer les conflits de fusion

Des conflits peuvent se produire lors d’une fusion si deux développeurs modifient les mêmes lignes dans un fichier et git ne sait pas automatiquement ce qui est correct. Git interrompt la fusion et vous informe que vous êtes dans un État conflictuel.

Visual Studio facilite l’identification et la résolution d’un conflit de fusion. Tout d’abord, la fenêtre **dépôt git** affiche une barre d’informations dorée en haut de la fenêtre.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Message « la fusion s’est terminée avec des conflits » dans Visual Studio ":::

La fenêtre **modifications git** affiche également un message « la *fusion est en cours avec des conflits*», avec les fichiers non fusionnés dans leur section distincte située en dessous.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Message « fusionner en cours avec des conflits » dans Visual Studio ":::

Toutefois, si aucune de ces fenêtres n’est ouverte et que vous accédez au fichier qui comporte des conflits de fusion, vous n’avez pas besoin de rechercher le texte suivant :

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Au lieu de cela, Visual Studio affiche une barre d’info dorée en haut de la page qui indique que le fichier ouvert présente des conflits. Ensuite, vous pouvez cliquer sur le lien pour ouvrir l' **éditeur de fusion**.

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Capture d’écran du message « le fichier contient des conflits de fusion » dans Visual Studio ":::

### <a name="the-merge-editor"></a>Éditeur de fusion

L’éditeur de fusion dans Visual Studio est un outil de fusion triple qui affiche les modifications entrantes, vos modifications actuelles et le résultat de la fusion. Vous pouvez utiliser la barre d’outils au niveau supérieur de l' **éditeur de fusion** pour naviguer entre les conflits et les différences fusionnées automatiquement dans le fichier.

:::image type="content" source="media/git-merge-editor.png" alt-text="Éditeur de fusion dans Visual Studio ":::

Vous pouvez également utiliser les basculements pour afficher/masquer les différences, afficher/masquer les différences de mots et personnaliser la disposition. Les cases à cocher situées en haut de chaque côté vous permettent d’effectuer toutes les modifications d’un côté ou de l’autre. Toutefois, pour prendre des modifications individuelles, vous pouvez cliquer sur les cases à cocher à gauche des lignes conflictuelles de chaque côté. Enfin, lorsque vous avez terminé la résolution des conflits, vous pouvez sélectionner le bouton **accepter la fusion** dans l’éditeur de fusion. Vous écrivez ensuite un message de validation et validez les modifications pour terminer la résolution.

## <a name="personalize-your-git-settings"></a>Personnaliser vos paramètres git

Pour personnaliser et personnaliser vos paramètres git au niveau du référentiel, ainsi qu’au niveau global, accédez aux   >  **paramètres** git dans la barre de menus ou aux **Outils**  >  **options**  >  **contrôle de code source** dans la barre de menus. Ensuite, choisissez les options souhaitées.

:::image type="content" source="media/git-options-settings.png" alt-text="Boîte de dialogue Options dans laquelle vous pouvez choisir des paramètres de personnalisation et de personnalisation dans l’IDE de Visual Studio ":::

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio"></a>Comment utiliser l’expérience d’Team Explorer complète dans Visual Studio

La nouvelle expérience git est le système de contrôle de version par défaut de Visual Studio 2019 à partir de la [version 16,8](/visualstudio/releases/2019/release-notes/) . Toutefois, si vous souhaitez la désactiver, vous pouvez. Accédez à **Outils**  >  **options**  >  **environnement** en préversion  >   , puis activez la case à cocher **nouvelle expérience utilisateur git** pour revenir à Team Explorer pour git.

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="La section fonctionnalités en version préliminaire de la boîte de dialogue Options dans Visual Studio ":::

## <a name="whats-next"></a>Étapes suivantes

Alors que la nouvelle expérience git est désormais activée par défaut dans Visual Studio 2019 [version 16,8](/visualstudio/releases/2019/release-notes/), nous continuons à ajouter de nouvelles fonctionnalités pour améliorer l’expérience. Si vous souhaitez consulter les nouvelles mises à jour apportées à l’expérience git dans une version préliminaire, vous pouvez la télécharger et l’installer à partir de la page [Visual Studio Preview](https://aka.ms/vspreview/) .

> [!IMPORTANT]
> Si vous avez une suggestion pour nous, faites-le nous savoir ! Nous apprécions l’occasion de vous contacter en cas de décisions de conception via le portail de la [**communauté des développeurs**](https://aka.ms/vs-suggest) .

## <a name="see-also"></a>Voir aussi

- [Prise en main de git et GitHub dans le didacticiel Visual Studio](/learn/modules/visual-studio-github-push/) sur Microsoft Learn
- Vidéo [Getting started with Git in Visual Studio](https://www.youtube.com/watch?v=GCZ9x3yqkyc) sur YouTube
- [Annonce de la publication de l’expérience git dans le](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/) billet de blog Visual Studio
- [Lancement de la nouvelle vidéo git Experience](https://www.youtube.com/watch?v=UHrAg3iKoe0&t) sur YouTube
- [La série de la boîte à outils Visual Studio présente : la nouvelle vidéo git Experience](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) sur Channel 9 et sur [YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be)
- [Nouvelles mises à jour intéressantes de l’expérience git dans le billet de blog Visual Studio](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/)
- Amélioration [de l’expérience git dans le billet de blog Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)
- [Utiliser des comptes GitHub dans Visual Studio](../ide/work-with-github-accounts.md)
- [Notes de publication de Visual Studio 2019](/visualstudio/releases/2019/release-notes)
