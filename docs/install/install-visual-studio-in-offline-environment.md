---
title: "Considérations particulières pour installer Visual Studio dans un environnement hors connexion | Microsoft Docs"
description: "{{ESPACE RÉSERVÉ}}"
ms.date: 06/05/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
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
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 1ce2f854d1c8e4a184446fb07c66a6fad9ca9ae1
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>Considérations particulières pour installer Visual Studio dans un environnement hors connexion

Visual Studio est avant tout conçu pour être installé à partir d’un ordinateur connecté à Internet, dans la mesure où de nombreux composants sont mis à jour régulièrement. Toutefois, en suivant quelques étapes supplémentaires, il est possible de déployer Visual Studio dans un environnement sans aucune connexion Internet disponible.

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Installer les certificats nécessaires pour l’installation hors connexion de Visual Studio
Le moteur d’installation de Visual Studio n’installe que le contenu approuvé. Pour cela, il contrôle les signatures Authenticode du contenu à télécharger et vérifie que tout le contenu est approuvé avant de l’installer. Cela permet de protéger votre environnement contre des attaques au cas où l’emplacement de téléchargement est compromis. Par conséquent, le programme d’installation de Visual Studio nécessite l’installation de plusieurs certificats standard racines et intermédiaires Microsoft à jour sur l’ordinateur d’un utilisateur. Si l’ordinateur est demeuré à jour par le biais de Windows Update, les certificats de signature sont automatiquement mis à jour et, pendant l’installation, Visual Studio actualise les certificats obligatoires pour vérifier les signatures des fichiers. 

Pour une entreprise avec des ordinateurs hors connexion qui n’ont pas les derniers certificats racines, un administrateur peut utiliser [ces instructions](https://technet.microsoft.com/en-us/library/dn265983.aspx) pour mettre à jour les certificats. Il est également possible de télécharger les certificats nécessaires au cours de la création d’une disposition réseau dans le dossier `certificates` et de les installer manuellement en double-cliquant sur le fichier de certificat, puis en exécutant l’Assistant Gestionnaire de certificat. Si le système vous demande un mot de passe, laissez-le vide.

Si vous écrivez un script du déploiement de Visual Studio dans un environnement hors connexion sur des postes de travail clients, vous devez suivre ces étapes :

1. Copiez l’[outil Gestionnaire de certificat](https://msdn.microsoft.com/en-us/library/e78byta0.aspx) (`certmgr.exe`) dans le partage d’installation (par exemple, `\\server\share\vs2017`). `certmgr.exe` n’est pas inclus dans le cadre de Windows lui-même, mais il est disponible dans le cadre du kit [SDK Windows](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk). 

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

### <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Quels sont les fichiers de certificats dans le dossier `certificates` ?
Les trois fichiers `.p12` figurant dans ce dossier contiennent chacun un certificat intermédiaire et un certificat racine. La plupart des systèmes tenus à jour via Windows Update disposent déjà de ces certificats.

1. `ManifestSignCertificates.p12` contient :
    * Certificat intermédiaire : **Microsoft Code Signing PCA 2011**
        * Non requis Le cas échéant, améliore les performances dans certains scénarios.
    * Certificat racine : **Microsoft Root Certificate Authority 2011**
        * Obligatoire sur les systèmes Windows 7 Service Pack 1 qui ne disposent pas des dernières mises à jour Windows.
2. `ManifestCounterSignCertificates.p12`
    * Certificat intermédiaire : **Microsoft Time-Stamp PCA 2010**
        * Non requis Le cas échéant, améliore les performances dans certains scénarios.
    * Certificat racine : **Microsoft Root Certificate Authority 2010**
        * Obligatoire pour les systèmes Windows 7 Service Pack 1 qui ne disposent pas des dernières mises à jour Windows.
3. `vs_installer_opc.SignCertificates.p12`
    * Certificat intermédiaire : **Microsoft Code Signing PCA**
        * Obligatoire pour tous les systèmes. Notez que les systèmes dotés de toutes les mises à jour appliquées à partir de Windows Update n’ont peut-être pas ce certificat.
    * Certificat racine : **Microsoft Root Certificate Authority**
        * Obligatoire. Ce certificat est fourni avec les systèmes exécutant Windows 7 ou version ultérieure.

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Pourquoi est-ce que les certificats du dossier `certificates` ne sont pas installés automatiquement ?
Quand une signature est vérifiée dans un environnement en ligne, les API Windows sont utilisées pour télécharger les certificats et les ajouter au système. La vérification que le certificat est approuvé et autorisé via les paramètres d’administration se produit pendant ce processus. Ce processus de vérification ne peut pas se produire dans la plupart des environnements hors connexion. L’installation manuelle des certificats permet aux administrateurs d’entreprise de s’assurer que les certificats sont approuvés et conformes à la stratégie de sécurité de leur organisation.

### <a name="checking-if-certificates-are-already-installed"></a>Vérification de l’installation des certificats
Une manière de vérifier l’installation du système consiste à suivre ces étapes :
* Exécutez mmc.exe
* Cliquez sur Fichier et sélectionnez Ajouter/Supprimer un composant logiciel enfichable
  * Double-cliquez sur **Certificats**, sélectionnez **Compte d’ordinateur** et cliquez sur **Suivant**
  * Sélectionnez **Ordinateur local**, cliquez sur **Terminer**, puis cliquez sur **OK**
  * Développez **Certificats (ordinateur local)**
  * Développez **Autorités de certification racines de confiance** et sélectionnez **Certificats**
    * Recherchez les certificats racines nécessaires dans cette liste.
  * Développez **Autorités de certification intermédiaires** et sélectionnez **Certificats**
    * Recherchez les certificats intermédiaires obligatoires dans cette liste.
* Cliquez sur Fichier et sélectionnez Ajouter/Supprimer un composant logiciel enfichable
  * Double-cliquez sur **Certificats**, sélectionnez **Mon compte d’utilisateur**, puis cliquez sur **Terminer** et sur **OK**.
  * Développez **Certificats – Utilisateur actuel**
  * Développez **Autorités de certification intermédiaires** et sélectionnez **Certificats**
    * Recherchez les certificats intermédiaires obligatoires dans cette liste.
    
Si les noms des certificats n’étaient pas dans les colonnes **Délivré à**, ils doivent être installés.  Si un certificat intermédiaire était uniquement dans le magasin de certificats intermédiaires de l’**utilisateur actuel**, il est disponible uniquement pour l’utilisateur connecté et devra éventuellement être installé pour d’autres utilisateurs.

## <a name="install-visual-studio"></a>Installer Visual Studio
Une fois les certificats installés, le déploiement de Visual Studio peut continuer hors connexion sans autre étape spécifique, en utilisant les [instructions ici](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation).


## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)

