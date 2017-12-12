---
title: Recherche et utilisation des extensions Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 06/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0327ccaa52f3bd348246eea39b754f5c9069f3a1
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="finding-and-using-visual-studio-extensions"></a>Recherche et utilisation des extensions Visual Studio
Les extensions Visual Studio sont des packages de code qui s’exécutent à l’intérieur de Visual Studio et fournissent des fonctionnalités de Visual Studio nouvelles ou améliorées. Vous trouverez plus d’informations sur les extensions Visual Studio ici : [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  

 Vous pouvez utiliser la boîte de dialogue **Extensions et mises à jour** pour installer des extensions et des exemples Visual Studio à partir de sites Web ou d'autres emplacements, puis les activer, les désactiver, les mettre à jour ou les désinstaller. (**Outils / Extensions et mises à jour**, ou tapez **Extensions** dans la fenêtre de **lancement rapide** ). La boîte de dialogue affiche également les mises à jour des exemples et extensions installés. Vous pouvez également télécharger des extensions à partir de sites web ou les obtenir auprès d'autres développeurs.  

> [!NOTE]
>  À compter de Visual Studio 2015, les extensions hébergées dans Visual Studio Marketplace sont automatiquement mises à jour.  Vous pouvez modifier ce paramètre via la boîte de dialogue **Extensions et mises à jour** .  Pour plus d'informations, consultez la section relative aux **mises à jour d'extensions automatiques** , ci-dessous.  

## <a name="finding-visual-studio-extensions"></a>Recherche d’extensions Visual Studio  
 Vous pouvez installer des extensions à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Ces extensions peuvent être des contrôles, des exemples, des modèles, des outils ou d'autres composants qui ajoutent des fonctionnalités à Visual Studio. Visual Studio prend en charge les extensions sous la forme de packages VSIX (ceux-ci incluent des modèles de projet, des modèles d'élément, des éléments de **boîte à outils** , des composants MEF (Managed Extension Framework) et des VSPackages). Vous pouvez également télécharger et installer les extensions basées sur Microsoft Installer (MSI), mais la boîte de dialogue **Extensions et mises à jour** ne peut pas les activer ni les désactiver. Visual Studio Marketplace contient des extensions VSIX et MSI.  

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Installation ou désinstallation d’extensions Visual Studio  
 Dans la boîte de dialogue **Extensions et mises à jour**, recherchez l'extension à installer. (Si vous connaissez le nom ou une partie du nom de l’extension, vous pouvez effectuer une recherche dans la fenêtre **Rechercher**.) Cliquez sur **Télécharger**.  L’installation de l’extension est planifiée. Votre extension sera installée après la fermeture de toutes les instances de Visual Studio.

 Si vous essayez d'installer une extension qui a des dépendances, le programme d'installation vérifie si elles sont déjà installées. Si elles ne sont pas installées, la boîte de dialogue **Extensions et mises à jour** donne la liste des dépendances qui doivent être installées avant que vous puissiez installer l'extension.  

 Si vous souhaitez cesser d'utiliser une extension, vous pouvez la désactiver ou la désinstaller. La désactivation d'une extension maintient l'extension installée mais elle n'est pas chargée. Vous pouvez désactiver uniquement les extensions VSIX. Les extensions qui ont été installées à l'aide d'un fichier MSI peuvent uniquement être désinstallées. Recherchez l'extension et cliquez sur **Désinstaller** ou **Désactiver**. Pour décharger une extension désactivée, vous devez redémarrer Visual Studio.  

## <a name="per-user-and-administrative-extensions"></a>Extensions par utilisateur et d'administration  
 La plupart des extensions sont des extensions par utilisateur, qui sont installées dans le dossier **%LocalAppData%\Microsoft\VisualStudio\\<version de Visual Studio\>\Extensions\\**. Certaines extensions sont des extensions d’administration, installées dans le dossier **\<dossier d’installation de Visual Studio>\Common7\IDE\Extensions\\**.  

 Pour protéger votre système contre les extensions pouvant contenir des erreurs ou du code malveillant, vous pouvez limiter le chargement des extensions par utilisateur aux cas où Visual Studio est exécuté avec des autorisations d'utilisateur normales. Les extensions par utilisateur sont ainsi désactivées lorsque Visual Studio est exécuté avec des autorisations d'administrateur. Pour ce faire, accédez à la page d’options **Extensions et mises à jour** (**Outils / Options**, **Environnement**, **Extensions et mises à jour**, ou tapez simplement **Extension** dans la fenêtre de **lancement rapide** ). Décochez la case **Charger les extensions par utilisateur lors d'une exécution en tant qu'administrateur** , puis redémarrez Visual Studio.  

## <a name="automatic-extension-updates"></a>mises à jour d'extensions automatiques  
 Les extensions par utilisateur sont automatiquement mises à jour quand une nouvelle version est disponible pour Visual Studio Marketplace.  La nouvelle version de l'extension est détectée et installée en arrière-plan, de sorte que lors du redémarrage suivant de Visual Studio, la nouvelle version de l'extension sera exécutée.  

 Seules les extensions par utilisateur peuvent être mises à jour automatiquement.  Les extensions d’administration qui sont installées pour tous les utilisateurs ne seront pas mises à jour et vous continuez à installer manuellement les nouvelles versions dans la boîte de dialogue **Extensions et mises à jour**, via le nœud **Mises à jour**. Vous pouvez voir les extensions qui seront mises à jour automatiquement dans le volet d’informations des extensions de la boîte de dialogue **Extensions et mises à jour**.  

 Si vous voulez désactiver les mises à jour automatiques, vous pouvez désactiver cette fonctionnalité pour toutes les extensions ou uniquement pour des extensions spécifiques.  

