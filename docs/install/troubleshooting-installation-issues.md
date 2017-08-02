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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: d9de84bed187c62962a76424aabdc5f355dff4dc
ms.openlocfilehash: e6c301a7b784c5966d4f7216e67067ef6ce3ed70
ms.contentlocale: fr-fr
ms.lasthandoff: 05/15/2017

---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-issues"></a>Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017

## <a name="symptoms"></a>Symptômes
Quand vous essayez d’installer ou de mettre à jour Microsoft Visual Studio 2017, l’opération échoue.

## <a name="workaround"></a>Solution de contournement
Pour contourner ce problème, effectuez les étapes suivantes.

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Étape 1 : Vérifier si ce problème est un problème connu
Il existe certains problèmes connus avec le programme d’installation de Visual Studio que Microsoft s’emploie à résoudre. Consultez la [section Problèmes connus des notes de publication](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#KIinstall) pour déterminer s’il existe une solution de contournement à votre problème.

### <a name="step-2---check-with-the-developer-community"></a>Étape 2 : Vérifier auprès de la communauté de développeurs
Recherchez votre message d’erreur sur la [communauté de développeurs Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html. D’autres membres de la communauté ont peut-être documenté une solution à votre problème.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Étape 3 : Supprimer le répertoire du programme d’installation de Visual Studio pour résoudre les problèmes de mise à niveau
Le programme d’amorçage du programme d’installation de Visual Studio est un exécutable léger minimal qui installe le reste du programme d’installation de Visual Studio. La suppression des fichiers du programme d’installation de Visual Studio, puis la réexécution du programme d’amorçage peuvent résoudre certains échecs de mise à jour. Pour ce faire, procédez comme suit :

1. Fermez le programme d’installation de Visual Studio.
2. Supprimez le répertoire du programme d’installation de Visual Studio. Il s’agit généralement du répertoire C:\Program Files (x86)\Microsoft Visual Studio\Installer.
3. Exécutez le programme d’amorçage du programme d’installation de Visual Studio. Vous pouvez trouver le programme d’amorçage dans votre dossier Téléchargements sous un nom au format ```vs_[Visual Studio edition]__*.exe```. Si vous ne trouvez pas cette application, vous pouvez télécharger le programme d’amorçage en accédant à la page des [téléchargements Visual Studio](https://www.visualstudio.com/downloads/), puis en cliquant sur le bouton de **téléchargement** correspondant à votre édition de Visual Studio. Exécutez cet exécutable pour réinitialiser les métadonnées d’installation.
4. Essayez à nouveau d’installer ou de mettre à jour Visual Studio. Si le programme d’installation échoue à nouveau, passez directement à l’étape 4 ci-dessous.
<br/>**Remarque :** Cette étape réinstalle les fichiers du programme d’installation de Visual Studio et réinitialise les métadonnées d’installation.

### <a name="step-4---report-a-problem"></a>Étape 4 : Signaler un problème
Dans certains cas (fichiers endommagés, par exemple), il peut se révéler nécessaire de résoudre les problèmes de manière individuelle :

1. Téléchargez l’outil [Microsoft Visual Studio and .NET Framework Log Collection Tool](https://www.microsoft.com/en-us/download/details.aspx?id=12493), puis exécutez-le. Cet outil collecte et compile les journaux d’installation disponibles pour les installations de Visual Studio, .NET Framework et SQL Server.
2. Ouvrez le programme d’installation de Visual Studio, puis cliquez sur **Signaler un problème** pour ouvrir l’outil Commentaires sur Visual Studio.
![Vous pouvez accéder par tabulation au bouton Fournir des commentaires pour ouvrir l’outil Commentaires](~/install/media/report-a-problem.png)
3. Indiquez le titre du problème signalé et les détails pertinents. Cliquez sur **Suivant** pour accéder à la section **Pièces jointes**, puis joignez le fichier journal généré (le fichier est généralement situé à l’emplacement %TEMP%\vslogs.zip).
![Accédez par tabulation au bouton Signaler un nouveau problème, puis suivez les étapes](~/install/media/problem-report-details.png)
4. Cliquez sur **Suivant** pour vérifier le problème signalé, puis sur **Envoyer**.

### <a name="step-5---run-installcleanupexe-to-clean-up-installation-files"></a>Étape 5 : Exécuter InstallCleanup.exe pour nettoyer les fichiers d’installation
En dernier recours, vous pouvez exécuter InstallCleanup.exe, un utilitaire fourni avec le programme d’installation de Visual Studio qui permet de nettoyer les fichiers d’installation. Il ne s’agit pas d’une réinstallation complète. Cet utilitaire supprime les données en cache et d’instance pour Visual Studio 2017.

1. Fermez le programme d’installation de Visual Studio.
2. Ouvrez une invite de commandes administrateur. Pour ce faire, procédez comme suit :
   * Dans le menu **Démarrer**, cliquez sur **Exécuter** (Démarrer+R).
   * Tapez **cmd**.
   * Cliquez avec le bouton droit sur **Invite de commandes**, puis sélectionnez **Exécuter en tant qu’administrateur**.
3. Tapez le chemin complet de l’utilitaire InstallCleanup.exe, puis indiquez le commutateur de ligne de commande suivant : -f. Par défaut, le chemin de l’utilitaire est le suivant :
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

