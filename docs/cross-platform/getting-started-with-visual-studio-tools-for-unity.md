---
title: Bien démarrer avec Visual Studio Tools pour Unity | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2020
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: indiesaudi
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a8f3e183bd72e9894eae55a5ed7c4f9322d44953
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250097"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Bien démarrer avec Outils Visual Studio pour Unity

## <a name="install-visual-studio"></a>Installer Visual Studio

### <a name="unity-bundled-installation"></a>Installation collective de Unity

À partir de Unity 2018.1, Visual Studio est l’éditeur de scripts C# par défaut pour Unity. Il est inclus dans l’Assistant Téléchargement Unity, ainsi que dans l’outil d’installation Unity Hub.

- Téléchargez Unity à partir de [store.unity.com](https://store.unity.com/).

Lors de l’installation, vérifiez que Visual Studio est coché dans la liste des composants à installer avec Unity :

#### <a name="unity-hub"></a>Unity Hub

:::moniker range="vs-2017"
![installation de unity hub](media/vs-2017/vstu-unity-hub.png)
:::moniker-end
:::moniker range=">=vs-2019"
![installation de unity hub](media/vs-2019/vstu-unity-hub.png)
:::moniker-end

:::moniker range="vs-2017"

#### <a name="unity-download-assistant"></a>Assistant Téléchargement de Unity

![installation de l’assistant téléchargement de Unity](media/vs-2017/vstu-download-assistant.png)

La version de Visual Studio fournie avec l’installation de Unity n’est pas toujours la plus récente. Si vous êtes invité à installer Visual Studio 2017, nous vous recommandons d’installer manuellement une version plus récente de Visual Studio.
:::moniker-end

### <a name="manual-installation"></a>Installation manuelle

Si vous avez déjà installé Visual Studio, ou si vous préférez installer manuellement, exécutez le programme d’installation de Visual Studio.

1. [Téléchargez le programme d’installation de Visual Studio](../install/install-visual-studio.md), ou ouvrez-le s’il est déjà installé.

1. Cliquez sur **Modifier** (s’il est déjà installé) ou **Installer** (pour les nouvelles installations) sur la version souhaitée de Visual Studio.

1. Dans l’onglet **Charges de travail**, faites défiler la page jusqu’à la section **Mobile et jeux** et sélectionnez la charge de travail **Développement de jeux avec Unity**.

   :::moniker range="vs-2017"
   ![Charge de travail Unity](media/vs-2017/vstu-unity-workload.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Charge de travail Unity](media/vs-2019/vstu-unity-workload.png)
   :::moniker-end

1. Cliquez sur **Modifier** (si elle est déjà installée) ou **Installer** (pour les nouvelles installations) en bas à droite de la fenêtre du programme d’installation.

#### <a name="check-for-updates-to-visual-studio"></a>Rechercher des mises à jour de Visual Studio

Il est recommandé de vérifier les mises à jour dans Visual Studio pour vous assurer que vous avez accès aux outils et fonctionnalités les plus récents. Cela n’interrompt pas votre projet Unity.

- [Mettre à jour Visual Studio 2017](../install/update-visual-studio.md)

## <a name="configure-unity-for-use-with-visual-studio"></a>Configurer Unity pour l’utiliser avec Visual Studio

À partir de Unity 2018.1, Visual Studio doit être l’éditeur de script externe par défaut dans Unity. Vous pouvez vérifier cela ou choisir une version en particulier de Visual Studio comme éditeur de scripts externe :

1. Sélectionnez **Préférences** dans le menu **Modifier**.

   :::moniker range="vs-2017"
   ![Sélectionner Préférences](media/vs-2017/vstu-unity-preferences.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Sélectionner Préférences](media/vs-2019/vstu-unity-preferences.png)
   :::moniker-end

2. Dans la boîte de dialogue Préférences, sélectionnez l’onglet **Outils externes**.

3. Dans la liste déroulante **Éditeur de scripts externe**, choisissez la version de Visual Studio de votre choix si elle apparaît ; sinon, sélectionnez **Parcourir…**.

   :::moniker range="vs-2017"
   ![Sélectionner Visual Studio](media/vs-2017/vstu-unity-external-tools.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Sélectionner Visual Studio](media/vs-2019/vstu-unity-external-tools.png)
   :::moniker-end

4. Si **Parcourir…** a été sélectionné, accédez au répertoire **Common7/IDE** à l’intérieur de votre répertoire d’installation de Visual Studio, puis sélectionnez **devenv.exe**. Cliquez ensuite sur **Ouvrir**.

   :::moniker range="vs-2017"
   ![Sélectionner Ouvrir](media/vs-2017/vstu-browse-for-application.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Sélectionner Ouvrir](media/vs-2019/vstu-browse-for-application.png)
   :::moniker-end

5. Une fois Visual Studio sélectionné dans la liste **Éditeur de scripts externe**, vérifiez que la case **Attachement de l’éditeur** est cochée.

6. Fermez la boîte de dialogue **Préférences** pour terminer le processus de configuration.

## <a name="support-for-older-versions"></a>Prise en charge des versions antérieures

Téléchargez et installez les Outils Visual Studio pour Unity sur Visual Studio Marketplace. Vous devez installer le package approprié à votre version de Visual Studio.

- Pour Visual Studio Community 2015, Visual Studio Professional 2015 ou Visual Studio Enterprise 2015 :

   [Télécharger Visual Studio 2015 Tools pour Unity](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Les Outils Visual Studio pour Unity exigent Unity 5.2 ou une version ultérieure, ainsi qu’une version de Visual Studio qui prend en charge les extensions, comme Visual Studio Community, Professional, Premium ou Enterprise. Pour vérifier que les Outils Visual Studio pour Unity sont activés dans votre installation de Unity, sélectionnez **À propos de Unity** dans le menu **Aide** et recherchez le texte « Outils Microsoft Visual Studio pour Unity activés » en bas à gauche de la boîte de dialogue.
> ![À propos de Unity](media/vs-2019/vstu-about-unity.png)

## <a name="next-steps"></a>Étapes suivantes

 Pour savoir comment manipuler et déboguer votre projet Unity dans Visual Studio, consultez [Outils Visual Studio pour Unity](../cross-platform/using-visual-studio-tools-for-unity.md).
