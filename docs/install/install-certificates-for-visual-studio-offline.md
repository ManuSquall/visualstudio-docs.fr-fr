---
title: Installer les certificats nécessaires à l’installation hors connexion de Visual Studio | Microsoft Docs
description: Décrit les étapes à effectuer pour installer les certificats nécessaires à l’installation hors connexion de Visual Studio.
ms.date: 08/30/2017
ms.reviewer: tims
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: tglee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 548e00743381e6a2c39d87d82c587b26f944702a
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Installer les certificats nécessaires à l’installation hors connexion de Visual Studio

Visual Studio est avant tout conçu pour être installé sur un ordinateur connecté à Internet, puisque de nombreux composants sont régulièrement mis à jour. Toutefois, en suivant quelques étapes supplémentaires, il est possible de déployer Visual Studio dans un environnement sans aucune connexion Internet disponible.

Le moteur d’installation de Visual Studio n’installe que le contenu approuvé. Pour cela, il contrôle les signatures Authenticode du contenu à télécharger et vérifie que tout le contenu est approuvé avant de l’installer. Cela permet de protéger votre environnement contre des attaques au cas où l’emplacement de téléchargement est compromis. Par conséquent, le programme d’installation de Visual Studio nécessite l’installation de plusieurs certificats standard racines et intermédiaires Microsoft à jour sur un ordinateur d’utilisateur. Lorsque l’ordinateur a été maintenu à jour avec Windows Update, les certificats de signature sont généralement à jour. Si l’ordinateur est connecté à Internet lors de l’installation, Visual Studio peut actualiser les certificats pour vérifier les signatures de fichiers. Si l’ordinateur n’est pas connecté à Internet, les certificats doivent être actualisés d’une autre façon.

## <a name="how-to-refresh-certificates-when-offline"></a>Comment actualiser les certificats hors connexion

Il existe trois options pour installer ou mettre à jour des certificats dans un environnement hors connexion.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Option 1 : Installer manuellement les certificats à partir d’un dossier de disposition

Lorsque vous créez une disposition réseau, les certificats nécessaires sont téléchargés dans le dossier des certificats. Vous pouvez alors installer les certificats manuellement en double-cliquant sur chaque fichier de certificat et en suivant les étapes de l’Assistant du gestionnaire de certificats. Si le système vous demande un mot de passe, laissez-le vide.

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Option 2 : Distribuer les certificats racines approuvés dans un environnement d’entreprise

