---
ms.openlocfilehash: a292b37a50bbf667fa5b23f18879cd79c3f76805
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85292058"
---
Web Deploy 3.6 for Hosting Servers fournit des fonctionnalités de configuration supplémentaires qui permettent de créer le fichier de paramètres de publication à partir de l’IU.

1. Si Web Deploy est déjà installé sur Windows Server, désinstallez-le à l’aide des programmes **du panneau**  >  **Programs**  >  **de configuration désinstaller un programme**.

2. Installez ensuite Web Deploy 3.6 for Hosting Servers sur Windows Server.

    Pour installer Web Deploy for Hosting Servers, utilisez Web Platform Installer (WebPI). (Pour trouver le lien vers Web Platform Installer à partir d’IIS, sélectionnez **IIS** dans le volet gauche du Gestionnaire de serveur. Dans le volet serveur, cliquez avec le bouton droit sur le serveur, puis sélectionnez **Gestionnaire de Internet Information Services (IIS)**. Utilisez ensuite le lien **recevoir de nouveaux composants de plateforme Web** dans la fenêtre **actions** .) Vous pouvez également obtenir le Web Platform Installer (WebPI) à partir des [téléchargements](https://www.microsoft.com/web/downloads/platform.aspx).

    Dans l’Web Platform Installer, vous trouverez **Web Deploy 3,6 pour les serveurs d’hébergement** sous l’onglet applications.

3. Si vous n’avez pas encore installé les **Scripts et outils de gestion IIS**, faites-le maintenant.

    Accédez à **Sélectionner**  >  outils de gestion**serveur Web rôles serveur (IIS)**  >  **Management Tools**, puis sélectionnez le rôle **scripts et outils de gestion IIS** , cliquez sur **suivant**, puis installez le rôle.

    ![Installer les scripts et outils de gestion IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Les scripts et les outils sont nécessaires pour permettre la génération du fichier de paramètres de publication.

4. Facultatif Vérifiez que Web Deploy s’exécute correctement en ouvrant  **le panneau de configuration > système et sécurité > outils d’administration > services**, puis assurez-vous que :

    * Le **service Web Deployment agent** est en cours d’exécution (le nom du service est différent dans les versions antérieures).

    * Le **service de gestion Web** est en cours d’exécution.

    Si l’un des services de l’agent n’est pas en cours d’exécution, redémarrez le **service Web Deployment agent**.

    Si le service Web Deployment Agent n’est pas présent, accédez à **panneau de configuration > programmes > désinstaller un programme**, recherchez **Microsoft \<version> Web Deploy **. Choisissez **Changer** l’installation et veillez à choisir **Sera installé sur le disque dur local** pour les composants Web Deploy. Effectuez les étapes relatives au changement de l’installation.