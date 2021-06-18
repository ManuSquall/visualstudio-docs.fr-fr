---
title: Résoudre les problèmes d’installation ou de mise à niveau
description: Parfois, des problèmes peuvent se produire. Cette page peut vous aider en cas d’échec de l’installation ou de la mise à niveau de Visual Studio.
ms.date: 06/24/2020
ms.custom: acquisition
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e0bc092663cc0e100598f991ae1b2a18a4b94501
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306863"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Résolution des problèmes d’installation et de mise à niveau de Visual Studio

> [!IMPORTANT]
> Vous rencontrez un problème d’installation ? Nous pouvons vous aider. Nous offrons une option de prise en charge de [**conversation d’installation**](https://visualstudio.microsoft.com/vs/support/#talktous) (en anglais uniquement).

Ce guide de résolution des problèmes inclut des instructions détaillées qui doivent permettre de résoudre la plupart des problèmes d’installation.

## <a name="online-installations"></a>Installations en ligne

Les étapes suivantes sont optimisées pour une installation en ligne classique. Pour tout problème affectant une installation hors connexion, consultez [Guide pratique pour résoudre les problèmes liés à une installation hors connexion](#offline-installations).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Étape 1 : Vérifier si ce problème est un problème connu

::: moniker range="vs-2017"

Il existe certains problèmes connus avec le programme d’installation de Visual Studio que Microsoft s’emploie à résoudre. Pour savoir s’il existe une solution de contournement à votre problème, consultez la [section Problèmes connus des notes de publication](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

::: moniker-end

::: moniker range=">=vs-2019"

Il existe certains problèmes connus avec le programme d’installation de Visual Studio que Microsoft s’emploie à résoudre. Pour savoir s’il existe une solution de contournement à votre problème, consultez la [section Problèmes connus des notes de publication](/visualstudio/releases/2019/release-notes#-known-issues).

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>Étape 2-essayer de réparer Visual Studio

La réparation corrige de nombreux problèmes de mise à jour courants. Pour plus d’informations sur le moment et la façon d’utiliser la fonctionnalité de réparation dans Visual Studio, consultez [réparer Visual Studio](repair-visual-studio.md).

### <a name="step-3---check-with-the-developer-community"></a>Étape 3 : consultez la communauté des développeurs

Effectuez une recherche à partir de votre message d’erreur auprès de la [Communauté de développeurs Visual Studio](https://aka.ms/feedback/suggest?space=8). D’autres membres de la communauté ont peut-être une solution documentée à votre problème.

### <a name="step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Étape 4 : supprimer le répertoire Visual Studio Installer pour résoudre les problèmes de mise à niveau

Le programme d’amorçage du programme d’installation de Visual Studio est un exécutable léger minimal qui installe le reste du programme d’installation de Visual Studio. La suppression des fichiers du programme d’installation de Visual Studio, puis la réexécution du programme d’amorçage peuvent résoudre certains échecs de mise à jour.

> [!NOTE]
> Effectuer les actions suivantes réinstalle les fichiers de Visual Studio Installer et réinitialise les métadonnées d’installation.

::: moniker range="vs-2017"

1. Fermez le programme d’installation de Visual Studio.
2. Supprimez le répertoire du programme d’installation de Visual Studio. En règle générale, le répertoire est `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Exécutez le programme d’amorçage du programme d’installation de Visual Studio. Vous pouvez trouver le programme d’amorçage dans votre dossier Téléchargements sous un nom respectant le modèle `vs_[Visual Studio edition]__*.exe`. Si vous ne trouvez pas cette application, vous pouvez télécharger le programme d’amorçage en accédant à la page des [téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), puis en cliquant sur le bouton **Téléchargement** correspondant à votre édition de Visual Studio. Exécutez ensuite l’exécutable pour réinitialiser vos métadonnées d’installation.
4. Essayez à nouveau d’installer ou de mettre à jour Visual Studio. Si le programme d’installation échoue à nouveau, passez à l’étape suivante.

::: moniker-end

::: moniker range=">=vs-2019"

1. Fermez le programme d’installation de Visual Studio.
2. Supprimez le répertoire du programme d’installation de Visual Studio. En règle générale, le répertoire est `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Exécutez le programme d’amorçage du programme d’installation de Visual Studio. Vous pouvez trouver le programme d’amorçage dans votre dossier Téléchargements sous un nom respectant le modèle `vs_[Visual Studio edition]__*.exe`. Si vous ne trouvez pas cette application, vous pouvez télécharger le programme d’amorçage en accédant à la page des [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads), puis en cliquant sur le bouton **Téléchargement** correspondant à votre édition de Visual Studio. Exécutez ensuite l’exécutable pour réinitialiser vos métadonnées d’installation.
4. Essayez à nouveau d’installer ou de mettre à jour Visual Studio. Si le programme d’installation échoue à nouveau, passez à l’étape suivante.

::: moniker-end

### <a name="step-5---report-a-problem"></a>Étape 5-signaler un problème

Dans certaines situations (fichiers endommagés, par exemple), vous devrez peut-être examiner les problèmes au cas par cas. Pour que nous puissions vous aider, effectuez les actions suivantes :

::: moniker range="vs-2017"

1. Collecter vos journaux d’installation. Pour plus d’informations, consultez [Guide pratique pour obtenir les journaux d’installation Visual Studio](#installation-logs).
2. Ouvrez le programme d’installation de Visual Studio, puis cliquez sur **Signaler un problème** pour ouvrir l’outil Commentaires sur Visual Studio.
![Vous pouvez accéder par tabulation au bouton Fournir des commentaires pour ouvrir l’outil Commentaires](media/report-a-problem.png)
3. Indiquez le titre du problème signalé et les détails pertinents. Cliquez sur **Suivant** pour accéder à la section **Pièces jointes**, puis joignez le fichier journal généré (le fichier est généralement situé à l’emplacement `%TEMP%\vslogs.zip`).
4. Cliquez sur **Suivant** pour vérifier le problème signalé, puis sur **Envoyer**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Collecter vos journaux d’installation. Pour plus d’informations, consultez [Guide pratique pour obtenir les journaux d’installation Visual Studio](#installation-logs).
2. Ouvrez le programme d’installation de Visual Studio, puis cliquez sur **Signaler un problème** pour ouvrir l’outil Commentaires sur Visual Studio.
![Vous pouvez accéder par tabulation au bouton Fournir des commentaires pour ouvrir l’outil Commentaires](media/vs-2019/vs-installer-report-problem.png)
3. Indiquez le titre du problème signalé et les détails pertinents. Cliquez sur **Suivant** pour accéder à la section **Pièces jointes**, puis joignez le fichier journal généré (le fichier est généralement situé à l’emplacement `%TEMP%\vslogs.zip`).
4. Cliquez sur **Suivant** pour vérifier le problème signalé, puis sur **Envoyer**.

::: moniker-end

### <a name="step-6---run-installcleanupexe-to-remove-installation-files"></a>Étape 6 : exécuter InstallCleanup.exe pour supprimer les fichiers d’installation

En dernier recours, vous pouvez [désinstaller Visual Studio](remove-visual-studio.md) pour supprimer tous les fichiers d’installation et les informations produit.

1. Suivez les instructions de la rubrique [Supprimer Visual Studio](remove-visual-studio.md).
2. Réexécutez le programme d’amorçage décrit à l' [étape 4 : supprimez le répertoire Visual Studio installer pour résoudre les problèmes de mise à niveau](#step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Essayez à nouveau d’installer ou de mettre à jour Visual Studio.

### <a name="step-7---contact-us-optional"></a>Étape 7-nous contacter (facultatif)

Si aucune des étapes précédentes ne vous permet d’installer ou de mettre à niveau Visual Studio correctement, contactez-nous via notre option de support [**Conversation en direct**](https://visualstudio.microsoft.com/vs/support/#talktous) (en anglais uniquement) pour obtenir une assistance supplémentaire.

## <a name="offline-installations"></a>Installations hors connexion

Voici un tableau des problèmes connus et des solutions de contournement qui peuvent vous aider lors de la création d’une [installation hors connexion](create-an-offline-installation-of-visual-studio.md) , puis l’installation à partir d’une disposition locale.

| Problème       | Élément                   | Solution |
| ----------- | ---------------------- | -------- |
| Les utilisateurs n’ont pas accès aux fichiers. | autorisations (ACL) | Veillez à ajuster les autorisations (ACL) afin qu’elles accordent un accès en lecture à d’autres utilisateurs  *avant* de partager l’installation hors connexion. |
| L’installation des nouvelles charges de travail, langues et des nouveaux composants a échoué.  | `--layout`  | Assurez-vous d’avoir un accès Internet si vous installez depuis une disposition partielle et sélectionnez des charges de travail, composants ou langues non téléchargés préalablement dans cette disposition partielle. |

Pour plus d’informations sur la résolution des problèmes liés à une [installation réseau](create-a-network-installation-of-visual-studio.md), consultez [résoudre les erreurs liées au réseau lorsque vous installez ou utilisez Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Journaux d’installation

Les journaux d’installation sont nécessaires pour résoudre la plupart des problèmes d’installation. Lorsque vous envoyez un problème à l’aide de [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio.md) dans Visual Studio Installer, ces journaux sont automatiquement inclus dans votre rapport.

Si vous contactez le Support Microsoft, vous devrez peut-être fournir ces journaux d’installation à l’aide de l’outil [Microsoft Visual Studio and .NET Framework Log Collection Tool](https://www.microsoft.com/download/details.aspx?id=12493). L’outil de collecte des journaux permet de collecter des journaux d’installation à partir de tous les composants installés par Visual Studio, y compris .NET Framework, SDK Windows et SQL Server. Il permet également de collecter des informations sur l’ordinateur, un inventaire de Windows Installer et des informations du journal des événements Windows pour Visual Studio Installer, le programme d’installation de Windows et la restauration du système.

Pour collecter les journaux :

1. [Téléchargez l’outil](https://www.microsoft.com/download/details.aspx?id=12493).
2. Ouvrez une invite de commandes d’administration.
3. Exécutez `Collect.exe` à partir du répertoire dans lequel vous avez enregistré l’outil.
4. Le fichier `vslogs.zip` résultant se trouve dans le répertoire `%TEMP%`, par exemple, `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`.

> [!NOTE]
> L’outil doit être exécuté sous le même compte utilisateur que l’installation défaillante. Si vous exécutez l’outil à partir d’un autre compte utilisateur, définissez l’option `–user:<name>` permettant de spécifier le compte utilisateur sous lequel l’installation défaillante a été exécutée. Exécutez `Collect.exe -?` à partir d’une invite de commandes d’administration pour des options supplémentaires et des informations d’utilisation.

## <a name="live-help"></a>Aide en direct

Si les solutions listées dans ce guide de résolution des problèmes ne vous permettent pas d’installer ou de mettre à niveau Visual Studio correctement, utilisez notre option de support [**Conversation en direct**](https://visualstudio.microsoft.com/vs/support/#talktous) (en anglais uniquement) pour obtenir une assistance supplémentaire.

## <a name="see-also"></a>Voir aussi

* [Réparer Visual Studio](repair-visual-studio.md)
* [Supprimer Visual Studio](remove-visual-studio.md)
* [Installer et utiliser Visual Studio et les services Azure derrière un pare-feu ou un serveur proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Outils de détection et de gestion des instances de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
