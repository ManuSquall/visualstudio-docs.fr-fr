---
title: Installer des certificats pour une installation hors connexion
description: Découvrez comment installer des certificats pour une installation hors connexion de Visual Studio.
ms.date: 03/29/2021
ms.custom: seodec18, SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6dc4137157e2fa5136a0b8c86c5cf72f284a9eb7
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307374"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Installer les certificats nécessaires à l’installation hors connexion de Visual Studio

Visual Studio est avant tout conçu pour être installé sur un ordinateur connecté à Internet, puisque de nombreux composants sont régulièrement mis à jour. Toutefois, en suivant quelques étapes supplémentaires, il est possible de déployer Visual Studio dans un environnement où une connexion Internet qui fonctionne correctement n’est pas disponible.

Le moteur d’installation de Visual Studio n’installe que le contenu approuvé. Pour cela, il contrôle les signatures Authenticode du contenu à télécharger et vérifie que tout le contenu est approuvé avant de l’installer. Cela permet de protéger votre environnement contre des attaques au cas où l’emplacement de téléchargement est compromis. Par conséquent, le programme d’installation de Visual Studio nécessite l’installation et la mise à jour de plusieurs certificats intermédiaires et racines Microsoft standard sur l’ordinateur d’un utilisateur. Lorsque l’ordinateur a été maintenu à jour avec Windows Update, les certificats de signature sont généralement à jour. Si l’ordinateur est connecté à Internet lors de l’installation, Visual Studio peut actualiser les certificats pour vérifier les signatures de fichiers. Si l’ordinateur n’est pas connecté à Internet, les certificats doivent être actualisés d’une autre façon.

## <a name="how-to-refresh-certificates-when-offline"></a>Comment actualiser les certificats hors connexion

Il existe trois options pour installer ou mettre à jour des certificats dans un environnement hors connexion.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Option 1 : Installer manuellement les certificats à partir d’un dossier de disposition

::: moniker range="vs-2017"

Lorsque vous créez une [disposition réseau](../install/create-a-network-installation-of-visual-studio.md) ou un [cache hors connexion local](../install/create-an-offline-installation-of-visual-studio.md), les certificats nécessaires sont téléchargés dans le dossier certificats. Vous pouvez alors installer les certificats manuellement en double-cliquant sur chaque fichier de certificat et en suivant les étapes de l’Assistant du gestionnaire de certificats. Si le système vous demande un mot de passe, laissez-le vide.

**Mise à jour** : pour Visual Studio 2017 version 15.8 Préversion 2 ou version ultérieure, vous pouvez installer manuellement les certificats en cliquant avec le bouton droit sur chacun des fichiers de certificat, puis sélectionnez Installer le certificat et cliquez sur l’Assistant Gestionnaire de certificats.

::: moniker-end

::: moniker range=">=vs-2019"

Lorsque vous créez une [disposition réseau](../install/create-a-network-installation-of-visual-studio.md) ou un [cache hors connexion local](../install/create-an-offline-installation-of-visual-studio.md), les certificats nécessaires sont téléchargés dans le dossier certificats. Vous pouvez installer manuellement les certificats en cliquant avec le bouton droit sur chacun des fichiers de certificat, en sélectionnant Installer le certificat, puis en suivant l’Assistant Gestionnaire de certificats. Si le système vous demande un mot de passe, laissez-le vide.

::: moniker-end

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Option 2 : Distribuer les certificats racines approuvés dans un environnement d’entreprise

Pour une entreprise équipée d’ordinateurs hors connexion qui n’ont pas les derniers certificats racines, un administrateur peut utiliser les instructions de la page [Configurer les racines de confiance et les certificats non autorisés](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) pour les mettre à jour.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Option 3 : Installer les certificats dans le cadre d’un déploiement de Visual Studio à base de script

Si vous écrivez un script du déploiement de Visual Studio dans un environnement hors connexion sur des postes de travail clients, vous devez suivre ces étapes :

