---
title: Rechercher et utiliser des extensions
ms.date: 01/30/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e282cdfda27579fd83871153a19897652d55865
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62962057"
---
# <a name="find-and-use-visual-studio-extensions"></a>Rechercher et utiliser des extensions Visual Studio

Les extensions Visual Studio sont des packages de code qui s’exécutent à l’intérieur de Visual Studio et fournissent des fonctionnalités de Visual Studio nouvelles ou améliorées. Vous trouverez plus d’informations sur les extensions Visual Studio ici : [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

::: moniker range="vs-2017"

Utilisez la boîte de dialogue **Extensions et mises à jour** pour installer et gérer les extensions Visual Studio. Pour ouvrir la boîte de dialogue **Extensions et mises à jour**, choisissez **Outils** > **Extensions et mises à jour**, ou tapez **Extensions** dans la zone de recherche **Lancement rapide**.

::: moniker-end

::: moniker range=">=vs-2019"

Utilisez la boîte de dialogue **Gérer les extensions** pour installer et gérer les extensions Visual Studio. Pour ouvrir la boîte de dialogue **Gérer les extensions**, choisissez **Extensions** > **Gérer les extensions**. Vous pouvez également taper **Extensions** dans la zone de recherche et choisir **Gérer les extensions**.

::: moniker-end

![Fenêtre Extensions dans Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

Le volet de gauche classe les extensions par catégorie : celles qui sont installées, celles qui sont disponibles sur Visual Studio Marketplace (**En ligne**) et celles pour lesquelles des mises à jour sont disponibles. Le **Gestionnaire d’extensions itinérantes** conserve une liste de toutes les extensions Visual Studio que vous avez installées sur une machine ou une instance de Visual Studio. Il est conçu pour vous permettre de rechercher plus facilement vos extensions préférées.

## <a name="find-visual-studio-extensions"></a>Rechercher des extensions Visual Studio

Vous pouvez installer des extensions à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Ces extensions peuvent être des contrôles, des exemples, des modèles, des outils ou d'autres composants qui ajoutent des fonctionnalités à Visual Studio. Visual Studio prend en charge les extensions sous la forme de packages VSIX (ceux-ci incluent des modèles de projet, des modèles d'élément, des éléments de **boîte à outils** , des composants MEF (Managed Extension Framework) et des VSPackages).

::: moniker range="vs-2017"

Vous pouvez également télécharger et installer les extensions basées sur Microsoft Installer (MSI), mais la boîte de dialogue **Extensions et mises à jour** ne peut pas les activer ni les désactiver. Visual Studio Marketplace contient des extensions VSIX et MSI.

::: moniker-end

::: moniker range=">=vs-2019"

Vous pouvez également télécharger et installer des extensions basées sur Microsoft Installer (MSI), mais la boîte de dialogue **Gérer les extensions** ne peut pas les activer ni les désactiver. Visual Studio Marketplace contient des extensions VSIX et MSI.

::: moniker-end

## <a name="install-or-uninstall-visual-studio-extensions"></a>Installer ou désinstaller des extensions Visual Studio

::: moniker range="vs-2017"

Dans **Extensions et mises à jour**, recherchez l’extension à installer. (Si vous connaissez le nom ou une partie du nom de l’extension, vous pouvez effectuer une recherche dans la fenêtre **Rechercher**.) Cliquez sur **Télécharger**. L’installation de l’extension est planifiée. Votre extension sera installée après la fermeture de toutes les instances de Visual Studio.

Si vous essayez d'installer une extension qui a des dépendances, le programme d'installation vérifie si elles sont déjà installées. Si elles ne sont pas installées, la boîte de dialogue **Extensions et mises à jour** donne la liste des dépendances qui doivent être installées avant que vous puissiez installer l'extension.

::: moniker-end

::: moniker range=">=vs-2019"

Dans **Gérer les extensions**, recherchez l’extension à installer. (Si vous connaissez le nom ou une partie du nom de l’extension, vous pouvez effectuer une recherche dans la fenêtre **Rechercher**.) Cliquez sur **Télécharger**. L’installation de l’extension est planifiée. Votre extension sera installée après la fermeture de toutes les instances de Visual Studio.

Si vous essayez d'installer une extension qui a des dépendances, le programme d'installation vérifie si elles sont déjà installées. Si elles ne sont pas installées, la boîte de dialogue **Gérer les extensions** répertorie les dépendances qui doivent être installées avant que vous puissiez installer l’extension.

::: moniker-end

Si vous souhaitez cesser d'utiliser une extension, vous pouvez la désactiver ou la désinstaller. La désactivation d'une extension maintient l'extension installée mais elle n'est pas chargée. Vous pouvez désactiver uniquement les extensions VSIX. Les extensions qui ont été installées à l'aide d'un fichier MSI peuvent uniquement être désinstallées. Recherchez l'extension et cliquez sur **Désinstaller** ou **Désactiver**. Redémarrez Visual Studio pour décharger une extension désactivée.

## <a name="per-user-and-administrative-extensions"></a>Extensions par utilisateur et d’administration

La plupart des extensions sont des extensions par utilisateur, qui sont installées dans le dossier *%LocalAppData%\Microsoft\VisualStudio\\<version de Visual Studio\>\Extensions\\*. Quelques-unes des extensions sont des extensions d’administration et sont installées dans le dossier *\<dossier d’installation de Visual Studio>\Common7\IDE\Extensions\\*.

Pour protéger votre système contre les extensions pouvant contenir des erreurs ou du code malveillant, vous pouvez limiter le chargement des extensions par utilisateur aux cas où Visual Studio est exécuté avec des autorisations d'utilisateur normales. Les extensions par utilisateur sont ainsi désactivées lorsque Visual Studio est exécuté avec des autorisations d'administrateur. Pour ce faire, accédez à la page d’options des extensions (**Outils** > **Options** > **Environnement** > **Extensions**). Décochez la case **Charger les extensions par utilisateur lors d'une exécution en tant qu'administrateur** , puis redémarrez Visual Studio.

## <a name="automatic-extension-updates"></a>Mises à jour d’extensions automatiques

Les extensions sont automatiquement mises à jour quand une nouvelle version est disponible sur Visual Studio Marketplace. La nouvelle version de l’extension est détectée et installée en arrière-plan. À l’ouverture suivante de Visual Studio, la nouvelle version de l’extension s’exécute.

Si vous voulez désactiver les mises à jour automatiques, vous pouvez désactiver cette fonctionnalité pour toutes les extensions ou uniquement pour des extensions spécifiques.

::: moniker range="vs-2017"

- Pour désactiver les mises à jour automatiques pour toutes les extensions, choisissez le lien **Changer les paramètres de vos extensions et mises à jour** dans la boîte de dialogue **Extensions et mises à jour**. Dans la boîte de dialogue **Options**, décochez **Mettre à jour automatiquement les extensions**.

- Pour désactiver les mises à jour automatiques pour une extension spécifique, décochez l’option **Mettre à jour automatiquement les extensions** dans le volet d’informations de l’extension, à droite de la boîte de dialogue **Extensions et mises à jour**.

::: moniker-end

::: moniker range=">=vs-2019"

- Pour désactiver les mises à jour automatiques pour toutes les extensions, choisissez le lien **Changer vos paramètres pour les extensions** dans la boîte de dialogue **Gérer les extensions**. Dans la boîte de dialogue **Options**, décochez **Mettre à jour automatiquement les extensions**.

- Pour désactiver les mises à jour automatiques pour une extension spécifique, décochez l’option **Mettre à jour automatiquement cette extension** dans le volet d’informations de l’extension, à droite de la boîte de dialogue **Gérer les extensions**.

::: moniker-end

## <a name="extension-crash-and-unresponsiveness-notifications"></a>Notifications de plantage/d’absence de réponse d’une extension

Visual Studio vous avertit si une extension est soupçonnée d’être impliquée dans un blocage au cours d’une session précédente. Lors d’un blocage, Visual Studio stocke la pile d’exception. À son prochain démarrage, Visual Studio examine la pile en commençant par le nœud terminal et en progressant vers la base. Si Visual Studio détermine qu’un frame appartient à un module qui fait partie d’une extension installée et activée, une notification s’affiche.

Visual Studio vous avertit aussi si une extension est soupçonnée d’être à l’origine d’une absence de réponse de l’interface utilisateur.

Lorsque ces notifications s’affichent, vous pouvez ignorer la notification ou effectuer l’une des actions suivantes :

::: moniker range="vs-2017"

- Choisir **Désactiver cette extension**. Visual Studio désactive l’extension et vous indique si vous devez redémarrer votre système pour que la désactivation prenne effet. Vous pouvez réactiver l’extension dans la boîte de dialogue **Extensions et mises à jour** si vous le souhaitez.

::: moniker-end

::: moniker range=">=vs-2019"

- Choisir **Désactiver cette extension**. Visual Studio désactive l’extension et vous indique si vous devez redémarrer votre système pour que la désactivation prenne effet. Vous pouvez réactiver l’extension dans la boîte de dialogue **Gérer les extensions** si vous le souhaitez.

::: moniker-end

- Choisir **Ne plus afficher ce message**.

  - Si la notification concerne un plantage dans une session antérieure, Visual Studio n’affiche plus de notification quand un plantage associé à cette extension se produit. Visual Studio continue d’afficher des notifications lorsque l’absence de réponse peut être associée à cette extension, ou pour les blocages ou toute absence de réponse qui peuvent être associés à d’autres extensions.
  - Si la notification concerne une absence de réponse, l’IDE n’affiche plus de notification quand cette extension est associée à l’absence de réponse. Visual Studio continue d’afficher des notifications relatives aux blocages pour cette extension et des notifications relatives aux blocages et à l’absence de réponse pour les autres extensions.

- Choisir **En savoir plus** pour accéder à cette page.

- Choisir le bouton **X** à la fin de la notification pour fermer la notification. Une nouvelle notification s’affiche pour les instances ultérieures de l’extension associées à un blocage ou une absence de réponse de l’interface utilisateur.

> [!NOTE]
> Une notification de blocage ou d’absence de réponse de l’interface utilisateur signifie seulement que l’un des modules de l’extension était sur la pile lorsque l’interface utilisateur n’a pas répondu ou lorsque le blocage s’est produit. Cela ne signifie pas nécessairement que l’extension elle-même était en cause. Il est possible que l’extension ait appelé du code qui fait partie de Visual Studio, qui à son tour a entraîné une absence de réponse de l’interface utilisateur ou un blocage. Toutefois, la notification peut toujours être utile si l’extension qui a conduit au blocage ou à l’absence de réponse de l’interface utilisateur n’est pas important(e) pour vous. Dans ce cas, la désactivation de l’extension permet d’éviter le blocage ou l’absence de réponse de l’interface utilisateur à l’avenir sans affecter votre productivité.

## <a name="sample-master-copies-and-working-copies"></a>Exemples de copies principales et de copies de travail

Lorsque vous installez un exemple en ligne, la solution est stockée dans deux emplacements :

- Une copie de travail est stockée à l’emplacement que vous avez spécifié quand vous avez créé le projet.

- Une copie principale distincte est stockée sur votre ordinateur.

::: moniker range="vs-2017"

Utilisez la fenêtre **Extensions et mises à jour** pour effectuer les tâches suivantes, relatives aux exemples :

::: moniker-end

::: moniker range=">=vs-2019"

Utilisez la fenêtre **Gérer les extensions** pour effectuer les tâches suivantes, relatives aux exemples :

::: moniker-end

- Répertorier les copies principales des exemples que vous avez installés.

- Désactiver ou désinstaller la copie principale d'un exemple.

- Installer des packs d'exemples, qui sont des collections d'exemples se rapportant à une technologie ou une fonctionnalité.

- Installer différents exemples en ligne.

- Afficher les notifications de mise à jour lorsque des modifications de code source sont publiées pour des exemples installés.

- Mettre à jour la copie principale d'un exemple installé lors de la réception d'une notification de mise à jour.

::: moniker range="vs-2017"

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Installation sans utiliser la boîte de dialogue Extensions et mises à jour

Les extensions empaquetées dans des fichiers *.vsix* peuvent être disponibles à d’autres emplacements que Visual Studio Marketplace. La boîte de dialogue **Extensions et mises à jour** ne peut pas détecter ces fichiers, mais vous pouvez installer un fichier *.vsix* en double-cliquant sur ce dernier, ou en le sélectionnant et en appuyant sur la touche **Entrée**. Après cela, suivez les instructions. Lorsque l'extension est installée, utilisez la boîte de dialogue **Extensions et mises à jour** pour l'activer, la désactiver ou la désinstaller.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Types d’extension non pris en charge par la boîte de dialogue Extensions et mises à jour

Visual Studio prend toujours en charge les extensions installées par le programme d'installation Microsoft (MSI), mais pas via la boîte de dialogue **Extensions et mises à jour** sans modification.

> [!TIP]
> Si une extension MSI inclut un fichier *extension.vsixmanifest*, elle apparaît dans la boîte de dialogue **Extensions et mises à jour**.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="installing-without-using-the-manage-extensions-dialog-box"></a>Installation sans utiliser la boîte de dialogue Gérer les extensions

Les extensions empaquetées dans des fichiers *.vsix* peuvent être disponibles à d’autres emplacements que Visual Studio Marketplace. La boîte de dialogue **Gérer les extensions** ne peut pas détecter ces fichiers, mais vous pouvez installer un fichier *.vsix* en double-cliquant sur ce dernier, ou en le sélectionnant et en appuyant sur la touche **Entrée**. Après cela, suivez les instructions. Lorsque l’extension est installée, utilisez la boîte de dialogue **Gérer les extensions** pour l’activer, la désactiver ou la désinstaller.

## <a name="extension-types-not-supported-by-the-manage-extensions-dialog-box"></a>Types d’extension non pris en charge par la boîte de dialogue Gérer les extensions

Visual Studio prend toujours en charge les extensions installées par le programme d’installation Microsoft (MSI), mais pas via la boîte de dialogue **Gérer les extensions** sans modification.

> [!TIP]
> Si une extension MSI inclut un fichier *extension.vsixmanifest*, elle apparaît dans la boîte de dialogue **Gérer les extensions**.

::: moniker-end