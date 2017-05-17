---
title: "Considérations particulières relatives à l’installation de Visual Studio dans un environnement hors connexion | Microsoft Docs"
description: "{{ESPACE RÉSERVÉ}}"
ms.date: 05/09/2017
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: b596b6b6f9cff58525d253157534b6b990c68fcd
ms.contentlocale: fr-fr
ms.lasthandoff: 05/09/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>Considérations particulières relatives à l’installation de Visual Studio dans un environnement hors connexion

Visual Studio est principalement conçu pour l’installation à partir d’un ordinateur connecté à Internet, dans la mesure où de nombreux composants sont mis à jour régulièrement. Toutefois, en suivant quelques étapes supplémentaires, il est possible de déployer Visual Studio dans un environnement où une connexion Internet qui fonctionne correctement n’est pas disponible.

## <a name="create-a-network-installation-layout"></a>Créer une disposition d’installation réseau
* Pour plus d’informations, consultez [Créer une installation réseau de Visual Studio](create-a-network-installation-of-visual-studio.md)

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Installer les certificats nécessaires pour l’installation hors connexion de Visual Studio
Le moteur d’installation de Visual Studio n’installe que le contenu approuvé.  Il contrôle les signatures Authenticode du contenu téléchargé et vérifie qu’il est approuvé avant de l’installer.  Les ordinateurs avec un accès à Internet téléchargent et installent automatiquement les certificats nécessaires à la vérification des signatures de fichiers.  Toutefois, si vous opérez dans un environnement hors connexion, ou sur un système avec une connectivité Internet médiocre, cela peut s’avérer impossible.  Pour les utilisateurs de cet environnement, vous devez vérifier que les certificats nécessaires sont préinstallés.  Ces certificats sont téléchargés par l’ordinateur en cours d’exécution dans le dossier « certificats » lors de la création d’une installation hors connexion.

Vous pouvez installer les certificats sur le client en double-cliquant manuellement sur le fichier de certificat, puis en cliquant sur l’Assistant du gestionnaire de certificats. Si le système vous demande un mot de passe, laissez-le vide.

Pour générer un script de l’installation des certificats, effectuez les étapes suivantes :

1. Copiez certmgr.exe sur le partage d’installation (par exemple, `\server\share\vs2017`). `certmgr.exe` est fourni avec le SDK Windows, qui peut être installé comme un composant facultatif dans la charge de travail _Développement pour la plateforme Windows universelle_. (Exemple : `"C:\Program Files (x86)\Windows Kits\10\bin\x86\certmgr.exe"`)

2. Créez un fichier de commandes avec les commandes suivantes :

```cmd
\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
```

3. Exécutez le fichier de commandes sur le client à partir d’une interface de commande d’administrateur ou d’un processus avec élévation de privilèges.

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Pourquoi est-ce que les certificats du dossier `certificates` ne sont pas installés automatiquement ?
Quand une signature est vérifiée dans un environnement en ligne, les API Windows sont utilisées pour télécharger les certificats et les ajouter au système. La vérification que le certificat est approuvé et autorisé via les paramètres d’administration se produit pendant ce processus. Ce processus de vérification ne peut pas se produire dans la plupart des environnements hors connexion. L’installation manuelle des certificats permet à l’utilisateur de vérifier que les certificats sont approuvés et conformes aux spécifications de l’administrateur.

## <a name="install-visual-studio"></a>Installer Visual Studio
Une fois les certificats installés, le déploiement de Visual Studio peut continuer hors connexion sans autre étape spécifique, en utilisant les [instructions ici](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation).


## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)

