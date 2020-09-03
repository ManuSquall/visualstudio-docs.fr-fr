---
title: Rechercher et installer des extensions
ms.date: 09/18/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f016af58b5799ca37b1a8f0cc54366d639c57c03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594407"
---
# <a name="manage-extensions-for-visual-studio"></a>Gérer les extensions pour Visual Studio

Les extensions sont des packages de code qui s’exécutent dans Visual Studio et fournissent des fonctionnalités nouvelles ou améliorées. Les extensions peuvent être des contrôles, des exemples, des modèles, des outils ou d’autres composants qui ajoutent des fonctionnalités à Visual Studio, par exemple, [Live share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) ou [Visual Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode).

Pour plus d’informations sur la création d’extensions Visual Studio, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md). Pour plus d’informations sur l’utilisation des extensions, consultez la page de l’extension individuelle sur [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Boîte de dialogue Extensions et mises à jour

Utilisez la boîte de dialogue **Extensions et mises à jour** pour installer et gérer les extensions Visual Studio. Pour ouvrir la boîte de dialogue **Extensions et mises à jour**, choisissez **Outils** > **Extensions et mises à jour**, ou tapez **Extensions** dans la zone de recherche **Lancement rapide**.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Boîte de dialogue gérer les extensions

Utilisez la boîte de dialogue **Gérer les extensions** pour installer et gérer les extensions Visual Studio. Pour ouvrir la boîte de dialogue **Gérer les extensions**, choisissez **Extensions** > **Gérer les extensions**. Vous pouvez également taper **Extensions** dans la zone de recherche et choisir **Gérer les extensions**.

::: moniker-end

![Fenêtre Extensions dans Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

Le volet de gauche classe les extensions par catégorie : celles qui sont installées, celles qui sont disponibles sur Visual Studio Marketplace (**En ligne**) et celles pour lesquelles des mises à jour sont disponibles. Le **Gestionnaire d’extensions itinérantes** conserve une liste de toutes les extensions Visual Studio que vous avez installées sur une machine ou une instance de Visual Studio. Il est conçu pour vous permettre de rechercher plus facilement vos extensions préférées.

## <a name="find-and-install-extensions"></a>Rechercher et installer des extensions

::: moniker range="vs-2017"

Vous pouvez installer des extensions à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com) ou de la boîte de dialogue extensions et mises à jour dans Visual Studio.

Pour installer des extensions à partir de Visual Studio :

1. Dans **Outils**  >  **extensions et mises à jour**, recherchez l’extension que vous souhaitez installer. Si vous connaissez le nom ou une partie du nom de l’extension, vous pouvez effectuer une recherche dans la fenêtre de **recherche** .

2. Sélectionnez **Télécharger**.

   L’installation de l’extension est planifiée. Votre extension sera installée après la fermeture de toutes les instances de Visual Studio.

Si vous essayez d'installer une extension qui a des dépendances, le programme d'installation vérifie si elles sont déjà installées. Si elles ne sont pas installées, la boîte de dialogue **Extensions et mises à jour** donne la liste des dépendances qui doivent être installées avant que vous puissiez installer l'extension.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Installer sans utiliser la boîte de dialogue Extensions et mises à jour

Les extensions empaquetées dans des fichiers *.vsix* peuvent être disponibles à d’autres emplacements que Visual Studio Marketplace. La boîte de dialogue **Outils**  >  **et mises à jour** ne peut pas détecter ces fichiers, mais vous pouvez installer un fichier *. vsix* en double-cliquant sur le fichier ou en sélectionnant le fichier et en appuyant sur **entrée**. Après cela, suivez les instructions. Lorsque l'extension est installée, utilisez la boîte de dialogue **Extensions et mises à jour** pour l'activer, la désactiver ou la désinstaller.

> [!NOTE]
> - Visual Studio Marketplace contient des extensions VSIX et MSI. La boîte de dialogue extensions et mises à jour ne peut pas activer ou désactiver les extensions MSI.
> - Si une extension MSI inclut un fichier *extension.vsixmanifest*, elle apparaît dans la boîte de dialogue **Extensions et mises à jour**.

::: moniker-end

::: moniker range=">=vs-2019"

Vous pouvez installer des extensions à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com) ou de la boîte de dialogue gérer les extensions dans Visual Studio.

Pour installer des extensions à partir de Visual Studio :

1. Dans **Extensions**  >  ,**gérer les extensions**, recherchez l’extension que vous souhaitez installer. (Si vous connaissez le nom ou une partie du nom de l’extension, vous pouvez effectuer une recherche dans la fenêtre **Rechercher**.)

2. Sélectionnez **Télécharger**.

   L’installation de l’extension est planifiée. Votre extension sera installée après la fermeture de toutes les instances de Visual Studio.

