---
title: Espaces de travail distants pour R
description: Guide pratique pour configurer les espaces de travail R distants et s’y connecter à partir de Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 96078d1b2fdb5a54c912cbf214024726ce102e4e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851840"
---
# <a name="set-up-remote-workspaces"></a>Configurer des espaces de travail distants

Cet article explique comment configurer un serveur distant avec SSL et un service R approprié. Les outils R pour Visual Studio (RTVS) peuvent ainsi se connecter à un espace de travail distant sur ce serveur.

## <a name="remote-computer-requirements"></a>Spécifications de l’ordinateur distant

- Windows 10, Windows Server 2016 ou Windows Server 2012 R2. RTVS nécessite également
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) ou version supérieure

## <a name="install-an-ssl-certificate"></a>Installer un certificat SSL

RTVS nécessite que toutes les communications avec un serveur distant s’effectuent sur HTTP, ce qui implique un certificat SSL sur le serveur. Vous pouvez utiliser un certificat signé par une autorité de certification approuvée (recommandée) ou un certificat auto-signé. (Un certificat auto-signé oblige RTVS à émettre des avertissements lors de la connexion.) Dans l’un ou l’autre, vous devez l’installer sur l’ordinateur et autoriser l’accès à sa clé privée.

### <a name="obtain-a-trusted-certificate"></a>Obtenir un certificat approuvé