-   Pour désactiver les mises à jour automatiques pour toutes les extensions, choisissez le lien **Changer les paramètres de vos extensions et mises à jour** dans la boîte de dialogue **Extensions et mises à jour**, puis décochez **Mettre à jour automatiquement les extensions**.  

-   Pour désactiver les mises à jour automatiques pour une extension spécifique, décochez l’option **Mettre à jour automatiquement les extensions** dans le volet d’informations de l’extension, à droite de la boîte de dialogue **Extensions et mises à jour**.  

> [!NOTE]
>  À partir de Visual Studio 2015 Update 2, vous pouvez spécifier (dans **Outils / Options / Environnement / Extensions et mises à jour**) si vous souhaitez des mises à jour automatiques pour les extensions par utilisateur, pour toutes les extensions utilisateur ou pour les deux (le paramètre par défaut).  

## <a name="extension-crash-notifications"></a>Notifications de blocage d’extension

Dans Visual Studio 2017 (version 15.3 - version préliminaire), Visual Studio vous avertit si une extension est soupçonnée d’être impliquée dans un blocage au cours d’une session précédente. Lors d’un blocage, Visual Studio stocke la pile d’exception. À son prochain démarrage, Visual Studio examine la pile en commençant par le nœud terminal et en progressant vers la base. Si Visual Studio détermine qu’un frame appartient à un module qui fait partie d’une extension installée et activée, vous recevez un message tel que :

  « Une session précédente s’est terminée de façon inattendue. Si vous désactivez l’extension 'nom_extension', vous pouvez éventuellement empêcher que des problèmes similaires se produisent. »

Vous pouvez ignorer cette notification ou effectuer l’une des actions suivantes :

-   Choisir **Désactiver cette extension**. Visual Studio désactive l’extension et vous indique si vous devez redémarrer votre système pour que la désactivation prenne effet. Vous pouvez réactiver l’extension dans la boîte de dialogue **Extensions et mises à jour** si vous le souhaitez.

-   Choisir **Ne plus afficher pour cette extension**. L’IDE n’affichera plus les notifications pour les blocages associés à cette extension, mais il affichera des notifications pour les blocages associés à d’autres extensions.

-   Choisir **En savoir plus** pour afficher cette rubrique d’aide dans votre navigateur par défaut.

-   Choisir le bouton **X** à la fin de la notification pour fermer la notification. Si la même extension est impliquée dans un blocage dans une session ultérieure, la notification s’affichera de nouveau.

> [!NOTE]
>  Une notification de blocage signifie uniquement qu’un des modules de l’extension était sur la pile pour le blocage. Cela ne signifie pas nécessairement que l’extension elle-même a provoqué le blocage. Il est possible que l’extension ait appelé du code faisant partie de Visual Studio, et que ce code a provoqué le blocage. Toutefois, la notification peut toujours être utile si le scénario qui a conduit au blocage n’est pas important pour vous. Dans ce cas, la désactivation de l’extension permet d’éviter le même blocage à l’avenir sans affecter votre productivité.


## <a name="sample-master-copies-and-working-copies"></a>Exemple de copies principales et de copies de travail  
 Lorsque vous installez un exemple en ligne, la solution est stockée dans deux emplacements :  

-   Une copie de travail est stockée dans l'emplacement que vous avez spécifié dans la boîte de dialogue **Nouveau projet** .  

-   Une copie principale distincte est stockée sur votre ordinateur.  

 Utilisez la boîte de dialogue **Extensions et mises à jour** pour effectuer les tâches suivantes, relatives aux exemples :  

-   Répertorier les copies principales des exemples que vous avez installés.  

-   Désactiver ou désinstaller la copie principale d'un exemple.  

-   Installer des packs d'exemples, qui sont des collections d'exemples se rapportant à une technologie ou une fonctionnalité.  

-   Installer différents exemples en ligne. (Vous pouvez également effectuer cette opération dans la boîte de dialogue **Nouveau projet** .)  

-   Afficher les notifications de mise à jour lorsque des modifications de code source sont publiées pour des exemples installés.  

-   Mettre à jour la copie principale d'un exemple installé lors de la réception d'une notification de mise à jour.  

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Installation sans utiliser la boîte de dialogue Extensions et mises à jour  
 Les extensions empaquetées dans des fichiers .vsix peuvent être disponibles à d’autres emplacements que Visual Studio Marketplace. La boîte de dialogue **Extensions et mises à jour** ne peut pas détecter ces fichiers, mais vous pouvez installer un fichier .vsix en double-cliquant dessus, ou en sélectionnant le fichier et en appuyant sur la touche Entrée. Après cela, suivez les instructions. Lorsque l'extension est installée, utilisez la boîte de dialogue **Extensions et mises à jour** pour l'activer, la désactiver ou la désinstaller.  

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Types d'extensions non pris en charge par la boîte de dialogue Extensions et mises à jour  
 Visual Studio prend toujours en charge les extensions installées par le programme d'installation Microsoft (MSI), mais pas via la boîte de dialogue **Extensions et mises à jour** sans modification.  

> [!TIP]
>  Si une extension MSI inclut un fichier extension.vsixmanifest, elle apparaît dans la boîte de dialogue **Extensions et mises à jour** .