Si vous essayez d'installer une extension qui a des dépendances, le programme d'installation vérifie si elles sont déjà installées. Si elles ne sont pas installées, la boîte de dialogue **Gérer les extensions** répertorie les dépendances qui doivent être installées avant que vous puissiez installer l’extension.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Installer sans utiliser la boîte de dialogue Gérer les extensions

Les extensions empaquetées dans des fichiers *.vsix* peuvent être disponibles à d’autres emplacements que Visual Studio Marketplace. La boîte de dialogue **Extensions**de  >  **gestion** des extensions ne peut pas détecter ces fichiers, mais vous pouvez installer un fichier *. vsix* en double-cliquant sur le fichier ou en sélectionnant le fichier et en appuyant sur **entrée**. Après cela, suivez les instructions. Lorsque l’extension est installée, utilisez la boîte de dialogue **Gérer les extensions** pour l’activer, la désactiver ou la désinstaller.

> [!NOTE]
> - Visual Studio Marketplace contient des extensions VSIX et MSI. La boîte de dialogue gérer les extensions ne peut pas activer ou désactiver les extensions MSI.
> - Si une extension MSI inclut un fichier *extension.vsixmanifest*, elle apparaît dans la boîte de dialogue **Gérer les extensions**.

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Désinstaller ou désactiver une extension

Si vous souhaitez cesser d'utiliser une extension, vous pouvez la désactiver ou la désinstaller. La désactivation d'une extension maintient l'extension installée mais elle n'est pas chargée. Recherchez l'extension et cliquez sur **Désinstaller** ou **Désactiver**. Redémarrez Visual Studio pour décharger une extension désactivée.

> [!NOTE]
> Vous pouvez désactiver les extensions VSIX, mais pas les extensions qui ont été installées à l’aide d’un MSI. Les extensions installées dans MSI peuvent uniquement être désinstallées.

## <a name="per-user-and-administrative-extensions"></a>Extensions par utilisateur et d’administration

La plupart des extensions sont par utilisateur et sont installées dans le dossier *%LocalAppData%\Microsoft\VisualStudio \\<Visual Studio version \> \Extensions \\ * . Certaines extensions sont des extensions administratives et sont installées dans le dossier * \<Visual Studio installation folder> \Common7\IDE\Extensions \\ * .

Pour protéger votre système contre les extensions pouvant contenir des erreurs ou du code malveillant, vous pouvez limiter le chargement des extensions par utilisateur aux cas où Visual Studio est exécuté avec des autorisations d'utilisateur normales. Cela signifie que les extensions par utilisateur sont désactivées lorsque Visual Studio est exécuté avec des autorisations élevées.

Pour limiter le chargement des extensions par utilisateur :

1. Ouvrez la page Options des extensions (**Outils**  >  **options**  >  **environnement**  >  **Extensions**).

2. Désactivez la case à cocher **charger les extensions par utilisateur lors de l’exécution en tant qu’administrateur** .

3. Démarrez Visual Studio.

## <a name="automatic-extension-updates"></a>Mises à jour d’extensions automatiques

Les extensions sont mises à jour automatiquement lorsqu’une nouvelle version est disponible sur Visual Studio Marketplace. La nouvelle version de l’extension est détectée et installée en arrière-plan. À l’ouverture suivante de Visual Studio, la nouvelle version de l’extension s’exécute.

Si vous souhaitez désactiver les mises à jour automatiques, vous pouvez désactiver la fonctionnalité pour toutes les extensions ou uniquement pour des extensions spécifiques.

::: moniker range="vs-2017"

- Pour désactiver les mises à jour automatiques pour toutes les extensions, choisissez le lien **Changer les paramètres de vos extensions et mises à jour** dans la boîte de dialogue **Outils** > **Extensions et mises à jour**. Dans la boîte de dialogue **Options**, décochez **Mettre à jour automatiquement les extensions**.

- Pour désactiver les mises à jour automatiques pour une extension spécifique, décochez l’option **Mettre à jour automatiquement les extensions** dans le volet d’informations de l’extension, à droite de la boîte de dialogue **Extensions et mises à jour**.

::: moniker-end

::: moniker range=">=vs-2019"

- Pour désactiver les mises à jour automatiques pour toutes les extensions, choisissez le lien **Changer vos paramètres pour les extensions** dans la boîte de dialogue **Extensions** > **Gérer les extensions**. Dans la boîte de dialogue **Options**, décochez **Mettre à jour automatiquement les extensions**.

- Pour désactiver les mises à jour automatiques pour une extension spécifique, décochez l’option **Mettre à jour automatiquement cette extension** dans le volet d’informations de l’extension, à droite de la boîte de dialogue **Gérer les extensions**.

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Notifications de blocage et d’absence de réponse