Pour une entreprise équipée d’ordinateurs hors connexion qui n’ont pas les derniers certificats racines, un administrateur peut utiliser les instructions de la page [Configurer les racines de confiance et les certificats non autorisés](https://technet.microsoft.com/library/dn265983.aspx) pour les mettre à jour.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Option 3 : Installer les certificats dans le cadre d’un déploiement de Visual Studio à base de script

Si vous écrivez un script du déploiement de Visual Studio dans un environnement hors connexion sur des postes de travail clients, vous devez suivre ces étapes :

1. Copiez [l’outil Gestionnaire de certificat](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) dans le partage d’installation (par exemple, \\server\share\vs2017). Certmgr.exe n’est pas inclus dans Windows, mais il est disponible dans le [SDK Windows](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Créez un fichier de commandes avec les commandes suivantes :

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

3. Déployez le fichier de commandes sur le client. Cette commande doit être exécutée à partir d’un processus avec élévation de privilèges.

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Quels sont les fichiers de certificats qui se trouvent dans le dossier des certificats ?

Les trois fichiers .P12 figurant dans ce dossier contiennent chacun un certificat intermédiaire et un certificat racine. La plupart des systèmes tenus à jour via Windows Update disposent déjà de ces certificats.

* **ManifestSignCertificates.p12** contient :
    * Certificat intermédiaire : **Microsoft Code Signing PCA 2011**
        * Non requis Le cas échéant, améliore les performances dans certains scénarios.
    * Certificat racine : **Microsoft Root Certificate Authority 2011**
        * Obligatoire sur les systèmes Windows 7 Service Pack 1 qui ne disposent pas des dernières mises à jour Windows.
* **ManifestCounterSignCertificates.p12** contient :
    * Certificat intermédiaire : **Microsoft Time-Stamp PCA 2010**
        * Non requis Le cas échéant, améliore les performances dans certains scénarios.
    * Certificat racine : **Microsoft Root Certificate Authority 2010**
        * Obligatoire pour les systèmes Windows 7 Service Pack 1 qui ne disposent pas des dernières mises à jour Windows.
* **Vs_installer_opc.SignCertificates.p12** contient :
    * Certificat intermédiaire : **Microsoft Code Signing PCA**
        * Obligatoire pour tous les systèmes. Notez que les systèmes dotés de toutes les mises à jour appliquées à partir de Windows Update n’ont peut-être pas ce certificat.
    * Certificat racine : **Microsoft Root Certificate Authority**
        * Obligatoire. Ce certificat est fourni avec les systèmes exécutant Windows 7 ou version ultérieure.

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Pourquoi les certificats du dossier de certificats ne sont-ils pas installés automatiquement ?

Quand une signature est vérifiée dans un environnement en ligne, les API Windows sont utilisées pour télécharger les certificats et les ajouter au système. La vérification que le certificat est approuvé et autorisé via les paramètres d’administration se produit pendant ce processus. Ce processus de vérification ne peut pas se produire dans la plupart des environnements hors connexion. L’installation manuelle des certificats permet aux administrateurs d’entreprise de s’assurer que les certificats sont approuvés et conformes à la stratégie de sécurité de leur organisation.

## <a name="checking-if-certificates-are-already-installed"></a>Vérification de l’installation des certificats

Une manière de vérifier l’installation du système consiste à suivre ces étapes :
1. Exécutez **mmc.exe**.<br/>
  a. Cliquez sur Fichier et sélectionnez **Ajouter/Supprimer un composant logiciel enfichable**.<br/>
  b. Double-cliquez sur **Certificats**, sélectionnez **Compte d’ordinateur** et cliquez sur **Suivant**.<br/>
  c. Sélectionnez **Ordinateur local**, cliquez sur **Terminer**, puis sur **OK**.<br/>
  d. Développez **Certificats (ordinateur local)**.<br/>
  e. Développez **Autorités de certification racines de confiance** et sélectionnez **Certificats**.<br/>
    * Recherchez les certificats racines nécessaires dans cette liste.<br/>

   f. Développez **Autorités de certification intermédiaires** et sélectionnez **Certificats**.<br/>
    * Recherchez les certificats intermédiaires obligatoires dans cette liste.<br/>

2. Cliquez sur Fichier et sélectionnez **Ajouter/Supprimer un composant logiciel enfichable**.<br/>
  a. Double-cliquez sur **Certificats**, sélectionnez **Mon compte d’utilisateur**, cliquez sur **Terminer**, puis sur **OK**.<br/>
  b. Développez **Certificats – Utilisateur actuel**.<br/>
  c. Développez **Autorités de certification intermédiaires** et sélectionnez **Certificats**.<br/>
    * Recherchez les certificats intermédiaires obligatoires dans cette liste.<br/>

Si les noms des certificats ne figuraient pas dans les colonnes **Délivré à**, ils doivent être installés.  Si un certificat intermédiaire se trouve uniquement dans le magasin de certificats intermédiaires de **l’utilisateur actuel**, il n’est disponible que pour l’utilisateur connecté. Vous devrez peut-être l’installer pour les autres utilisateurs.

## <a name="install-visual-studio"></a>Installer Visual Studio

Après avoir installé les certificats, vous pouvez poursuivre le déploiement de Visual Studio en suivant les instructions de la section [Déploiement à partir d’une installation réseau](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation) de « Créer une installation réseau de Visual Studio ».

## <a name="get-support"></a>Obtenir de l’aide
Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md). Si aucune étape de résolution des problèmes ne vous aide, vous pouvez nous contacter pour une conversation en direct sur une assistance à l’installation (en anglais uniquement). Pour plus de détails, consultez la [page du support Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Voici d’autres options de support :
* Vous pouvez nous signaler des problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui s’affiche dans le programme d’installation de Visual Studio et dans l’IDE de Visual Studio.
* Vous pouvez nous faire part d’une suggestion de produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Vous pouvez suivre les problèmes au niveau d’un produit sur le site [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) et y poser des questions et obtenir des réponses.
* Vous pouvez également communiquer avec nous et d’autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter ](https://gitter.im/Microsoft/VisualStudio)  (Cette option nécessite un compte [GitHub](https://github.com/).)

## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
