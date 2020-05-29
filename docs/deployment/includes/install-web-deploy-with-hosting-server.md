---
ms.openlocfilehash: 1e6c6714720d652fff266e3e852d01982c98e34a
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173875"
---
Web Deploy 3.6 for Hosting Servers fournit des fonctionnalités de configuration supplémentaires qui permettent de créer le fichier de paramètres de publication à partir de l’IU.

1. Si Web Deploy 3,6 est déjà installé sur Windows Server, désinstallez-le à l’aide des programmes **du panneau**  >  **Programs**  >  **de configuration désinstaller un programme**.

2. Installez ensuite Web Deploy 3.6 for Hosting Servers sur Windows Server.

    Pour installer Web Deploy for Hosting Servers, utilisez Web Platform Installer (WebPI). (Pour trouver le lien vers Web Platform Installer à partir d’IIS, sélectionnez **IIS** dans le volet gauche du Gestionnaire de serveur. Dans le volet serveur, cliquez avec le bouton droit sur le serveur, puis sélectionnez **Gestionnaire de Internet Information Services (IIS)**. Utilisez ensuite le lien **recevoir de nouveaux composants de plateforme Web** dans la fenêtre **actions** .) Vous pouvez également obtenir le Web Platform Installer (WebPI) à partir des [téléchargements](https://www.microsoft.com/web/downloads/platform.aspx).

    Dans l’Web Platform Installer, vous trouverez **Web Deploy 3,6 pour les serveurs d’hébergement** sous l’onglet applications.

3. Si vous n’avez pas encore installé les **Scripts et outils de gestion IIS**, faites-le maintenant.

    Accédez à **Sélectionner**  >  outils de gestion**serveur Web rôles serveur (IIS)**  >  **Management Tools**, puis sélectionnez le rôle **scripts et outils de gestion IIS** , cliquez sur **suivant**, puis installez le rôle.

    ![Installer les scripts et outils de gestion IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Les scripts et les outils sont nécessaires pour permettre la génération du fichier de paramètres de publication.

4. (Facultatif) Vérifiez que Web Deploy s’exécute correctement en ouvrant **Panneau de configuration > Système et sécurité > Outils d’administration > Services**, puis en vérifiant que le **Service de l’agent de déploiement web** est en cours d’exécution (le nom du service est différent dans les anciennes versions).

    Si le service de l’agent n’est pas en cours d’exécution, démarrez-le. S’il n’est pas présent, accédez à **Panneau de configuration > Programmes > Désinstaller un programme**, recherchez **Microsoft Web Deploy\<version>**. Choisissez **Changer** l’installation et veillez à choisir **Sera installé sur le disque dur local** pour les composants Web Deploy. Effectuez les étapes relatives au changement de l’installation.