Visual Studio vous avertit si une extension est soupçonnée d’être impliquée dans un blocage au cours d’une session précédente. Lors d’un blocage, Visual Studio stocke la pile d’exception. À son prochain démarrage, Visual Studio examine la pile en commençant par le nœud terminal et en progressant vers la base. Si Visual Studio détermine qu’un frame appartient à un module qui fait partie d’une extension installée et activée, une notification s’affiche.

Visual Studio vous avertit aussi si une extension est soupçonnée d’être à l’origine d’une absence de réponse de l’interface utilisateur.

Lorsque ces notifications s’affichent, vous pouvez ignorer la notification ou effectuer l’une des actions suivantes :

::: moniker range="vs-2017"

- Choisir **Désactiver cette extension**. Visual Studio désactive l’extension et vous indique si vous devez redémarrer votre système pour que la désactivation prenne effet. Vous pouvez réactiver l’extension dans la **Tools**  >  boîte de dialogue**extensions et mises à jour** des outils si vous le souhaitez.

::: moniker-end

::: moniker range=">=vs-2019"

- Choisir **Désactiver cette extension**. Visual Studio désactive l’extension et vous indique si vous devez redémarrer votre système pour que la désactivation prenne effet. Vous pouvez réactiver l’extension dans la boîte de dialogue **Extensions**de  >  **gestion** des extensions si vous le souhaitez.

::: moniker-end

- Choisir **Ne plus afficher ce message**.

  - Si la notification concerne un plantage dans une session antérieure, Visual Studio n’affiche plus de notification quand un plantage associé à cette extension se produit. Visual Studio continue d’afficher des notifications lorsque l’absence de réponse peut être associée à cette extension, ou pour les blocages ou toute absence de réponse qui peuvent être associés à d’autres extensions.
  - Si la notification ne répond pas, l’environnement de développement intégré (IDE) n’affiche plus de notification lorsque cette extension est associée à une absence de réponse. Visual Studio continue d’afficher les notifications liées aux incidents pour cette extension et les notifications de blocage et de non-réponse pour d’autres extensions.

- Choisissez **en savoir plus** pour accéder à cette page.

- Choisir le bouton **X** à la fin de la notification pour fermer la notification. Une nouvelle notification s’affiche pour les instances ultérieures de l’extension associées à un blocage ou une absence de réponse de l’interface utilisateur.

> [!NOTE]
> Une notification de blocage ou d’absence de réponse de l’interface utilisateur signifie seulement que l’un des modules de l’extension était sur la pile lorsque l’interface utilisateur n’a pas répondu ou lorsque le blocage s’est produit. Cela ne signifie pas nécessairement que l’extension elle-même était en cause. Il est possible que l’extension soit appelée du code qui fait partie de Visual Studio, ce qui, à son tour, a entraîné une absence de réponse de l’interface utilisateur ou un incident. Toutefois, la notification peut toujours être utile si l’extension qui a conduit au blocage ou à l’absence de réponse de l’interface utilisateur n’est pas important(e) pour vous. Dans ce cas, la désactivation de l’extension permet d’éviter le blocage ou l’absence de réponse de l’interface utilisateur à l’avenir sans affecter votre productivité.

## <a name="samples"></a>Exemples

Lorsque vous installez un exemple en ligne, la solution est stockée dans deux emplacements :

- Une copie de travail est stockée à l’emplacement que vous avez spécifié quand vous avez créé le projet.

- Une copie principale distincte est stockée sur votre ordinateur.

::: moniker range="vs-2017"

Vous pouvez utiliser la boîte de dialogue **Outils** > **Extensions et mises à jour** pour effectuer ces tâches en lien avec les exemples :

::: moniker-end

::: moniker range=">=vs-2019"

Vous pouvez utiliser la boîte de dialogue **Extensions** > **Gérer les extensions** pour effectuer ces tâches en lien avec les exemples :

::: moniker-end

- Répertorier les copies principales des exemples que vous avez installés.

- Désactiver ou désinstaller la copie principale d'un exemple.

- Installer des packs d'exemples, qui sont des collections d'exemples se rapportant à une technologie ou une fonctionnalité.

- Installer différents exemples en ligne.

- Afficher les notifications de mise à jour lorsque des modifications de code source sont publiées pour des exemples installés.

- Mettre à jour la copie principale d'un exemple installé lors de la réception d'une notification de mise à jour.

## <a name="see-also"></a>Voir aussi

- [Visual Studio Marketplace](https://marketplace.visualstudio.com)
- [SDK Visual Studio](../extensibility/visual-studio-sdk.md)
