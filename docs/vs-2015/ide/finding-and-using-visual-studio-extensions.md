---
title: Recherche et utilisation des extensions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: df6219a66b0f6c85e197b209741706abc7ce3d06
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655876"
---
# <a name="finding-and-using-visual-studio-extensions"></a>Recherche et utilisation des extensions Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les extensions Visual Studio sont des packages de code qui s’exécutent à l’intérieur de Visual Studio et fournissent des fonctionnalités de Visual Studio nouvelles ou améliorées. Vous trouverez plus d’informations sur les extensions Visual Studio ici : [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Vous pouvez utiliser la boîte de dialogue **Extensions et mises à jour** pour installer des extensions et des exemples Visual Studio à partir de sites Web ou d'autres emplacements, puis les activer, les désactiver, les mettre à jour ou les désinstaller. (**Outils / Extensions et mises à jour**, ou tapez **Extensions** dans la fenêtre de **lancement rapide** ). La boîte de dialogue affiche également les mises à jour des exemples et extensions installés. Vous pouvez également télécharger des extensions à partir de sites web ou les obtenir auprès d'autres développeurs.

> [!NOTE]
> À compter de Visual Studio 2015, les extensions hébergées dans la galerie Visual Studio seront automatiquement mises à jour.  Vous pouvez modifier ce paramètre via la boîte de dialogue **Extensions et mises à jour** .  Pour plus d'informations, consultez la section relative aux **mises à jour d'extensions automatiques** , ci-dessous.

