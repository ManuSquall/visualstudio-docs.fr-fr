---
title: "Espaces de travail distants avec les Outils R pour Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5778c9cf-564d-47b0-8d64-e5dc09162479
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 1016f07c0f4505f2dd652482dd4d568655565cf0
ms.contentlocale: fr-fr
ms.lasthandoff: 05/12/2017

---


# <a name="setting-up-remote-workspaces"></a>Configuration des espaces de travail distants

Pour utiliser un espace de travail distant avec les Outils R pour Visual Studio (RTVS), l’ordinateur distant doit être configuré avec SSL et un service R approprié comme indiqué dans cette rubrique. 

- [Spécifications de l’ordinateur distant](#remote-computer-requirements)
- [Installer un certificat SSL](#install-an-ssl-certificate)
- [Installer R Services](#install-r-services)
- [Configurer R Services](#configure-r-services)
- [Résolution des problèmes](#troubleshooting)

## <a name="remote-computer-requirements"></a>Spécifications de l’ordinateur distant

- Windows 10, Windows Server 2016 ou Windows Server 2012 R2. RTVS nécessite également
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) ou version supérieure

## <a name="install-an-ssl-certificate"></a>Installer un certificat SSL

RTVS nécessite que toutes les communications avec un serveur distant s’effectuent sur HTTP, ce qui implique un certificat SSL sur le serveur. Vous pouvez utiliser un certificat signé par une autorité de certification approuvée (recommandée) ou un certificat auto-signé (dans ce cas, RTVS envoie des avertissements quand il se connecte). Indépendamment du certificat, vous devez ensuite l’installer sur l’ordinateur et autoriser l’accès à sa clé privée.

### <a name="obtaining-a-trusted-certificate"></a>Obtention d’un certificat approuvé

Un certificat approuvé est émis par une autorité de certification (consultez l’article sur les [autorités de certification sur Wikipedia](https://en.wikipedia.org/wiki/Certificate_authority) pour plus d’informations). Comme pour l’obtention d’une carte d’identité émise par l’État, cela implique plusieurs processus et des frais potentiels, mais permet de vérifier l’authenticité de la demande et du demandeur.

Le champ de clé qui doit se trouver dans le certificat est le nom de domaine complet de votre serveur R. L’autorité de certification nécessite la preuve que vous êtes autorisé à créer un serveur pour le domaine auquel il appartient.

Pour plus d’informations, consultez l’article sur les [certificats de clé publique](https://en.wikipedia.org/wiki/Public_key_certificate) sur Wikipedia.

### <a name="obtaining-a-self-signed-certificate"></a>Obtention d’un certificat auto-signé

Par rapport à un certificat émis par une autorité approuvée, un certificat auto-signé est comme si vous créiez vous-même votre carte d’identité. Bien évidemment, cela est beaucoup plus simple que de passer par une autorité approuvée, mais en contre-partie l’authentification obtenue est moins forte, ce qui signifie qu’un pirate informatique peut substituer son propre certificat au certificat non signé et ainsi capturer tout le trafic entre le client et le serveur. *Le certificat auto-signé doit donc être utilisé uniquement pour les tests de scénarios, sur un réseau approuvé, et jamais en production.*

Pour cette raison, RTVS émet toujours l’avertissement suivant lors de la connexion à un serveur avec un certificat auto-signé :

![Boîte de dialogue d’avertissement de certificat auto-signé](~/rtvs/media/workspaces-remote-self-signed-certificate-warning.png)

Pour émettre un certificat auto-signé :

1. Ouvrez une session sur le serveur R à l’aide d’un compte d’administrateur.
1. Ouvrez une nouvelle invite de commandes administrateur PowerShell et envoyez la commande suivante, en remplaçant `"remote-machine-name"` par le nom de domaine complet de votre serveur.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Si vous n’avez jamais exécuté Powershell auparavant sur le serveur R, vous devez exécuter la commande suivante pour activer l’exécution explicite de commandes :

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Pour plus d’informations, consultez l’article sur les [certificats auto-signés](https://en.wikipedia.org/wiki/Self-signed_certificate) sur Wikipedia.

### <a name="installing-the-certificate"></a>Installation du certificat

Pour installer le certificat sur l’ordinateur distant, exécutez `certlm.msc` (le gestionnaire de certificats) à partir d’une invite de commandes. Cliquez avec le bouton droit sur le dossier **Personnel** et sélectionnez la commande **Toutes les tâches > Importer** :

![Commande d’importation de certificat](~/rtvs/media/workspaces-remote-certificate-import.png)


### <a name="granting-permissions-to-read-the-ssl-certificates-private-key"></a>Octroi d’autorisations pour lire la clé privée du certificat SSL

Une fois le certificat importé, accordez des autorisations au compte `NETWORK SERVICE` pour lire la clé privée, comme indiqué ci-dessous. `NETWORK_SERVICE` est le compte utilisé pour exécuter le répartiteur R Services, qui est le service qui met fin aux connexions SSL entrantes sur le serveur.

1. Exécutez `certlm.msc` (le gestionnaire de certificats) à partir d’une invite de commandes administrateur.
1. Développez **Personnel > Certificats**, cliquez avec le bouton droit sur votre certificat, puis sélectionnez **Toutes les tâches > Gérer les clés privées**.
1. Clic avec le bouton droit sur le certificat et sélection de la commande Gérer les clés privées sous Toutes les tâches
1. Dans la boîte de dialogue qui s’affiche, sélectionnez **Ajouter** et entrez `NETWORK SERVICE` comme nom de compte :

    ![Boîte de dialogue Gérer les clés privées, ajout de NETWORK_SERVICE](~/rtvs/media/workspaces-remote-manage-private-key-dialog.png)

1. Sélectionnez **OK** deux fois pour fermer les boîtes de dialogue et valider vos modifications.


## <a name="install-r-services"></a>Installer R Services

Pour exécuter le code R, l’ordinateur distant doit avoir un interpréteur R installé comme suit :

1. Téléchargez et installez l’un des programmes suivants :

    - [Microsoft R Open](https://mran.microsoft.com/open/)
    - [CRAN R pour Windows](https://cran.r-project.org/bin/windows/base/)

    Ces deux programmes ont les mêmes fonctionnalités, mais Microsoft R Open bénéficie de bibliothèques d’algèbre linéaire à accélération matérielle, fournies par la bibliothèque [Intel Math Kernel Library](https://software.intel.com/intel-mkl).

1. Exécutez le [programme d’installation de R Services](https://aka.ms/rtvs-services) et redémarrez quand vous y êtes invité. Le programme d’installation effectue les opérations suivantes :

    -    Création d’un dossier dans `%PROGRAMFILES%\R Tools for Visual Studio\1.0\` et copie de tous les fichiers binaires nécessaires.
    -    Installation de `RHostBrokerService` et `RUserProfileService`, et configuration pour un démarrage automatique.
    -    Configuration du service `seclogon` pour qu’il démarre automatiquement.
    -    Ajout de `Microsoft.R.Host.exe` et `Microsoft.R.Host.Broker.exe` au règles de pare-feu entrantes sur le port 5444 par défaut.

R Services démarre automatiquement au redémarrage de l’ordinateur :

- Le **service de répartiteur de l’hôte R** gère tout le trafic HTTPS entre Visual Studio et le processus dans lequel s’exécute le code sur l’ordinateur.
- Le **service des profils utilisateur R** est un composant privilégié qui gère la création des profils utilisateur Windows. Ce composant est appelé quand un nouvel utilisateur se connecte pour la première fois au serveur R.

Vous pouvez l’observer dans la console de gestion des services (`compmgmt.msc`).  

## <a name="configure-r-services"></a>Configurer R Services

Une fois que R Services est en cours d’exécution sur l’ordinateur distant, vous devez aussi créer des comptes d’utilisateur, définir des règles de pare-feu, configurer le réseau Azure et configurer le certificat SSL.

1. Comptes d’utilisateur : Créez des comptes pour chaque utilisateur qui accède à l’ordinateur distant. Vous pouvez créer des comptes d’utilisateur locaux standard (sans privilège), ou vous pouvez joindre votre serveur R à votre domaine et ajouter des groupes de sécurité appropriés au groupe de sécurité `Users`.
1. Règles de pare-feu : Par défaut, `R Host Broker` écoute sur le port TCP 5444. Par conséquent, vérifiez qu’il existe des règles de pare-feu Windows activées pour le trafic entrant et sortant (le trafic sortant est nécessaire pour l’installation des packages et des scénarios similaires).  Le programme d’installation de R Services définit ces règles automatiquement pour le pare-feu Windows intégré. Toutefois, si vous utilisez un pare-feu tiers, vous devez ouvrir manuellement le port 5444 pour `R Host Broker`.
1. Configuration d’Azure : Si l’ordinateur distant est une machine virtuelle sur Azure, vous devez ouvrir le port 5444 pour le trafic entrant dans le réseau Azure, qui est indépendant du pare-feu Windows. Pour plus d’informations, consultez [Filtrer le trafic réseau avec les groupes de sécurité réseau](https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg) dans la documentation Azure.
1. Indiquer au répartiteur de l’hôte R le certificat SSL à charger : si vous installez le certificat sur un serveur intranet, il est probable que le nom de domaine complet de votre serveur soit identique à son nom NETBIOS. Dans ce cas, vous n’avez rien à faire et le certificat par défaut est chargé.

    Toutefois, si vous installez votre certificat sur un serveur sur Internet (par exemple, une machine virtuelle Azure), utilisez le nom de domaine complet (FQDN) de votre serveur, car le nom de domaine complet d’un serveur sur Internet n’est jamais le même que son nom NETBIOS.

    Pour ce faire, accédez à l’emplacement où est installé R Services (`%PROGRAM FILES%\R Remote Service for Visual Studio\1.0` par défaut), ouvrez le fichier `Microsoft.R.Host.Broker.Config.json` dans un éditeur de texte et remplacez son contenu par ce qui suit, en attribuant à CN le nom de domaine complet de votre serveur, par exemple, `foo.westus.cloudapp.azure.com` :

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

**Le serveur R ne répond pas, que faire ?**

Vérifiez si vous pouvez envoyer un test ping à l’ordinateur distant à partir de la ligne de commande : `ping remote-machine-name`. Si le test ping échoue, vérifiez que l’ordinateur est en cours d’exécution.

**Q. La fenêtre interactive R indique que l’ordinateur distant est actif, mais pourquoi le service n’est-il pas en cours d’exécution ?**

Il existe trois raisons possibles à ce problème :

-    [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) ou version supérieure n’est pas installé sur l’ordinateur.
-    Les règles de pare-feu pour `Microsoft.R.Host.Broker` et `Microsoft.R.Host` ne sont pas activées pour les connexions entrantes et sortantes sur le port 5444.
-    Un certificat SSL avec `CN=<remote-machine-name>` n’est pas installé.

Redémarrez l’ordinateur après avoir apporté l’une des modifications ci-dessus. Vérifiez que `RHostBrokerService` et `RUserPofileService` sont en cours d’exécution par le biais du Gestionnaire des tâches (onglet Services) ou `services.msc`.

**Q. Pourquoi la fenêtre interactive R indique « 401 Accès refusé » lors de la connexion au serveur R ?**

Deux raisons possibles :

- Il est très probable que le compte `NETWORK SERVICE` n’ait pas accès à la clé privée du certificat SSL. Suivez les instructions précédentes pour accorder au compte `NETWORK SERVICE` l’accès à la clé privée.
- Vérifiez que le service `seclogon` est en cours d’exécution. Utilisez `services.msc` pour configurer `seclogon` pour qu’il démarre automatiquement.                                                         
**Q. Pourquoi la fenêtre interactive R indique « 404 Introuvable » lors de la connexion au serveur R ?**

Ceci est probablement dû à l’absence de bibliothèques redistribuables Visual C++. Consultez la fenêtre interactive R pour voir s’il existe un message concernant une bibliothèque (DLL) manquante. Ensuite, vérifiez que le package redistribuable VS 2015 est installé, ainsi que R.

**Q. Je ne peux pas accéder à Internet/une ressource à partir de la fenêtre interactive R, que dois-je faire ?**

Vérifiez que les règles de pare-feu pour `Microsoft.R.Host.Broker` et `Microsoft.R.Host` autorisent l’accès sortant sur le port 5444. Redémarrez l’ordinateur après avoir appliqué les modifications.

**Q. J’ai essayé toutes les solutions ci-dessus et le problème n’est pas résolu. Que puis-je faire ?**

Consultez les fichiers journaux dans `C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp`. Il existe un fichier journal distinct pour chaque instance du service de répartiteur R exécuté. En d’autres termes, si le service a dû redémarrer pour une raison quelconque, un autre fichier journal est créé. Examinez le fichier journal avec l’horodatage le plus récent pour obtenir des indices sur ce qui pourrait ne pas fonctionner.

