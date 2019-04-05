---
ms.openlocfilehash: 69f4f4c2b55670d510652b44a203b9f0eafcc53a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "57874488"
---

1. Fermez et rouvrez la console de gestion IIS pour afficher les options de configuration mises à jour dans l’IU.

2. Dans IIS, cliquez avec le bouton droit sur le **site web par défaut**, choisissez **Déployer** > **Activer la publication Web Deploy**.

    ![Configurer la configuration Web Deploy](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

3. Dans la boîte de dialogue **Activer la publication Web Deploy**, examinez les paramètres.

4. Cliquez sur **Configurer**.

    Dans le panneau **Résultats**, la sortie indique que les droits d’accès sont accordés à l’utilisateur spécifié et qu’un fichier ayant l’extension *.publishsettings* a été généré à l’emplacement indiqué dans la boîte de dialogue.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    En fonction de votre configuration Windows Server et IIS, vous voyez des valeurs distinctes dans le fichier XML. Voici quelques détails sur les valeurs que vous voyez :

   * Le fichier *msdeploy.axd* référencé dans l’attribut `publishUrl` est un fichier de gestionnaire HTTP généré dynamiquement pour Web Deploy. (À des fins de test, `http://myhostname:8172` fonctionne également, en règle générale.)
   * Le port `publishUrl` a la valeur 8172, ce qui correspond au port par défaut de Web Deploy.
   * Le port `destinationAppUrl` a la valeur 80, ce qui correspond au port par défaut d’IIS.
   * Si vous ne parvenez pas à vous connecter à l’hôte distant dans Visual Studio à l’aide du nom d’hôte (dans les étapes qui suivent), testez l’adresse IP à la place du nom d’hôte.

     > [!NOTE]
     > Si vous publiez sur IIS, sur une machine virtuelle Azure, vous devez ouvrir les ports Web Deploy et IIS dans le groupe Sécurité réseau. Pour plus d’informations, consultez [Installer et exécuter IIS](/azure/virtual-machines/windows/quick-create-portal#install-web-server).

5. Copiez ce fichier sur l’ordinateur où vous exécutez Visual Studio.
