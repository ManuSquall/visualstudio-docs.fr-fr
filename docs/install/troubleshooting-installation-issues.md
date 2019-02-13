---
title: Résoudre les problèmes d’installation ou de mise à niveau
description: Parfois, des problèmes peuvent se produire. Cette page peut vous aider en cas d’échec de l’installation ou de la mise à niveau de Visual Studio.
ms.date: 08/01/2018
ms.custom: seodec18
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edb6d9133fdf3a2a7a4109b9f438f86cc0cdec61
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931570"
---
# <a name="troubleshoot-visual-studio-2017-installation-and-upgrade-issues"></a>Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017

> [!IMPORTANT]
> Vous rencontrez un problème d’installation ? Nous pouvons vous aider. Nous proposons une option de support [**Conversation en direct**](https://visualstudio.microsoft.com/vs/support/#talktous) (en anglais uniquement).

Ce guide de résolution des problèmes inclut des instructions détaillées qui doivent permettre de résoudre la plupart des problèmes d’installation.

## <a name="how-to-troubleshoot-an-online-installation"></a>Guide pratique pour résoudre les problèmes liés à une installation en ligne

Les étapes suivantes sont optimisées pour une installation en ligne classique. Pour tout problème affectant une installation hors connexion, consultez [Guide pratique pour résoudre les problèmes liés à une installation hors connexion](#how-to-troubleshoot-an-offline-installation).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Étape 1 : Vérifier si ce problème est un problème connu

Il existe certains problèmes connus avec le programme d’installation de Visual Studio que Microsoft s’emploie à résoudre. Pour savoir s’il existe une solution de contournement à votre problème, consultez la [section Problèmes connus des notes de publication](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

### <a name="step-2---check-with-the-developer-community"></a>Étape 2 : Vérifier auprès de la communauté de développeurs

Effectuez une recherche à partir de votre message d’erreur auprès de la [Communauté de développeurs Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). D’autres membres de la communauté ont peut-être une solution documentée à votre problème.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Étape 3 : Supprimer le répertoire du programme d’installation de Visual Studio pour résoudre les problèmes de mise à niveau

Le programme d’amorçage du programme d’installation de Visual Studio est un exécutable léger minimal qui installe le reste du programme d’installation de Visual Studio. La suppression des fichiers du programme d’installation de Visual Studio, puis la réexécution du programme d’amorçage peuvent résoudre certains échecs de mise à jour.

> [!NOTE]
> Effectuer les actions suivantes réinstalle les fichiers de Visual Studio Installer et réinitialise les métadonnées d’installation.

1. Fermez le programme d’installation de Visual Studio.
2. Supprimez le répertoire du programme d’installation de Visual Studio. En règle générale, le répertoire est `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Exécutez le programme d’amorçage du programme d’installation de Visual Studio. Vous pouvez trouver le programme d’amorçage dans votre dossier Téléchargements sous un nom respectant le modèle `vs_[Visual Studio edition]__*.exe`. Si vous ne trouvez pas cette application, vous pouvez télécharger le programme d’amorçage en accédant à la page des [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), puis en cliquant sur le bouton **Téléchargement** correspondant à votre édition de Visual Studio. Exécutez ensuite l’exécutable pour réinitialiser vos métadonnées d’installation.
4. Essayez à nouveau d’installer ou de mettre à jour Visual Studio. Si le programme d’installation échoue à nouveau, passez à l’étape suivante.

### <a name="step-4---report-a-problem"></a>Étape 4 : Signaler un problème

Dans certaines situations (fichiers endommagés, par exemple), vous devrez peut-être examiner les problèmes au cas par cas. Pour que nous puissions vous aider, effectuez les actions suivantes :

1. Collecter vos journaux d’installation. Pour plus d’informations, consultez [Guide pratique pour obtenir les journaux d’installation Visual Studio](#how-to-get-visual-studio-installation-logs).
2. Ouvrez le programme d’installation de Visual Studio, puis cliquez sur **Signaler un problème** pour ouvrir l’outil Commentaires sur Visual Studio.
![Vous pouvez accéder par tabulation au bouton Fournir des commentaires pour ouvrir l’outil Commentaires](media/report-a-problem.png)
3. Indiquez le titre du problème signalé et les détails pertinents. Cliquez sur **Suivant** pour accéder à la section **Pièces jointes**, puis joignez le fichier journal généré (le fichier est généralement situé à l’emplacement `%TEMP%\vslogs.zip`).
4. Cliquez sur **Suivant** pour vérifier le problème signalé, puis sur **Envoyer**.

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>Étape 5 : Exécuter InstallCleanup.exe pour nettoyer les fichiers d’installation

En dernier recours, vous pouvez [désinstaller Visual Studio](remove-visual-studio.md) pour supprimer tous les fichiers d’installation et les informations produit.

1. Suivez les instructions de la rubrique [Supprimer Visual Studio](remove-visual-studio.md).
2. Exécutez à nouveau le programme d’amorçage dans [Étape 3 : supprimer le répertoire de Visual Studio Installer pour résoudre les problèmes de mise à niveau](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Essayez à nouveau d’installer ou de mettre à jour Visual Studio.

### <a name="step-6---contact-us-optional"></a>Étape 6 : Nous contacter (facultatif)

Si aucune des étapes précédentes ne vous permet d’installer ou de mettre à niveau Visual Studio correctement, contactez-nous via notre option de support [**Conversation en direct**](https://visualstudio.microsoft.com/vs/support/#talktous) (en anglais uniquement) pour obtenir une assistance supplémentaire.

## <a name="how-to-troubleshoot-an-offline-installation"></a>Guide pratique pour résoudre les problèmes liés à une installation hors connexion

Voici un tableau des problèmes connus et de certaines solutions de contournement qui peuvent vous aider quand vous effectuez une installation dans une topologie locale.

| Problème       | Élément                   | Solution |
| ----------- | ---------------------- | -------- |
| Les utilisateurs n’ont pas accès aux fichiers. | autorisations (ACL) | Vérifiez que vous ajustez les autorisations (ACL) de sorte qu’elles accordent un accès en lecture aux autres utilisateurs *avant* de partager l’installation hors connexion. |
| L’installation des nouvelles charges de travail, langues et des nouveaux composants a échoué.  | `--layout`  | Assurez-vous d’avoir un accès Internet si vous installez depuis une disposition partielle et sélectionnez des charges de travail, composants ou langues non téléchargés préalablement dans cette disposition partielle. |

## <a name="how-to-get-visual-studio-installation-logs"></a>Guide pratique pour obtenir les journaux d’installation de Visual Studio

Les journaux d’installation sont nécessaires pour résoudre la plupart des problèmes d’installation. Lorsque vous envoyez un problème à l’aide de [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) dans Visual Studio Installer, ces journaux sont automatiquement inclus dans votre rapport.

Si vous contactez le Support Microsoft, vous devrez peut-être fournir ces journaux d’installation à l’aide de l’outil [Microsoft Visual Studio and .NET Framework Log Collection Tool](https://aka.ms/vscollect). L’outil de collecte des journaux permet de collecter des journaux d’installation à partir de tous les composants installés par Visual 2017 Studio, y compris .NET Framework, Kit SDK Windows et SQL Server. Il permet également de collecter des informations sur l’ordinateur, un inventaire de Windows Installer et des informations du journal des événements Windows pour Visual Studio Installer, le programme d’installation de Windows et la restauration du système.

Pour collecter les journaux :

1. [Télécharger l’outil](https://aka.ms/vscollect).
2. Ouvrez une invite de commandes d’administration.
3. Exécutez `Collect.exe` à partir du répertoire dans lequel vous avez enregistré l’outil.
4. Le fichier `vslogs.zip` résultant se trouve dans le répertoire `%TEMP%`, par exemple, `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`.

> [!NOTE]
> L’outil doit être exécuté sous le même compte utilisateur que l’installation défaillante. Si vous exécutez l’outil à partir d’un autre compte utilisateur, définissez l’option `–user:<name>` permettant de spécifier le compte utilisateur sous lequel l’installation défaillante a été exécutée. Exécutez `Collect.exe -?` à partir d’une invite de commandes d’administration pour des options supplémentaires et des informations d’utilisation.

## <a name="get-live-help"></a>Obtenir de l’aide en direct

Si les solutions listées dans ce guide de résolution des problèmes ne vous permettent pas d’installer ou de mettre à niveau Visual Studio correctement, utilisez notre option de support [**Conversation en direct**](https://visualstudio.microsoft.com/vs/support/#talktous) (en anglais uniquement) pour obtenir une assistance supplémentaire.

## <a name="see-also"></a>Voir aussi

* [Supprimer Visual Studio 2017](remove-visual-studio.md)
* [Installer et utiliser Visual Studio et les services Azure derrière un pare-feu ou un serveur proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Outils de détection et de gestion des instances de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
