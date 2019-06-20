---
ms.openlocfilehash: 0fc18fab56f5b46ef097cdf699e4f0569dc190c9
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67256612"
---
Web Deploy 3.6 for Hosting Servers fournit des fonctionnalités de configuration supplémentaires qui permettent de créer le fichier de paramètres de publication à partir de l’IU.

1. Si Web Deploy 3.6 est déjà installé sur Windows Server, désinstallez-le via **Panneau de configuration** > **Programmes** > **Désinstaller un programme**.

2. Installez ensuite Web Deploy 3.6 for Hosting Servers sur Windows Server.

    Pour installer Web Deploy for Hosting Servers, utilisez [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Pour trouver le lien vers Web Platform Installer à partir d’IIS, sélectionnez **IIS** dans le volet gauche du Gestionnaire de serveur. Cliquez avec le bouton droit sur le serveur, puis sélectionnez **Gestionnaire des services Internet (IIS)** .)

    Dans Web Platform Installer, sous l’onglet Applications, se trouve **Web Deploy for Hosting Servers**.

3. Si vous n’avez pas encore installé les **Scripts et outils de gestion IIS**, faites-le maintenant.

    Accédez à **Sélectionner des rôles de serveurs** > **Serveur web (IIS)**  > **Outils de gestion**, sélectionnez le rôle **Scripts et outils de gestion IIS**, cliquez sur **Suivant**, puis installez le rôle.

    ![Installer les scripts et outils de gestion IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Les scripts et les outils sont nécessaires pour permettre la génération du fichier de paramètres de publication.

4. (Facultatif) Vérifiez que Web Deploy s’exécute correctement en ouvrant **Panneau de configuration > Système et sécurité > Outils d’administration > Services**, puis en vérifiant que le **Service de l’agent de déploiement web** est en cours d’exécution (le nom du service est différent dans les anciennes versions).

    Si le service de l’agent n’est pas en cours d’exécution, démarrez-le. S’il n’est pas présent, accédez à **Panneau de configuration > Programmes > Désinstaller un programme**, recherchez **Microsoft Web Deploy\<version>** . Choisissez **Changer** l’installation et veillez à choisir **Sera installé sur le disque dur local** pour les composants Web Deploy. Effectuez les étapes relatives au changement de l’installation.