## <a name="finding-visual-studio-extensions"></a>Recherche d’extensions Visual Studio
 Vous pouvez installer des extensions à partir de la [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou de la [Galerie d’exemples](https://code.msdn.microsoft.com/vstudio) sur le site Web Microsoft. Ces extensions peuvent être des contrôles, des exemples, des modèles, des outils ou d'autres composants qui ajoutent des fonctionnalités à Visual Studio. Visual Studio prend en charge les extensions sous la forme de packages VSIX (ceux-ci incluent des modèles de projet, des modèles d'élément, des éléments de **boîte à outils** , des composants MEF (Managed Extension Framework) et des VSPackages). Vous pouvez également télécharger et installer les extensions basées sur Microsoft Installer (MSI), mais la boîte de dialogue **Extensions et mises à jour** ne peut pas les activer ni les désactiver. La galerie Visual Studio contient des extensions VSIX et MSI.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Installation ou désinstallation d’extensions Visual Studio
 Dans la boîte de dialogue **Extensions et mises à jour**, recherchez l'extension à installer. (Si vous connaissez le nom ou une partie du nom de l’extension, vous pouvez effectuer une recherche dans la fenêtre Rechercher dans la **Galerie Visual Studio** .) Cliquez sur **Télécharger**, puis sur **installer**. Pour charger l'extension, vous devez redémarrer Visual Studio.

 Si vous essayez d'installer une extension qui a des dépendances, le programme d'installation vérifie si elles sont déjà installées. Si elles ne sont pas installées, la boîte de dialogue **Extensions et mises à jour** donne la liste des dépendances qui doivent être installées avant que vous puissiez installer l'extension.

 Si vous souhaitez cesser d'utiliser une extension, vous pouvez la désactiver ou la désinstaller. La désactivation d'une extension maintient l'extension installée mais elle n'est pas chargée. Vous pouvez désactiver uniquement les extensions VSIX. Les extensions qui ont été installées à l'aide d'un fichier MSI peuvent uniquement être désinstallées. Recherchez l'extension et cliquez sur **Désinstaller** ou **Désactiver**. Pour décharger une extension désactivée, vous devez redémarrer Visual Studio.

## <a name="per-user-and-administrative-extensions"></a>Extensions par utilisateur et d'administration
 La plupart des extensions sont des extensions par utilisateur, qui sont installées dans le dossier **%LocalAppData%\Microsoft\VisualStudio\\<version de Visual Studio\>\Extensions\\** . Certaines extensions sont des extensions d’administration, installées dans le dossier **\<dossier d’installation de Visual Studio>\Common7\IDE\Extensions\\** .

 Pour protéger votre système contre les extensions pouvant contenir des erreurs ou du code malveillant, vous pouvez limiter le chargement des extensions par utilisateur aux cas où Visual Studio est exécuté avec des autorisations d'utilisateur normales. Les extensions par utilisateur sont ainsi désactivées lorsque Visual Studio est exécuté avec des autorisations d'administrateur. Pour ce faire, accédez à la page d’options **Extensions et mises à jour** (**Outils / Options**, **Environnement**, **Extensions et mises à jour**, ou tapez simplement **Extension** dans la fenêtre de **lancement rapide** ). Décochez la case **Charger les extensions par utilisateur lors d'une exécution en tant qu'administrateur** , puis redémarrez Visual Studio.

## <a name="automatic-extension-updates"></a>mises à jour d'extensions automatiques
 Les extensions par utilisateur sont automatiquement mises à jour lorsqu'une nouvelle version est disponible dans la galerie Visual Studio.  La nouvelle version de l'extension est détectée et installée en arrière-plan, de sorte que lors du redémarrage suivant de Visual Studio, la nouvelle version de l'extension sera exécutée.

 Seules les extensions par utilisateur peuvent être mises à jour automatiquement.  Les extensions d'administration qui sont installées pour tous les utilisateurs ne seront pas mises à jour et vous continuez à installer manuellement les nouvelles versions via le nœud **Mises à jour** de la boîte de dialogue **Extensions et mises à jour** . Vous pouvez voir les extensions qui seront mises à jour automatiquement dans le volet d'informations des extensions de la boîte de dialogue **Extensions et mises à jour** .

 Si vous voulez désactiver les mises à jour automatiques, vous pouvez désactiver cette fonctionnalité pour toutes les extensions ou uniquement pour des extensions spécifiques.

- Pour désactiver les mises à jour automatiques pour toutes les extensions, cliquez sur le lien **Modifier vos paramètres Extensions et mises à jour** dans la boîte de dialogue **Extensions et mises à jour** , puis décochez **Mettre automatiquement à jour les extensions**.

- Pour désactiver les mises à jour automatiques pour une extension spécifique, décochez l'option **Mettre automatiquement à jour cette extension** dans le volet d'informations de l'extension sur le côté droit de la boîte de dialogue **Extensions et mises à jour** .

> [!NOTE]
> À partir de Visual Studio 2015 Update 2, vous pouvez spécifier (dans **Outils / Options / Environnement / Extensions et mises à jour**) si vous souhaitez des mises à jour automatiques pour les extensions par utilisateur, pour toutes les extensions utilisateur ou pour les deux (le paramètre par défaut).

## <a name="sample-master-copies-and-working-copies"></a>Exemple de copies principales et de copies de travail
 Lorsque vous installez un exemple en ligne, la solution est stockée dans deux emplacements :

- Une copie de travail est stockée dans l'emplacement que vous avez spécifié dans la boîte de dialogue **Nouveau projet** .

- Une copie principale distincte est stockée sur votre ordinateur.

  Utilisez la boîte de dialogue **Extensions et mises à jour** pour effectuer les tâches suivantes, relatives aux exemples :

- Répertorier les copies principales des exemples que vous avez installés.

- Désactiver ou désinstaller la copie principale d'un exemple.

- Installer des packs d'exemples, qui sont des collections d'exemples se rapportant à une technologie ou une fonctionnalité.

- Installer différents exemples en ligne. (Vous pouvez également effectuer cette opération dans la boîte de dialogue **Nouveau projet** .)

- Afficher les notifications de mise à jour lorsque des modifications de code source sont publiées pour des exemples installés.

- Mettre à jour la copie principale d'un exemple installé lors de la réception d'une notification de mise à jour.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Installation sans utiliser la boîte de dialogue Extensions et mises à jour
 Les extensions empaquetées dans des fichiers .vsix peuvent être disponibles à d'autres emplacements que la galerie Visual Studio. La boîte de dialogue **Extensions et mises à jour** ne peut pas détecter ces fichiers, mais vous pouvez installer un fichier .vsix en double-cliquant dessus, ou en sélectionnant le fichier et en appuyant sur la touche Entrée. Après cela, suivez les instructions. Lorsque l'extension est installée, utilisez la boîte de dialogue **Extensions et mises à jour** pour l'activer, la désactiver ou la désinstaller.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Types d'extensions non pris en charge par la boîte de dialogue Extensions et mises à jour
 Visual Studio prend toujours en charge les extensions installées par le programme d'installation Microsoft (MSI), mais pas via la boîte de dialogue **Extensions et mises à jour** sans modification.

> [!TIP]
> Si une extension MSI inclut un fichier extension.vsixmanifest, elle apparaît dans la boîte de dialogue **Extensions et mises à jour** .
