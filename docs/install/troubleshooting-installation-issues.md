---
title: "Résolution des problèmes d’installation | Microsoft Docs"
description: "Parfois, des problèmes peuvent se produire. Cette page peut vous aider en cas d’échec de l’installation ou de la mise à niveau de Visual Studio."
ms.date: 08/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: timsneath
ms.author: tims
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6f0fe07b55ae0eeb57c0cc11fed047f31966cb6e
ms.openlocfilehash: 15e3b7cf051d26b6784df13f57794f6057e4c91c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-issues"></a>Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017

## <a name="symptoms"></a>Symptômes
Quand vous essayez d’installer ou de mettre à jour Visual Studio 2017, l’opération échoue.

## <a name="workaround"></a>Solution de contournement
Pour contourner ce problème, effectuez les étapes suivantes.

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Étape 1 : Vérifier si ce problème est un problème connu
Il existe certains problèmes connus avec le programme d’installation de Visual Studio que Microsoft s’emploie à résoudre. Consultez la [section Problèmes connus des notes de publication](https://www.visualstudio.com/news/releasenotes/vs2017-knownissues) pour déterminer s’il existe une solution de contournement à votre problème.

### <a name="step-2---check-with-the-developer-community"></a>Étape 2 : Vérifier auprès de la communauté de développeurs
Effectuez une recherche à partir de votre message d’erreur auprès de la [Communauté de développeurs Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). D’autres membres de la communauté ont peut-être documenté une solution à votre problème.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Étape 3 : Supprimer le répertoire du programme d’installation de Visual Studio pour résoudre les problèmes de mise à niveau
Le programme d’amorçage du programme d’installation de Visual Studio est un exécutable léger minimal qui installe le reste du programme d’installation de Visual Studio. La suppression des fichiers du programme d’installation de Visual Studio, puis la réexécution du programme d’amorçage peuvent résoudre certains échecs de mise à jour.

**Remarque :** Effectuer les actions suivantes réinstalle les fichiers de Visual Studio Installer et réinitialise les métadonnées d’installation.

1. Fermez le programme d’installation de Visual Studio.
2. Supprimez le répertoire du programme d’installation de Visual Studio. Il s’agit généralement du répertoire C:\Program Files (x86)\Microsoft Visual Studio\Installer.
3. Exécutez le programme d’amorçage du programme d’installation de Visual Studio. Vous pouvez trouver le programme d’amorçage dans votre dossier Téléchargements sous un nom au format ```vs_[Visual Studio edition]__*.exe```. Si vous ne trouvez pas cette application, vous pouvez télécharger le programme d’amorçage en accédant à la page des [téléchargements Visual Studio](https://www.visualstudio.com/downloads/), puis en cliquant sur le bouton **Téléchargement** correspondant à votre édition de Visual Studio. Exécutez l’exécutable pour réinitialiser les métadonnées d’installation.
4. Essayez à nouveau d’installer ou de mettre à jour Visual Studio. Si le programme d’installation échoue à nouveau, passez à l’étape suivante.

### <a name="step-4---report-a-problem"></a>Étape 4 : Signaler un problème
Dans certains cas (fichiers endommagés, par exemple), il peut se révéler nécessaire de résoudre les problèmes de manière individuelle :

1. Collecter vos journaux d’installation. Consultez [Guide pratique pour obtenir les journaux d’installation Visual Studio](#how-to-get-the-visual-studio-installation-logs) ci-dessous pour plus d’informations.
2. Ouvrez le programme d’installation de Visual Studio, puis cliquez sur **Signaler un problème** pour ouvrir l’outil Commentaires sur Visual Studio.
![Vous pouvez accéder par tabulation au bouton Fournir des commentaires pour ouvrir l’outil Commentaires](media/report-a-problem.png)
3. Indiquez le titre du problème signalé et les détails pertinents. Cliquez sur **Suivant** pour accéder à la section **Pièces jointes**, puis joignez le fichier journal généré (le fichier est généralement situé à l’emplacement %TEMP%\vslogs.zip).
![Accédez par tabulation au bouton Signaler un nouveau problème, puis suivez les étapes](media/problem-report-details.png)
4. Cliquez sur **Suivant** pour vérifier le problème signalé, puis sur **Envoyer**.

### <a name="step-5---run-installcleanupexe-to-clean-up-installation-files"></a>Étape 5 : Exécuter InstallCleanup.exe pour nettoyer les fichiers d’installation
En dernier recours, vous pouvez exécuter InstallCleanup.exe, InstallCleanup.exe est un outil fourni avec Visual Studio Installer qui permet de nettoyer les fichiers d’installation. Cet outil n’effectue pas une réinstallation complète. Cet outil supprime les données en cache et d’instance pour Visual Studio 2017.

1. Fermez le programme d’installation de Visual Studio.
2. Ouvrez une invite de commandes administrateur. Pour ce faire, procédez comme suit :
   * Dans le menu **Démarrer**, cliquez sur **Exécuter** (Démarrer+R).
   * Tapez **cmd**.
   * Cliquez avec le bouton droit sur **Invite de commandes**, puis sélectionnez **Exécuter en tant qu’administrateur**.
3. Tapez le chemin complet de l’utilitaire InstallCleanup.exe, puis indiquez le commutateur de ligne de commande suivant : -f. Par défaut, le chemin de l’utilitaire est le suivant :
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```
4. Exécutez à nouveau le programme d’amorçage dans [Étape 3 : supprimer le répertoire de Visual Studio Installer pour résoudre les problèmes de mise à niveau](#step-3--delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
5. Essayez à nouveau d’installer ou de mettre à jour Visual Studio.

## <a name="how-to-troubleshoot-an-offline-installer"></a>Comment résoudre les problèmes d’un programme d’installation hors connexion
Voici un tableau susceptible de vous aider qui présente des problèmes connus et certaines solutions de contournement lors de l’installation à partir d’une disposition locale.

| Problème       | Élément                   | Solution |
| ----------- | ---------------------- | -------- |
| Les utilisateurs n’ont pas accès aux fichiers. | autorisations (ACL) | Vérifiez que vous ajustez les autorisations (ACL) de sorte qu’elles accordent un accès en lecture aux autres utilisateurs *avant* de partager l’installation hors connexion. |
| L’installation des nouvelles charges de travail, langues et des nouveaux composants a échoué.  | `--layout`  | Assurez-vous d’avoir un accès Internet si vous installez depuis une disposition partielle et sélectionnez des charges de travail, composants ou langues non téléchargés préalablement dans cette disposition partielle. |

## <a name="how-to-get-the-visual-studio-installation-logs"></a>Guide pratique pour obtenir les journaux d’installation Visual Studio
Les journaux d’installation sont nécessaires pour résoudre la plupart des problèmes d’installation. Lorsque vous envoyez un problème à l’aide de [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) dans Visual Studio Installer, ces journaux sont automatiquement inclus dans votre rapport.

Si vous contactez le Support Microsoft, vous devrez peut-être fournir ces fichiers journaux d’installation à l’aide de [l’outil de collecte des journaux Microsoft Visual Studio et .NET Framework](https://aka.ms/vscollect). L’outil de collecte des journaux permet de collecter des journaux d’installation à partir de tous les composants installés par Visual 2017 Studio, y compris .NET Framework, Kit SDK Windows et SQL Server. Il permet également de collecter des informations sur l’ordinateur, un inventaire de Windows Installer et des informations du journal des événements Windows pour Visual Studio Installer, le programme d’installation de Windows et la restauration du système.

Pour collecter les journaux

1. [Télécharger l’outil](https://aka.ms/vscollect).
2. Ouvrez une invite de commandes d’administration.
3. Exécutez Collect.exe à partir du répertoire dans lequel vous avez enregistré l’outil.
4. Recherchez le fichier Vslogs.zip résultant dans votre répertoire %TEMP%, par exemple, C:\Users\YourName\AppData\Local\Temp\vslogs.zip.

> [!NOTE]
> L’outil doit être exécuté sous le même compte utilisateur que l’installation défaillante. Si vous exécutez l’outil à partir d’un autre compte utilisateur, définissez l’option – utilisateur :\<nom\> permettant de spécifier le compte utilisateur sous lequel l’installation défaillante a été exécutée. Exécutez `Collect.exe -?` à partir d’une invite de commandes d’administration pour des options supplémentaires et des informations d’utilisation.