Un certificat approuvé est émis par une autorité de certification (consultez l’article sur les [autorités de certification sur Wikipedia](https://en.wikipedia.org/wiki/Certificate_authority) pour plus d’informations). Comme pour l’obtention d’une carte d’identité émise par l’État, l’émission d’un certificat approuvé implique plusieurs processus et des frais potentiels, mais permet de vérifier l’authenticité de la demande et du demandeur.

Le champ de clé qui doit se trouver dans le certificat est le nom de domaine complet de votre serveur R. L’autorité de certification nécessite la preuve que vous êtes autorisé à créer un serveur pour le domaine auquel il appartient.

Pour plus d’informations, consultez l’article sur les [certificats de clé publique](https://en.wikipedia.org/wiki/Public_key_certificate) sur Wikipedia.

## <a name="install-an-ssl-certificate-on-windows"></a>Installer un certificat SSL sur Windows

Le certificat SSL doit être installé manuellement sur Windows. Suivez les instructions ci-dessous pour installer un certificat SSL.

### <a name="obtain-a-self-signed-certificate-windows"></a>Obtenir un certificat auto-signé (Windows)

Ignorez cette section si vous disposez d’un certificat approuvé. Par rapport à un certificat émis par une autorité approuvée, un certificat auto-signé est comme si vous créiez vous-même votre carte d’identité. Bien évidemment, ce processus est beaucoup plus simple que de passer par une autorité approuvée, mais l’authentification obtenue est en contrepartie moins forte, ce qui signifie qu’un pirate informatique peut substituer son propre certificat au certificat non signé et ainsi capturer tout le trafic entre le client et le serveur. Par conséquent, *le certificat auto-signé doit être utilisé uniquement pour les scénarios de test, sur un réseau approuvé, et jamais en production.*

Pour cette raison, RTVS émet toujours l’avertissement suivant lors de la connexion à un serveur avec un certificat auto-signé :

![Boîte de dialogue d’avertissement de certificat auto-signé](media/workspaces-remote-self-signed-certificate-warning.png)

Pour émettre un certificat auto-signé :

1. Ouvrez une session sur le serveur R à l’aide d’un compte d’administrateur.
1. Ouvrez une nouvelle invite de commandes administrateur PowerShell et envoyez la commande suivante, en remplaçant `"remote-machine-name"` par le nom de domaine complet de votre serveur.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Si vous n’avez jamais exécuté PowerShell sur le serveur R, exécutez la commande suivante pour activer l’exécution explicite de commandes :

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Pour plus d’informations, consultez l’article sur les [certificats auto-signés](https://en.wikipedia.org/wiki/Self-signed_certificate) sur Wikipedia.

### <a name="install-the-certificate"></a>Installer le certificat

Pour installer le certificat sur l’ordinateur distant, exécutez *certlm.msc* (le gestionnaire de certificats) à partir d’une invite de commandes. Cliquez avec le bouton droit sur le dossier **Personnel** et sélectionnez la commande **Toutes les tâches** > **Importer** :

![Commande d’importation de certificat](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>Octroyer des autorisations pour lire la clé privée du certificat SSL

Une fois le certificat importé, accordez des autorisations au compte `NETWORK SERVICE` pour lire la clé privée, comme indiqué dans les instructions suivantes. `NETWORK_SERVICE` est le compte utilisé pour exécuter le répartiteur R Services, qui est le service qui met fin aux connexions SSL entrantes sur le serveur.

1. Exécutez *certlm.msc* (le gestionnaire de certificats) à partir d’une invite de commandes administrateur.
1. Développez   >  **certificats** personnels, cliquez avec le bouton droit sur votre certificat, puis sélectionnez **toutes les tâches**  >  **gérer les clés privées**.
1. Cliquez avec le bouton droit sur le certificat et sélectionnez la commande **Gérer les clés privées** sous **Toutes les tâches**.
1. Dans la boîte de dialogue qui s’affiche, sélectionnez **Ajouter** et entrez `NETWORK SERVICE` comme nom de compte :

    ![Boîte de dialogue Gérer les clés privées, ajout de NETWORK_SERVICE](media/workspaces-remote-manage-private-key-dialog.png)

1. Sélectionnez **OK** deux fois pour fermer les boîtes de dialogue et valider vos modifications.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Installer un certificat SSL sur Ubuntu

Le package `rtvs-daemon` installe un certificat auto-signé par défaut dans le cadre de l’installation.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>Obtenir un certificat auto-signé (Ubuntu)

Pour les avantages et les risques liés à l’utilisation d’un certificat auto-signé, consultez la description pour Windows. Le package `rtvs-daemon` génère et configure le certificat auto-signé lors de l’installation. Vous devez faire cela seulement si vous souhaitez remplacer le certificat auto-signé généré automatiquement.

Pour émettre vous-même un certificat auto-signé :

1. Connectez-vous directement ou via SSH à votre ordinateur Linux.
2. Installez le package `ssl-cert` :

    ```sh
    sudo apt-get install ssl-cert
    ```

3. Exécutez `make-ssl-cert` pour générer le certificat SSL auto-signé par défaut :

    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```

4. Convertissez la clé générée et les fichiers PEM en fichier PFX. Le fichier PFX généré doit se trouver dans votre dossier de base :

    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>Configurer le démon RTVS

Le chemin de fichier du certificat SSL (chemin du fichier PFX) doit être défini dans */etc/rtvs/rtvsd.config.json*. Mettez à jour `X509CertificateFile` et `X509CertificatePassword` avec respectivement le chemin du fichier et le mot de passe.

```json
{
  "logging": { "logFolder": "/tmp" },
  "security": {
    "allowedGroup": "",
    "X509CertificateFile": "/etc/rtvs/ssl-cert-snakeoil.pfx",
    "X509CertificatePassword": "SnakeOil"
  },
  "startup": { "name": "rtvsd" },
  "urls": "https://0.0.0.0:5444"
}
```

Enregistrez le fichier et redémarrez le démon : `sudo systemctl restart rtvsd`.

## <a name="install-r-services-on-windows"></a>Installer R Services sur Windows

Pour exécuter le code R, l’ordinateur distant doit avoir un interpréteur R installé comme suit :

1. Téléchargez et installez l’un des programmes suivants :

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R pour Windows](https://cran.r-project.org/bin/windows/base/)

     Ces deux programmes ont les mêmes fonctionnalités, mais Microsoft R Open bénéficie de bibliothèques d’algèbre linéaire à accélération matérielle, fournies par la bibliothèque [Intel Math Kernel Library](https://software.intel.com/intel-mkl).

2. Exécutez le [programme d’installation de R Services](https://github.com/Microsoft/RTVS/blob/master/doc/rtvsd/rtvs-remote-downloads.md) et redémarrez quand vous y êtes invité. Le programme d’installation effectue les opérations suivantes :

    - Création d’un dossier dans *%PROGRAMFILES%\Outils R pour Visual Studio\1.0\\* et copie de tous les fichiers binaires nécessaires.
    - Installation de `RHostBrokerService` et `RUserProfileService`, et configuration pour un démarrage automatique.
    - Configuration du service `seclogon` pour qu’il démarre automatiquement.
    - Ajout de *Microsoft.R.Host.exe* et *Microsoft.R.Host.Broker.exe* dans les règles de trafic entrant de pare-feu sur le port 5444 par défaut.

R Services démarre automatiquement au redémarrage de l’ordinateur :

- Le **service de répartiteur de l’hôte R** gère tout le trafic HTTPS entre Visual Studio et le processus dans lequel s’exécute le code R sur l’ordinateur.
- Le **service des profils utilisateur R** est un composant privilégié qui gère la création des profils utilisateur Windows. Ce service est appelé quand un nouvel utilisateur se connecte pour la première fois au serveur R.

Vous pouvez voir ces services dans la console de gestion des services (*compmgmt.msc*).

## <a name="install-r-services-on-linux"></a>Installer R Services sur Linux

Pour exécuter le code R, l’ordinateur distant doit avoir un interpréteur R installé comme suit :

1. Téléchargez et installez l’un des programmes suivants :

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R pour Windows](https://cran.r-project.org/bin/linux/ubuntu/)

     Ces deux programmes ont les mêmes fonctionnalités, mais Microsoft R Open bénéficie de bibliothèques d’algèbre linéaire à accélération matérielle, fournies par la bibliothèque [Intel Math Kernel Library](https://software.intel.com/intel-mkl).

2. Suivez les instructions données dans la rubrique [Remote R Service pour Linux](setting-up-remote-r-service-on-linux.md), qui concerne les ordinateurs Ubuntu physiques, les machines virtuelles Ubuntu Azure, le sous-système Windows pour Linux (WSL) et les conteneurs Docker, y compris ceux exécutés sur le référentiel Azure Container.

## <a name="configure-r-services"></a>Configurer R Services

Une fois que R Services est en cours d’exécution sur l’ordinateur distant, vous devez aussi créer des comptes d’utilisateur, définir des règles de pare-feu, configurer le réseau Azure et configurer le certificat SSL.

1. Comptes d’utilisateur : Créez des comptes pour chaque utilisateur qui accède à l’ordinateur distant. Vous pouvez créer des comptes d’utilisateur locaux standard (sans privilège), ou vous pouvez joindre votre serveur R à votre domaine et ajouter les groupes de sécurité appropriés au groupe de sécurité `Users`.

1. Règles de pare-feu : Par défaut, `R Host Broker` écoute sur le port TCP 5444. Par conséquent, vérifiez qu’il existe des règles de pare-feu Windows activées pour le trafic entrant et sortant (le trafic sortant est nécessaire pour l’installation des packages et des scénarios similaires).  Le programme d’installation de R Services définit ces règles automatiquement pour le pare-feu Windows intégré. Toutefois, si vous utilisez un pare-feu tiers, ouvrez manuellement le port 5444 pour `R Host Broker`.

1. Configuration d’Azure : Si l’ordinateur distant est une machine virtuelle sur Azure, ouvrez le port 5444 pour le trafic entrant dans le réseau Azure, qui est indépendant du pare-feu Windows. Pour plus d’informations, consultez [Filtrer le trafic réseau avec les groupes de sécurité réseau](/azure/virtual-network/virtual-networks-nsg) dans la documentation Azure.

1. Indiquer au répartiteur de l’hôte R le certificat SSL à charger : Si vous installez le certificat sur un serveur intranet, il est probable que le nom de domaine complet de votre serveur soit identique à son nom NETBIOS. Dans ce cas, vous n’avez rien à faire et le certificat par défaut est chargé.

    Toutefois, si vous installez votre certificat sur un serveur accessible sur Internet (par exemple, une machine virtuelle Azure), utilisez le nom de domaine complet (FQDN) de votre serveur, car le nom de domaine complet d’un serveur accessible sur Internet n’est jamais le même que son nom NETBIOS.

    Pour utiliser le nom de domaine complet, accédez à l’emplacement où est installé R Services (*%PROGRAM FILES%\R Remote Service for Visual Studio\1.0* par défaut), ouvrez le fichier *Microsoft.R.Host.Broker.Config.json* dans un éditeur de texte et remplacez son contenu par ce qui suit, en attribuant à CN le nom de domaine complet de votre serveur, par exemple `foo.westus.cloudapp.azure.com` :

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Enregistrez le fichier et redémarrez l’ordinateur pour appliquer les modifications.

## <a name="troubleshooting"></a>Résolution des problèmes

**Question. L’ordinateur R Server ne répond pas, que dois-je faire ?**

Essayez d’envoyer un test ping à l’ordinateur distant à partir de la ligne de commande : `ping remote-machine-name`. Si le test ping échoue, vérifiez que l’ordinateur est en cours d’exécution.

**Question. La fenêtre interactive R indique que l’ordinateur distant est allumé, mais pourquoi le service n’est-il pas en cours d’exécution ?**

Il existe trois raisons possibles :

- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) ou version supérieure n’est pas installé sur l’ordinateur.
- Les règles de pare-feu pour `Microsoft.R.Host.Broker` et `Microsoft.R.Host` ne sont pas activées pour les connexions entrantes et sortantes sur le port 5444.
- Un certificat SSL avec `CN=<remote-machine-name>` n’est pas installé.

Redémarrez l’ordinateur après avoir apporté l’une des modifications ci-dessus. Vérifiez que `RHostBrokerService` et `RUserProfileService` sont en cours d’exécution par le biais du Gestionnaire des tâches (onglet Services) ou *services.msc*.

**Question. Pourquoi la fenêtre interactive R indique « 401 accès refusé » lors de la connexion au serveur R ?**

Il existe deux raisons possibles :

- Il est très probable que le compte `NETWORK SERVICE` n’ait pas accès à la clé privée du certificat SSL. Suivez les instructions précédentes pour accorder au compte `NETWORK SERVICE` l’accès à la clé privée.
- Vérifiez que le service `seclogon` est en cours d’exécution. Utilisez *services.msc* pour configurer `seclogon` pour qu’il démarre automatiquement.

**Question. Pourquoi la fenêtre interactive R indique-t-elle « 404 introuvable » lors de la connexion au serveur R ?**

Cette erreur est probablement due à l’absence de bibliothèques redistribuables Visual C++. Consultez la fenêtre interactive R pour voir s’il existe un message concernant une bibliothèque (DLL) manquante. Ensuite, vérifiez que le package redistribuable VS 2015 est installé, ainsi que R.

**Question. Je ne peux pas accéder à Internet/Resource à partir de la fenêtre interactive R, que dois-je faire ?**

Vérifiez que les règles de pare-feu pour `Microsoft.R.Host.Broker` et `Microsoft.R.Host` autorisent l’accès sortant sur le port 5444. Redémarrez l’ordinateur après avoir appliqué les modifications.

**Question. J’ai essayé toutes ces solutions et cela ne fonctionne toujours pas. Quoi encore?**

Examinez les fichiers journaux dans *C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp*. Ce dossier contient des fichiers journaux distincts pour chaque instance du service R Broker qui a été exécuté. Un autre fichier journal est créé chaque fois que le service redémarre. Examinez le fichier journal le plus récent pour obtenir des indices sur ce qui pourrait ne pas fonctionner.