1. Copiez l' [outil Certificate Manager](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) dans la disposition du réseau ou l’emplacement d’installation du cache local. Certmgr.exe n’est pas inclus dans Windows, mais il est disponible dans le [SDK Windows](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Créez un fichier de commandes avec les commandes suivantes :

   ```shell
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root
   ```
   
   Vous pouvez également créer un fichier de commandes qui utilise certutil.exe, fourni avec Windows, avec les commandes suivantes :
   
      ```shell
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Déployez le fichier de commandes sur le client. Cette commande doit être exécutée à partir d’un processus avec élévation de privilèges.

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Quels sont les fichiers de certificats qui se trouvent dans le dossier des certificats ?

* **manifestRootCertificate. cer** contient les éléments suivants :
  * Certificat racine : **Microsoft Root Certificate Authority 2011**
* **manifestCounterSignRootCertificate. cer** et **vs_installer_opc. RootCertificate. cer** contient les éléments suivants :
  * Certificat racine : **Microsoft Root Certificate Authority 2010**
 
Visual Studio Installer requiert uniquement l’installation des certificats racines sur le système. Tous ces certificats sont requis pour les systèmes Windows 7 Service Pack 1 sur lesquels les mises à jour Windows les plus récentes ne sont pas installées.

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Pourquoi les certificats du dossier de certificats ne sont-ils pas installés automatiquement ?

Quand une signature est vérifiée dans un environnement en ligne, les API Windows sont utilisées pour télécharger les certificats et les ajouter au système. La vérification que le certificat est approuvé et autorisé via les paramètres d’administration se produit pendant ce processus. Ce processus de vérification ne peut pas se produire dans la plupart des environnements hors connexion. L’installation manuelle des certificats permet aux administrateurs d’entreprise de s’assurer que les certificats sont approuvés et conformes à la stratégie de sécurité de leur organisation.

## <a name="checking-if-certificates-are-already-installed"></a>Vérification de l’installation des certificats

Une manière de vérifier l’installation du système consiste à suivre ces étapes :

1. Exécutez **mmc.exe**.<br/>
  a. Cliquez sur **Fichier** et sélectionnez **Ajouter/Supprimer un composant logiciel enfichable**.<br/>
  b. Double-cliquez sur **Certificats**, sélectionnez **Compte d’ordinateur** et cliquez sur **Suivant**.<br/>
  c. Sélectionnez **Ordinateur local**, cliquez sur **Terminer**, puis sur **OK**.<br/>
  d. Développez **Certificats (ordinateur local)**.<br/>
  e. Développez **Autorités de certification racines de confiance** et sélectionnez **Certificats**.<br/>
    * Recherchez les certificats racines nécessaires dans cette liste.<br/>

   f. Développez **Autorités de certification intermédiaires** et sélectionnez **Certificats**.<br/>
    * Recherchez les certificats intermédiaires obligatoires dans cette liste.<br/>

2. Cliquez sur **Fichier** et sélectionnez **Ajouter/Supprimer un composant logiciel enfichable**.<br/>
  a. Double-cliquez sur **Certificats**, sélectionnez **Mon compte d’utilisateur**, cliquez sur **Terminer**, puis sur **OK**.<br/>
  b. Développez **Certificats – Utilisateur actuel**.<br/>
  c. Développez **Autorités de certification intermédiaires** et sélectionnez **Certificats**.<br/>
    * Recherchez les certificats intermédiaires obligatoires dans cette liste.<br/>

Si les noms des certificats ne figuraient pas dans les colonnes **Délivré à**, ils doivent être installés.  Si un certificat intermédiaire se trouve uniquement dans le magasin de certificats intermédiaires de **l’utilisateur actuel**, il n’est disponible que pour l’utilisateur connecté. Vous devrez peut-être l’installer pour les autres utilisateurs.

## <a name="install-visual-studio"></a>Installation de Visual Studio

Après avoir installé les certificats sur l’ordinateur client, vous êtes prêt à [installer Visual Studio à partir du cache local](../install/create-an-offline-installation-of-visual-studio.md#step-3---install-visual-studio-from-the-local-cache)ou à [déployer Visual Studio à partir du partage de disposition réseau](create-a-network-installation-of-visual-studio.md#deploy-from-a-network-installation) vers l’ordinateur client.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Créer une installation réseau de Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Créer une installation hors connexion de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)

