---
title: "Résolution des problèmes d’installation | Microsoft Docs"
description: "Parfois, des problèmes peuvent se produire. Cette page peut vous aider en cas d’échec de l’installation ou de la mise à niveau de Visual Studio."
ms.date: 04/14/2017
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
ms.sourcegitcommit: 89f86a5935ad283ef5c0e29ea2db0ae22cf603a8
ms.openlocfilehash: 0fd361edd5bc5056f09c64aa4499a10a50656546
ms.contentlocale: fr-fr
ms.lasthandoff: 08/07/2017

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

1. Téléchargez l’outil [Microsoft Visual Studio and .NET Framework Log Collection Tool](https://aka.ms/vscollect), puis exécutez-le. Cet outil collecte et compile les journaux d’installation disponibles pour les installations de Visual Studio, .NET Framework et SQL Server.
2. Ouvrez le programme d’installation de Visual Studio, puis cliquez sur **Signaler un problème** pour ouvrir l’outil Commentaires sur Visual Studio.
![Vous pouvez accéder par tabulation au bouton Fournir des commentaires pour ouvrir l’outil Commentaires](media/report-a-problem.png)
3. Indiquez le titre du problème signalé et les détails pertinents. Cliquez sur **Suivant** pour accéder à la section **Pièces jointes**, puis joignez le fichier journal généré (le fichier est généralement situé à l’emplacement %TEMP%\vslogs.zip).
![Accédez par tabulation au bouton Signaler un nouveau problème, puis suivez les étapes](media/problem-report-details.png)
4. Cliquez sur **Suivant** pour vérifier le problème signalé, puis sur **Envoyer**.

### <a name="step-5---run-installcleanupexe-to-clean-up-installation-files"></a>Étape 5 : Exécuter InstallCleanup.exe pour nettoyer les fichiers d’installation
En dernier recours, vous pouvez exécuter InstallCleanup.exe, un utilitaire fourni avec le programme d’installation de Visual Studio qui permet de nettoyer les fichiers d’installation. Il ne s’agit pas d’une réinstallation complète. Cet utilitaire supprime les données en cache et d’instance pour Visual Studio 2017.

1. Fermez le programme d’installation de Visual Studio.
2. Ouvrez une invite de commandes administrateur. Pour ce faire, procédez comme suit :
   * Dans le menu **Démarrer**, cliquez sur **Exécuter** (Démarrer+R).
   * Tapez **cmd**.
   * Cliquez avec le bouton droit sur **Invite de commandes**, puis sélectionnez **Exécuter en tant qu’administrateur**.
3. Tapez le chemin complet de l’utilitaire InstallCleanup.exe, puis indiquez le commutateur de ligne de commande suivant : -f. Par défaut, le chemin de l’utilitaire est le suivant :
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```
4. Réexécutez le programme d’amorçage décrit à l’étape 3.
5. Essayez à nouveau d’installer ou de mettre à jour Visual Studio.

## <a name="how-to-troubleshoot-an-offline-installer"></a>Comment résoudre les problèmes d’un programme d’installation hors connexion
Voici un tableau susceptible de vous aider qui présente des problèmes connus et certaines solutions de contournement lors de l’installation à partir d’une disposition locale.

| Problème       | Élément                   | Solution |
| ----------- | ---------------------- | -------- |
| Les utilisateurs n’ont pas accès aux fichiers. | autorisations (ACL) | Vérifiez que vous ajustez les autorisations (ACL) de sorte qu’elles accordent un accès en lecture aux autres utilisateurs *avant* de partager l’installation hors connexion. |
| L’installation des nouvelles charges de travail, langues et des nouveaux composants a échoué.  | `--layout`  | Si vous effectuez l’installation à partir d’une disposition partielle et que vous sélectionnez des charges de travail, des composants ou des langues qui ne sont pas disponibles dans la disposition précédente, vérifiez que vous disposez d’une connexion à Internet. |

